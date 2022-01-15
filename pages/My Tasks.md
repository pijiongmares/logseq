- ## 101121 Enhance SMS Address Confirmation
  collapsed:: true
	- ### Send SMS Improvement Feature Notes:
		- ### Current:
			- Hi, this is CHEF KWO SKT. Please click the link below to share with us your location for delivery. [https://sesame.menu/sms/api/location/redirect/gI61xp](https://sesame.menu/sms/api/location/redirect/gI61xp)
		- ### Permission:
			- If allow - show the customer's address in the map
			- If deny - show the restaurant's address in the map
		- ### Requirements:
			- Allow the customer to change the address (even multiple times) during the session only
			- After the call, expire the update link
			- When viewing the link - send the customer address set in POS with condition of:
			- Allow permission:
			- If valid - confirm
			- If not - allow to change then confirm
			- If not allow:
			- Send restaurant address
			- ~~Update the SMS sent to customer?~~  - Not needed, current message is enough.
		- ### To check:
			- Na sa-save ba yung new address sa next call?
			- Sa receipt kaya na lalagay yung address ng customer? - YES
			- Implementation:
			- Approach 1 - kung pwede i-expire yung link after ng call
			- Approach 2 - allow 1 time update after mag end yung call
			- To check - na u-update ba yung receipt sa restaurant kapag nag palit ng address?
		- ### Other question:
			- Pwede ba mag update after ng call?
			- Mas preferred na hindi
			- Note - may expiry yung link
			- Currently sesame.menu yung nasa domain na sini-send sa sms. ok lang ba to sa future? since possible mawala sa future yung sesame.menu - Ok lang, via nginx yung change sa future
		- ### Github Repository
			- [https://github.com/kjt01/sms-customer-client](https://github.com/kjt01/sms-customer-client)
			- [Text Message to Confirm Address - BA Corner - Confluence (atlassian.net)](https://wondersco.atlassian.net/wiki/spaces/BA/pages/1241153572/Text+Message+to+Confirm+Address)
			- [Receive sms free](https://smsreceivefree.com/info/13479675336/?__cf_chl_captcha_tk__=pmd_3hbkuug7pOXVnKpurqBjXAoxjulqp7k2j7Wk4U3O6Jc-1629821478-0-gqNtZGzNAvujcnBszQh9)
	- ## Code Findings
		- ### map.html
			- In map.html, send sms function does not include the address set by the agent in the request to the kjt-sms-connect-service backend (only sms number,  username, and restaurant id are being sent)
		- ### kjt-sms-connect-service (receive the request for sending sms from map.html)
			- The map.html sends request to /sms/api/location/customer in the GeolocationController class. it accepts a payload of CustomerLocationSMS model class which has the properties smsNumber, rid, and username
			- Transaction id and time created are also generated in the GeolocationController
			- GeolocationController has algorithms that fits to be in a service, refactor?
			- In the GeolocationController, generates a geolocation long url that consist of the customerlocationsms.html page (location in the sms-customer-client project), smsNumber, transaction id, and the address of the restaurant
			- Create a CustLocReqURL model class that consist of the long url, time created of the custom location url model, and the restaurant id
			- Generate a shorten url (replace the long url with a generated unique id) and save the CustLocReqURL model in the directory SMS:ManagedUrl in redis
			- Construct the complete url with the shorten/temp url
			- Create instance of SendSMSGeoLocationRequest to send the url via sms
		- ### kjt-sms-connect-service (receive the request for redirecting to address confirmation ui (customerlocationsms.html) from the url send via sms)
			- Customer loads the url into the browser, request sent to /map/api/location/redirect/{shorten url}
			- Method retrieves the long url saved in redis using the shorten url (id referencing to the record)
			- Compare the time created of the long url (the time the request receives from map.html) vs the expiration duration in the application.properties (geoExpiration) in minutes (default if 600 minutes)
			- If the long url is expired, redirect to cuslocsmssessionexpired.html location in the sms-customer-client project
			- If valid, redirect to customerlocationsms.html (also in sms-customer-client project)
		- ### Customerlocationsms.html
			- The page parses the query string which are the sms number, transaction id, and the restaurant address
			- Uses navigator.geolocation which gets the current location of the customer
			- Permission will be asked to allow getting the location. if true, set the current location of the customer. and if false, set the restaurant address from the query string in the url
			- Confirm location and send to /sms/api/location/customer/confirm in the kjt-sms-connect-service project
		- ### kjt-sms-connect-service (receive the request for confirming the address from the customerlocationsms.location)
			- Receives the confirmed address and send it back to the pos order screen via web socket (changing the address in the screen of the agent in real time)
	- ## Notes To Consider
		- In the map.html, the request being sent includes smsnumber, username, and restaurant id. maybe just add the address set by the agent
		- The CustomerLocationSMS model class is in the kjt-pos-comm which is part of a core library. Maybe restaurant id property is used in other projects so do not remove it, maybe just add the address property that was set by the agent in the property of the class?
		- There are 2 places where the validation of expired linked are done.
			- 1. When the customer access the url in his/her browser, then it will send a request to redirect api resource (redis directory is SMS:ManagedURL)
			- 2. When the customer send the location, it will send a request to the confirm api resource (redis directory is SMS:CustomerLocationSMS)
		- Restaurant info was retrieved from the kjt.core.api.restaurant.byrid:/api/restaurant/rid/{rid}} api resource
		- Can we retrieve the call status and order status from an existing api resource? or direct jpa db?
		-
		- Send SMS
		- New customer/new address when send button clicked
		- Existing customer/new address send message when send button clicked
			-
	- ## Revised Specs 10/20/21
		- 1. Bring out send sms  (bring out the send sms button from map.html beside the address input box)
		- 2. Map cleaner  (remove pins of commercial/other places)
		- 3. Make input field double size  (make textarea)
		- 4. Input feature gives the address  (already doing this)
		- 5. Confirmation alert after selecting an address (edited)
	- ## Execution Plan
		- 1. Create a button with a message icon beside the address text field, copy the script from the send button in map.html (the modal html element that has an input box for the mobile number and the buttons). The script, using ajax, includes the request to the kjt-sms-connect-service confirm endpoint that sends the address back to the pos.html using websocket
		- 2. Update the customerlocationsms.html google api implementation and just add the options to remove the pinned commercial places
		- 3. Change the input element to textarea (google map api searchbox accepts textarea element)
		- 4. Google map api already shows the places while typing in the search box (autocomplete)
		- 5. Show an alert element (popup/anywhere in the main page) that the location was sent back to the agent
	- ## venom.letsdochinese.com nginx.conf
		- ``` nginx
		  # added line in int.letsdochinese.com server
		  location /KJTCore/resources/map {
		  	alias /var/www/sms/location/;
		  	try_files $uri $uri.html $uri/;
		  	autoindex off;
		  	expires -1;
		  }
		  ```
		  ```
- ## 110921 Add Cloning Of Menu in Restaurant Editor
  collapsed:: true
	- ## Tables currently affected by the cloning
		- kjt.category
		- kjt.comboappcategory
		- kjt.dish
		- kjt.dishproperties
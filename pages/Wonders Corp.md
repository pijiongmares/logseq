- # Onboarding
	- # Onboarding Notes
		- # Application Environments
			- ## int/int-ph
				- Where devs test the codes (INT is base in New York and INT-PH is in Singapore)
			- ## qa
				- Regression/feature testing (dev also test in this environment)
			- ## training
				- Training environment (pre-prod)
			- ## dev/staging
				- First phase of deployment (Staging area/clone copy of PROD)
				- Content team (the ones updating the records of the restaurant including visiting the clients)
				- Content team uses editor in this environment
			- ## prod
				- No editor
				  
				  ___
		- # Database
			- No editors/configs in DEV/PROD so changes to the restaurant or users (configs/editors), need to push (general/restaurant/agent). Usually done off hours.
			- ## int-ph
				- hostname : xavier.celkkcvywdgq.ap-southeast-1.rds.amazonaws.com
			- ## int
				- hostname : magneto.cskuefg0dln0.us-east-1.rds.amazonaws.com
			- ## qa
				- hostname : juggernaut.cskuefg0dln0.us-east-1.rds.amazonaws.com
			- ## training
				- hostname : training-db.letsdochinese.com
			- ## dev/staging
				- hostname : dev-db.letsdochinese.com
			- ## prod
				- hostname :
					- Server F - 192.168.1.160
					- Foxtrot - foxtrot.letsdochinese.com
					- MNL-DB mnl-db.letsdochinese.com
					  ___
		- # POS (Phone Order System) Introduction and Overview
			- ## POS Home Screen
				- ### AUX Statistics Report
					- Agents performance/time stats
		- ### Inbound Contacts
		- ATT (average talk time)
		- AWT (average work time)
		- AHT (talk + work)
		- ### call statistics report
		- agent & restaurant call stats (customers (customers of the restaurants) & clients(restaurants))
		  
		  ---
		- ### my schedule
		- #### my schedule
		- shows the schedule of the agent
		- #### my activity
		- timekeeping record (for time in/out select wonders in aux, wait for 2 mins, then select logout)
		  
		  ---
		- ### mistakes & coaching
		- mistake reports
		- ### news
		- new restaurants and features (processes) bulletin
		- ### queue
		- current queued calls for the agent
		  
		  ---
		- ### call history
		- call summary of the agent
		- clicking on the records will show a popup for playing the recorded call
		- #### clients
		- clients/restaurant owners call
		- #### outbounds
		- outbound calls
		- #### inbounds
		- inbound calls
		- #### finished
		- finished calls
		- #### abandoned
		- abandoned calls
		- no one received the call
		- #### calendar
		- select date to view
		  
		  ---
		- ### aux
		- agent status (ready, mgmt, callback, wonders, coaching, sbs, meeting, restroom, other, logout)
		- agent must be ready in order to be able to take a call
		- ### restaurant color coding
		- blue : active
		- yellow : onboarding
		- red : offboarding
		- white : for testing
		- ## restaurant order screen
		- automatically shows when the agent receives a call from the customer ordering to a specific restaurant
		- can also be accessed by clicking the restaurant from the home screen
		- #### order types
		- ##### pick-up
		- can be selected with online (order made online) or not online (order made via phone)
		- address is optional
		- ##### delivery
		- can be selected with online (order made online) or not online (order made via phone)
		- ##### online (managers use only)
		- toggle button. used together with pick-up or delivery option
		- ##### more button option
		- ###### order section (2nd column from the left)
		- shows the customer information, payment, status and the order details
		- if agent value is "online", it means the order was made with online button enabled (manager's use only)
		- order has versions
		  
		  1. **mistake** - create a report for a mistake with an order (either an agent mistake, qa, coaching, or a possible bug in the system)
		  2. **modify** - use to modify current date sent orders
		  3. **void** - void the order
		  4. **reminder** - used to warn or give a message to an agent for that order
			- run out of specific dish
			- can set time occurence
			  5. **rush** - rush order. provide reason
		- ###### order filters
		- today, delivery, pickup, saved, online, and date (select date of order)
		- ###### order list
		- shows the list of orders sent
		- gray colored orders means it is from the previous days
		- white are saved orders or orders made from sesame.menu (osaved)
		- green are today's orders
		- red are voided
		- ###### call list relative (not link to orders)
		- used to review orders of the customer
		- calls are not linked to any orders. it is used to review the orders using the call or calls
		- ###### call section (right)
		- shows the orders and call history (inbound and outbound) of the agent for the selected restaurant
		- call : customer/client number or any number. also shows the saved contact information for the restaurant
		- recorded time follows the restaurant's local time
		- disable calls (for selected agents only) : option to redirect call to restaurant or the restaurant is close
		  
		  ---
		- #### customer information and order list section (left sidebar)
		- phone number
		- name
		- address (street, apt/house/biz no., city) with distance in miles between the customer and the client
		- order remarks
		- conf note (customer remarks shows)\
		- customer language radio button
		- split order : separate order, payment, and receipt (sub orders)
		- ##### add and minus button
		- increment or decrement quantity
		- ##### save
		- used when customers are undecided and wish to call later then save the order
		- ##### home
		- go back to home screen
		- ##### credit card
		- Visa, Mastercard, Discover (min $12)
		- credit card charge, cash charge, tip (can split payment to cash and card)
		- card number
		- expiration date (month and year)
		- cvv
		- billing zip code
		- call recording stops when entering credit card details
		- propay credit card are external that are sent to the restaurant for processing
		- can also be updated for sent orders
		- ##### send
		- pay cash
		- sent orders for the current date can still be modifed
		- ##### price section
		- discounts
		- subtotal (discount applied)
		- dish & delivery tax (not always the same)
		- total price
		- eta to finish
		- #### restaurant note (top middle)
		- #### menu
		- ##### purple : modifications of the dish
		- special order : dishes that do not exist maybe added
		- menu : displays the softversion of the menu
		- ##### blue/category
		- ##### category note
		- ##### green/dishes per category
		- clicking the dish will show the ask & click popup depending on the condition
		- some dish has time conditions and when there are conditions that are set to "ask", ask & click popup will show
		- combo size will also show ask & click
		- ###### ask & click
		- top section shows the current condition that can be applied to the selected dish
		- option to select the side dish for the main dish selected
		- ##### after the ask & click popup
		- reminder popup : ask the message displayed
		- after selecting the type of dish in ask & click, the dish options will be enabled in the  located at the middle left
		- ###### size info note
		- ###### brown : sizes
		- L : Lunch
		- Qt/Quart : Large
		- md : Median
		- Pt/Pint : Small
		- C : Combo
		- ###### blue : rice substitutes
		- ###### green : regular dish substitutes
		- #### transfer call (right sidebar)
		- ##### transfer : transfer call to manager, spanish, party order, chinese, and external transfers (restaurant order & online order)
		- external transfers are orders that where processed using the clients portal/order system, not with pos
		- ##### help : ask for help and chinese assistant
		- # online order system (sesame.menu)
		  
		  ___
		- like the pos but users are not the agent, instead this is for the customers
		- no dish modifications, instead enter remarks
		- online orders are via credit card. cash may lead to scams
		- orders sent are viewed in the pos as a saved order with order number (osaved)
		- customers who registers or create an account, they are saved as an aws user
		- ## mobile
		- for client/restaurant use only
		- # pos dashboard
		  
		  ___
		- # pos editor
		- ## mmt
		- editor data viewer and updater
		- ## editors menu
		- ### restaurant/dishes/delivery/printer
		- #### restaurant note
		- ##### restaurant list (left sidebar)
		- ##### restaurant note editor
		- after clicking the restaurant in the list
		- editor for restaurant note (located at the top of the restaurant screen in the pos, top middle)
		- attached file for the restaurant menu
		  
		  
		  ___
		- #### category
		- category note after selecting a category
		- ##### category list (left 2nd column)
		- ##### category editor
		  
		  
		  ___
		- #### size info editor
		- located at the dish size section
		- ##### restaurant
		- restaurant size info note are shown by default
		- ##### category
		- if set, the size info will show after selecting the category
		  
		  
		  ___
		- #### dish note
		- note after selecting a dish
		- ##### restaurant
		- ##### dish list (3rd column)
		- ##### dish editor
		  
		  
		  ___
		- #### coupon note
		- after selecting the coupon category
		- ##### restaurant list
		- ##### coupon editor
		  
		  
		  ___
		- #### restaurant time
		- ##### restaurant selector
		- ##### restaurant time list
		- ##### restaurant time editor
		- ###### type
		- lunch
		- combo (dinner)
		- closed
		- size4
		- off
		- on
		- open
		  
		  
		  ___
		- #### order time
		- ##### restaurant selector
		- ##### order time editor
		- ###### base time
		- restaurant pickup and delivery estimated order time base on time
		- ###### order total
		- estimated order time base on price?
		- ###### distance estimate
		- estimated order time base on distance of the customer address from the restaurant's location
		  
		  
		  ___
		- #### dish size text
		- ##### restaurant selector
		- ##### dish size text editor
		- base on category.
		- size1 : usually small
		- size2 : usually large
		- lunch
		- dinner : usually combo
		- size3 : usually medium or median
		- size4 : usually family size 
		  
		  
		  ___
		- #### restaurant
		- ##### restaurant list
		- ##### restaurant editor
		- restaurant information
		  
		  
		  ___
		- #### matrix
		- ##### restaurant list
		- ##### category list
		- ##### matrix editor
		- import/download excel file containing the matrix
		  
		  
		  ___
		- #### delivery address
		- notes base on customer address for delivery
		- ##### restaurant selector
		- ##### delivery address editor
		  
		  
		  ___
		- #### delivery fee
		- ##### restaurant selector
		- ##### delivery fee editor
		- ###### distance
		- fee base on minimum distance and delivery
		- ###### city
		- fee base on city
		  
		  
		  ___
		- #### printer editor
		- printers and receipt templates
		- ##### restaurant selector
		- ##### printer editor
		  
		  
		  ___
		  
		  ___
		  
		  ___
		- ### credit cards
		- #### credit card note
		- ##### restaurant list
		- ##### credit card note editor
		- accepted credit cards, required credit card info stripe info, propay info, and the editor
		  ___
		- #### cc processing fee editor
		- ##### restaurant selector
		- ##### credit card note editor
		- fee base on minimum amount
		  
		  ___
		- #### stripe account
		- ##### restaurant selector
		- ##### stripe account editor
		- restaurant information
		- owner information
		- banking information
		  
		  ___
		- #### stripe rate
		- ##### restaurant selector
		- ##### stripe rate editor
		- stripe rate, per card charge, and daily fee
		  
		  ___
		- #### propay account
		- ##### restaurant selector
		- ##### propay account editor
		- personal information
		- bank account
		- gross billing
		- address
		- beneficial owner information
		  
		  ___
		- #### propay status
		- ##### restaurant selector
		- ##### propay status editor
		- add note
		  ___
		- ### others (business address, geofence, announcements, sms)
		- #### business address
		- restaurant branches
		- ##### restaurant selector
		- ##### business address editor
		  
		  ___
		- #### geofence
		- restaurant branches
		- ##### restaurant selector
		- ##### geofence editor
		- select branch address
		- set map coordinates scope
		  
		  ___
		- #### accouncement editor
		  
		  ___
		- #### sms
		- ##### restaurant list
		- ##### pickup/delivery sms text template
		  
		  ___
		- ### phone/mobile app
		- #### restaurant phone
		- ##### restaurant selector
		- ##### restaurant phone editor
		  
		  ___
		- #### mobile client
		- ##### restaurant selector
		- ##### mobile client editor
		- restaurant account for mobile app
		  
		  ___
		  
		  
		  ___
		- # queue display
		- UI to display calls that are in queue
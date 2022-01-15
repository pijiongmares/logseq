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
					- ATT (Average Talk Time)
					- AWT (Average Work Time)
					- AHT (Talk + Work)
				- ### Call Statistics Report
					- Agent & restaurant call stats (customers (customers of the restaurants) & clients(restaurants))
				- ### My Schedule
					- #### My Schedule
						- Shows the schedule of the agent
					- #### My Activity
						- Timekeeping record (for time in/out select wonders in aux, wait for 2 mins, then select logout)
				- ### Mistakes & Coaching
					- Mistake reports
				- ### News
					- New restaurants and features (processes) bulletin
				- ### Queue
					- Current queued calls for the agent
				- ### Call History
					- Call summary of the agent
					- Clicking on the records will show a popup for playing the recorded call
					- #### Clients
						- Clients/restaurant owners call
					- #### Outbounds
						- Outbound calls
					- #### Inbounds
						- Inbound calls
					- #### Finished
						- Finished calls
					- #### Abandoned
						- Abandoned calls
						- No one received the call
					- #### Calendar
						- Select date to view
					- ### AUX
						- Agent status (ready, mgmt, callback, wonders, coaching, sbs, meeting, restroom, other, logout)
						- Agent must be ready in order to be able to take a call
					- ### Restaurant Color Coding
						- Blue : active
						- Yellow : onboarding
						- Red : offboarding
						- White : for testing
				-
			- ## Restaurant Order Screen
				- Automatically shows when the agent receives a call from the customer ordering to a specific restaurant
				- Can also be accessed by clicking the restaurant from the home screen
					- ### Order Types
						- #### Pick-Up
							- Can be selected with online (order made online) or not online (order made via phone)
							- Address is optional
						- #### Delivery
							- Can be selected with online (order made online) or not online (order made via phone)
						- #### Online (Managers Use Only)
							- Toggle button. used together with pick-up or delivery option
						- #### More Button Option
							- #### Order Section (2nd Column from the Left)
								- Shows the customer information, payment, status and the order details
								- if agent value is "online", it means the order was made with online button enabled (manager's use only)
								- Order has versions
									- 1. **Mistake** - create a report for a mistake with an order (either an agent mistake, qa, coaching, or a possible bug in the system)
									- 2. **Modify** - use to modify current date sent orders
									- 3. **Void** - void the order
									- 4. **Reminder** - used to warn or give a message to an agent for that order
										- run out of specific dish
										- can set time occurence
									- 5. **Rush** - rush order. provide reason
							- #### Order Filters
								- Today, delivery, pickup, saved, online, and date (select date of order)
							- #### Order List
								- Shows the list of orders sent
								- Gray colored orders means it is from the previous days
								- White are saved orders or orders made from sesame.menu (osaved)
								- Green are today's orders
								- Red are voided
							- #### Call List Relative (No Direct Link to Orders)
								- Used to review orders of the customer
								- Calls are not linked to any orders. It is used to review the orders using the call or calls
							- #### Call Section (Right)
								- Shows the orders and call history (inbound and outbound) of the agent for the selected restaurant
								- Call : customer/client number or any number. also shows the saved contact information for the restaurant
								- Recorded time follows the restaurant's local time
								- Disable calls (for selected agents only) : option to redirect call to restaurant or the restaurant is close
						- ### Customer Information and Order List Section (Left Sidebar)
							- Phone number
							- Name
							- Address (street, apt/house/biz no., city) with distance in miles between the customer and the client
							- Order remarks
							- Conf note (customer remarks shows)\
							- Customer language radio button
							- Split order : separate order, payment, and receipt (sub orders)
							- #### Add and Minus Button
								- Increment or decrement quantity
							- #### Save
								- Used when customers are undecided and wish to call later then save the order
							- #### Home
								- Go back to home screen
							- #### Credit Card
								- Visa, Mastercard, Discover (min $12)
								- Credit card charge, cash charge, tip (can split payment to cash and card)
								- card number
								- expiration date (month and year)
								- cvv
								- billing zip code
								- call recording stops when entering credit card details
								- propay credit card are external that are sent to the restaurant for processing
								- can also be updated for sent orders
							- #### Send
								- Pay cash
								- Sent orders for the current date can still be modifed
							- #### Price Section
								- Discounts
								- Subtotal (discount applied)
								- Dish & delivery tax (not always the same)
								- Total price
								- ETA to finish
						- ### Restaurant Note (Top Middle)
						- ### Menu
							- #### Purple : modifications of the dish
								- Special order : dishes that do not exist maybe added
								- Menu : displays the soft version of the menu
							- #### Blue/Category
							- #### Category Note
							- #### Green/Dishes per Category
								- Clicking the dish will show the ask & click popup depending on the condition
								- Some dish has time conditions and when there are conditions that are set to "ask", ask & click popup will show
								- Combo size will also show ask & click
							- #### Ask & Click
								- Top section shows the current condition that can be applied to the selected dish
								- Option to select the side dish for the main dish selected
							- #### After the Ask & Click Popup
								- Reminder popup : ask the message displayed
								- After selecting the type of dish in ask & click, the dish options will be enabled in the located at the middle left
							- #### Size Info Note
							- #### Brown : sizes
								- L : Lunch
								- Qt/Quart : Large
								- md : Median
								- Pt/Pint : Small
								- C : Combo
							- #### Blue : rice substitutes
							- #### Green : regular dish substitutes
						- ### Transfer Call (Right Sidebar)
							- #### Transfer : transfer call to manager, Spanish, party order, Chinese, and external transfers (restaurant order & online order)
								- External transfers are orders that where processed using the clients portal/order system, not with POS
							- #### Help : ask for help and chinese assistant
		- # Online Order System (sesame.menu)
			- Like the POS but users are not the agent, instead this is for the customers
			- No dish modifications, instead enter remarks
			- Online orders are via credit card. cash may lead to scams
			- Orders sent are viewed in the POS as a saved order with order number (osaved)
			- Customers who registers or create an account, they are saved as an aws user
		- ## Mobile
		- For client/restaurant use only
		- # POS Dashboard
		- # POS Editor
			- ## Menu Management (mmt)
				- Editor data viewer and updater
			- ## Editors Menu
				- ### Restaurant/Dishes/Delivery/Printer
				- ### Restaurant Note
					- #### Restaurant List (Left Sidebar)
					- #### Restaurant Note Editor
						- After clicking the restaurant in the list
						- Editor for restaurant note (located at the top of the restaurant screen in the POS, top middle)
						- Attached file for the restaurant menu
					- ### Category
						- Category note after selecting a category
						- #### Category List (Left 2nd Column)
						- #### Category Editor
						  
						  
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
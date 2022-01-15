- # Orientation
  collapsed:: true
	- Founded 2012, Long Island, NYC
	  
	  1st Captive Inhouse BPO, fastest growing BPO in Dumaguete
	  
	  2019 started in Rockwell Business Center Manila
	  2020 started in Dumaguete
	  
	  Product / Service : Online technologies solution, restaurant clients (Majority are Chinese)
	  
	  Mission : To provide a virtuous ecosystem of tools and services to restaurant operations to help them be more successful
	  
	  Vision : We are the leading technology and customer service partner for restaurants everywhere
	-
	- ## Core values :
	- client-focused
	- people-centric
	- relentlessly high standard
	- deliver measurable results
	- be creative
	- work hard and have fun
	- be efficient
	- ## Attendance :
		- Notification Process
		- Respond to the google form for unplanned absence/tardiness notification form at least 2 hours prior to shift
		  Critical Workday (CWD Declaration)
		- Philippine Holidays - Legal and special non-working days
		- Day before and after PH holidays
		- Day before and after rest days or approved leaves
		- Payroll payout dates, day before and after payout dates
	- ## Payroll Legal Deductions :
		- No work, no pay
	- ## Loans
	- ## Payouts
		- Will be every other Friday (Biweekly), which will be a total of 26 payouts in a year rather than the normal 24 payouts / year
	- ## Company-Provided Benefits :
		- Leave benefits - 1st year 15, 1st anniv 20 (Mine is 26)
		- Forfeiture - leaves are carried over to the next year (Mine can be converted to cash)
		- HMO Benefits - Intellicare, 150,000 per illness per year (Mine can add 4 dependents)
		- Life Insurance - 300,000
	- ## House Rules And Security Guidelines
		- Claygo - clean as you go
		- Always keep the doors close
		- Wear company Id all the time
		- With lockers
		- Health Declaration Form every day when going onsite
- # Engineering Introduction
  collapsed:: true
	- # Onboarding with Sir Arman
		- Jira - tasks - [Wonderers - Agile Board - Jira (atlassian.net)](https://wondersco.atlassian.net/secure/RapidBoard.jspa?rapidView=58&projectKey=SKT)
		- Confluence - for documentations - [BA Corner - Confluence (atlassian.net)](https://wondersco.atlassian.net/wiki/spaces/BA/overview)
		- Wonders service desk portal - for hr/it concerns - [WONDERS SERVICE DESK PORTAL - Jira Service Management (atlassian.net)](https://wondersco.atlassian.net/servicedesk/customer/portals)
		- POS - phone order system [POS (letsdochinese.com)](https://mnl-api.letsdochinese.com/KJTCore/resources/nonagent.html)
		- POS - phone order system (for agents) [POS (letsdochinese.com)](https://mnl-api.letsdochinese.com/KJTCore/resources/agentwithmetrics.html)
		- Github wonders - [Wonders Coporation (github.com)](https://github.com/kjt01)
		- ## Probitionary Period
			- Employee's feedback
			- Manager's feedback
		- ## Policies : able to adhere required to me (tasks and company policies)
			- Customer service
				- Improve system stability and availability
				- Add value to customers by developing features and providing end to end support
			- Internal support and services
				- Deliver ease to use and efficient applications for our internal users
			- Team performance and culture
				- Create a culture of scalability, continuous progression, and fosterin trust
		- ## Filing of Leave
			- PTO (personal time off) approval
			- Email PTO and wait for approval
			- Google calendar set PTO sched
			- NICE : add activity for the PTO sched
	- # Onboarding with Sir Nicko
		- Mission : To provide a virtuous ecosystem of tools and services to retaurant operations to help them be more successful
		- Vision : We are the leading techonology and customer service partner for restaurants everywhere
		- Order processing, credit card payments, delivery fulfillment
		- Steve (ceo) and Dennis Lin, Bobby VP, BJ Sys Arch, Sherwin VP PH Country Head
		- Arman - engineering manager
		- Jegger - team lead
		  JZ - backend dev supervisor
		  Nico - IT Ops
		  Joseph Nicko - HR business partner for engineering
- # Onboarding
  collapsed:: true
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
		- # Mobile
			- For client/restaurant use only
		- # POS Dashboard
		- # POS Editor
			- ## Menu Management (mmt)
				- Editor data viewer and updater
			- ## Editors Menu
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
				- ### Size Info Editor
					- Located at the dish size section
					- #### Restaurant
						- Restaurant size info note are shown by default
					- #### Category
						- If set, the size info will show after selecting the category
				- ### Dish Note
					- Note after selecting a dish
					- #### Restaurant
					- #### Dish List (3rd Column)
					- #### Dish Editor
				- ### Coupon Note
					- After selecting the coupon category
					- #### Restaurant List
					- #### Coupon Editor
				- ### Restaurant Time
					- #### Restaurant Selector
					- #### Restaurant Time List
					- #### Restaurant Time Editor
					- #### Type
						- Lunch
						- Combo (dinner)
						- Closed
						- Size4
						- Off
						- On
						- Open
				- ### Order Time
					- #### Restaurant Selector
					- #### Order Time Editor
						- #### Base Time
							- Restaurant pickup and delivery estimated order time base on time
						- #### Order Total
							- Estimated order time base on price?
						- #### Distance Estimate
							- Estimated order time base on distance of the customer address from the restaurant's location
				- ### Dish Size Text
					- #### Restaurant Selector
					- #### Dish Size Text Editor
						- Base on category.
						- Size1 : usually small
						- Size2 : usually large
						- Lunch
						- Dinner : usually combo
						- Size3 : usually medium or median
						- Size4 : usually family size
				- ### Restaurant
					- #### Restaurant List
					- #### Restaurant Editor
						- Restaurant information
				- ### Matrix
					- #### Restaurant List
					- #### Category List
					- #### Matrix Editor
						- Import/download excel file containing the matrix
				- ### Delivery Address
					- Notes base on customer address for delivery
					- #### Restaurant Selector
					- #### Delivery Address Editor
				- ### Delivery Fee
					- #### Restaurant Selector
					- #### Delivery Fee Editor
						- #### Distance
							- Fee base on minimum distance and delivery
						- #### City
							- Fee base on city
				- ### Printer
					- Printers and receipt templates
					- #### Restaurant Selector
					- #### Printer Editor
				- ### Credit Card Note
					- #### Restaurant List
					- #### Credit Card Note Editor
						- Accepted credit cards, required credit card info stripe info, Propay info, and the editor
				- ### CC Processing Fee
					- #### Restaurant Selector
					- #### Credit Card Note Editor
						- Fee base on minimum amount
				- ### Stripe Account
					- #### restaurant selector
					- #### stripe account editor
						- Restaurant information
						- Owner information
						- Banking information
				- ### Stripe Rate
					- ##### Restaurant Selector
					- ##### Stripe Rate Editor
						- Stripe rate, per card charge, and daily fee
				- ### Propay Account
					- #### Restaurant Selector
					- #### Propay Account Editor
						- Personal information
						- Bank account
						- Gross billing
						- Address
						- Beneficial owner information
				- ### Propay Status
					- #### Restaurant Selector
					- #### Propay Status Editor
						- Add note
				- ### Business Address
					- Restaurant branches
					- #### Restaurant Selector
					- #### Business Address Editor
				- ### Geofence
					- Restaurant branches
					- #### Restaurant Selector
					- #### Geofence Editor
						- Select branch address
						- Set map coordinates scope
				- ### Announcement Editor
				- ### SMS
					- #### Restaurant List
					- #### Pickup/Delivery SMS Text Template
				- ### Restaurant Phone
					- #### Restaurant Selector
					- #### Restaurant Phone Editor
				- ### Mobile Client
					- #### Restaurant Selector
					- #### Mobile Client Editor
						- Restaurant account for mobile app
		- # Queue Display
			- UI to display calls that are in queue
- # Onboarding With JZ
  collapsed:: true
	- # Entities
	  Client 
	  Customer
	  Internal
		- Agents
		- Training team
		- Content team
	- # Ticket Flow
	  Users -> WIT - Support Ticket (for IT Ops) -> IT Support Team -> SKT Ticket (Jira)
	- # NGINX & Webservices Setup
		- ## QA & DEV env
			- 1 Server for Docker App
			- 1 Server for NGINX
		-
		- ## Learn Liquibase
		-
		- **.core nginx for (PUT, POST, DELETE)**
		- **.content-pusher-pool NGINX for (GET)**
		-
		- UI -> .lic, .jazz, kmc, etc. nginx -> .core nginx -> Backend Service/Server
		-
		- Backend -> Backend
		- .core nginx
		-
		- Public -> Backend Service/Server
		- .edge
	-
	- # Cronicle
		- Push changes using Cronicle
		- Push by rid (changes in Staging DB compare to PROD by restaurant id )
		- Synckjtdb (all changes in Staging DB compare to PROD)
		- ## synckjtdb - 2AM (1hr)
		- ## synckjtdb_upgrade - 4AM (20min)
		- ## if synckjtdb was run manually, also run synckjtdb_upgrade
		-
		- ## Cronicle (pictor and ursa servers)
		- ## Cron job manager
	- # Monitoring Tools
		- ## Rollbar
			- Log monitoring tool
		- ## Grafana
			- Application performance monitoring tool
		- ## Kibana
			- Log viewer/visualization
	- # AWS
		- ## API Gateway
			- Routing (sesame.menu and mobile only)
		- ## S3
			- File storage server
		- ## EC2
			- Elastic compute cloud (servers)
	- # Pain Points
		- Users (customer, client, content team)
		- Investigate by BA
		- BA sign off (Jira tickets)
		- Develop (Dev to Dev, always coordinate)
		- Any changes will be updated in Jira tickets
		- QA Testing
		- UAT Training
		- QA Sign Off
		- PROD
		- ## Metrics
			- For measuring the effectiveness of the change/additional feature
			- Possible of multiple phases if requirements are not met
- # Ways Of Working
  collapsed:: true
	- # Pull Request Format
		- \<Epic\> - \<User story/bug ticket\> - \<User story/bug ticket title\>
		- SKT-6497 - SKT-6761 - Change English and Chinese Texts in Chinese Modal
		-
		- Approver: to approve/code review only the PR
		- Reviewer: is the one who will merge the change
		- For bug, create new bug tickets and link to the user story
		- For UI change, attach the screenshot in the PR
		- After merging, delete the branch
	- # Commit Notes
		- SKT-6497 - SKT-6761 - Change English and Chinese Texts in Chinese Modal
		- Don't use: git commit -m ""
		- Use instead: git commit
		-
		- First line: SKT-6497-SKT-6761-\<message\>
		  \<space\>
		- Succeeding lines: \<changes made\>
	- # Pull Request Notes
		- First line: Epic: \<link\>
		- Second line: Story: \<link\>
		- \<space\>
		- \<changes made\>
	- # Merge Options
		- Squash and merge: will squash your multiple commits before merging your change to master
		- Rebase and merge: rebase first your branch with master branch
		- Create a merge commit: create new commit with merging your change to master
	- ## When Squashing Commits
		- Remove "SKT-6497 - SKT-6761 - Change English and Chinese Texts in Chinese Modal" in each commits
		- Retain changes
- # My Workstation Environment
  collapsed:: true
	- # MySQL Workstation
		- Download both the kjt and kjtcallctr script files in [kjtcallctr database copy](https://drive.google.com/drive/u/2/folders/1ubCcGcHjmdNmw4KxE1QveSmrU41qoY3x) (use wonders google account) and run in it the local mysql database
		- ## Local Creds
			- Windows service name : MySQL57
			- Port : 3306
			- Username : appuser
			- Password : p@ssw0rd
		- ## Database VPN Access
			- [mnl-db.letsdochinese.com](http://mnl-db.letsdochinese.com/) connects using pseudothyrum vpn
			- [foxtrot.letsdochinese.com](http://foxtrot.letsdochinese.com/) connects using  aditus vpn
	- # Liquibase ChangeLogs for kjt and kjtcallctr
	- ## kjt-db-kjtcore and kjt-db-kjtcallctr github
		- Clone [kjt-db-kjtcore git repo](https://github.com/kjt01/kjt-db-kjtcore)
		- Clone [kjt-db-kjtcallctr](https://github.com/kjt01/kjt-db-kjtcallctr)
	- ## Liquibase Maven commands
		- mvn liquibase:status -Plocal -Dliquibase.contexts=local -Dliquibase.changeLogFile=changelog-master -Dliquibase.username=appuser -Dliquibase.password=123
		- mvn liquibase:update -Plocal -Dliquibase.contexts=local -Dliquibase.changeLogFile=changelog-master -Dliquibase.username=appuser -Dliquibase.password=123
		- mvn liquibase:rollback -Plocal -Dliquibase.contexts=local -Dliquibase.changeLogFile=changelog-master Dliquibase.username=appuser -Dliquibase.password=123 -Dliquibase.rollbackCount=1
	- # Redis
		- Download [sentinel_26379.conf](https://drive.google.com/file/d/1CFOT6nfyIVK9L4VcRPGOSP9uF9YDlNfO/view?usp=sharing) and move it to the redis directory
		- Download [redis desktop manager](https://drive.google.com/open?id=1dezAKxn9dufo7RwMpuyXee_x0V7kKyjI)
		- ## Local
			- Port : 6379
	- # Core Projects
		- ## Clone [kjt-pos-comm](https://github.com/kjt01/kjt-pos-comm)
			- Build mvn clean install -U -DskipTests=true
		- ## Clone [kjt-redis-comm](https://github.com/kjt01/kjt-redis-comm.git)
			- Build mvn clean install -U -DskipTests=true
		- ## Clone [payment-processing-comm](https://github.com/kjt01/payment-processing-comm)
			- Build mvn clean install -U -DskipTests=true
		- ## Clone [kjt-ext-prop](https://github.com/kjt01/kjt-ext-prop)
		- ## Clone [kjt-freemarker-templates](https://github.com/kjt01/kjt-freemarker-templates)
		- ## Clone [kjt-pos-core](https://github.com/kjt01/kjt-pos-core)
		- Build mvn clean install -U -DskipTests=true.
		- After build, copy the KJTCore.war file from the target folder to the Tomcat webapp folder (rename to KJTCore.war).
		- At Tomcat conf, update the catalina.properties. Append the resource path of kjt-ext-prop and path of kjt-freemaker-templates in the common.loader key.
		- At Tomcat conf, update the context.xml. Add the following the change DB account
		  
		  ``` xml
		  <Resource auth="Container" driverClassName="com.mysql.jdbc.Driver" logAbandoned="true" maxActive="100" maxIdle="30" maxWait="10000" name="jdbc/kjt" password="kjt" removeAbandoned="true" removeAbandonedTimeout="60" type="javax.sql.DataSource" url="jdbc:mysql://localhost:3306/kjt?autoReconnect=true&amp;characterEncoding=UTF-8&amp;noAccessToProcedureBodies=true" username="root" validationQuery="select 1"/>
		  
		  <Resource auth="Container" driverClassName="com.mysql.jdbc.Driver" logAbandoned="true" maxActive="100" maxIdle="30" maxOpenPreparedStatements="100" maxWait="10000" name="jdbc/kjtcallctr" password="kjt" poolPreparedStatements="true" removeAbandoned="true" removeAbandonedTimeout="60" type="javax.sql.DataSource" url="jdbc:mysql://localhost:3306/kjtcallctr?autoReconnect=true&amp;noAccessToProcedureBodies=true" username="root" validationQuery="select 1"/>
		  
		  <Resource auth="Container" driverClassName="com.mysql.jdbc.Driver" logAbandoned="true" maxActive="100" maxIdle="30" maxOpenPreparedStatements="100" maxWait="10000" name="jdbc/kjtcallctrrep" password="kjt" poolPreparedStatements="true" removeAbandoned="true" removeAbandonedTimeout="60" type="javax.sql.DataSource" url="jdbc:mysql://localhost:3306/kjtcallctr?autoReconnect=true&amp;noAccessToProcedureBodies=true" username="root" validationQuery="select 1"/>
		  
		  ```
		- At Tomcat conf, update server.xml. Look for port 8080 and change to 8081
		- Copy the mysql-connector-java from .m2 repository to Tomcat lib folder
		- kjt-pos-core is currently being divided into smaller services. following are so far the existing projects that are extracted from kjt-pos-core
		  	1.  content-config-server
		  	2.  order-processing-service
		  	3.  user-config-server
		- kjt-sms-connect-service needs core-client-comm (gradle) and sms-service-comm (maven)
- # Applications Setup Changes (For Local Only)
  collapsed:: true
	- ## content-config-service
		- ### appication-local.yml
			- ``` yml
			  	
			  	# username and password changed
			  	application: 
			  		datasource: 
			  			type: com.zaxxer.hikari.HikariDataSource
			  			jdbc: jdbc:mysql://localhost:3306/kjt?autoReconnect=true&characterEncoding=UTF-8&noAccessToProcedureBodies=true&useSSL=false&serverTimezone=America/New_York
			  			username: root
			  			password: p@ssw0rd
			  	
			  	```
		- ### pom.xml
			- ```xml
			  	<!--jabylon repo commented-->
			  	 <repositories>
			  		 <!-- jhipster-needle-maven-repository -->
			  		 <!-- <repository>
			  			 <id>jabylon</id>
			  			 <url>http://www.jabylon.org/maven/</url>
			  		 </repository> -->
			  	 </repositories>
			  	
			  	<!--added local profile-->
			  	<profile>
			  		 <id>local</id>
			  		 <dependencies>
			  			 <dependency>
			  				 <groupId>org.springframework.boot</groupId>
			  				 <artifactId>spring-boot-starter-undertow</artifactId>
			  			 </dependency>
			  		 </dependencies>
			  		 <build>
			  			 <plugins>
			  				 <plugin>
			  					 <artifactId>maven-clean-plugin</artifactId>
			  					 <configuration>
			  					 <filesets>
			  					 <fileset>
			  					 <directory>D:/work/wonders\ corp/projects/content-config-server/src/main/resources/static</directory>
			  					 </fileset>
			  					 </filesets>
			  					 </configuration>
			  				 </plugin>
			  					 <plugin>
			  						 <groupId>org.springframework.boot</groupId>
			  						 <artifactId>spring-boot-maven-plugin</artifactId>
			  						 <configuration>
			  							<mainClass>com.kjt.ccs.ContentConfigServerApp</mainClass>
			  						 </configuration>
			  						 <executions>
			  							 <execution>
			  								 <goals>
			  									<goal>build-info</goal>
			  								 </goals>
			  							 </execution>
			  						 </executions>
			  					 </plugin>
			  				 <plugin>
			  					 <groupId>pl.project13.maven</groupId>
			  					 <artifactId>git-commit-id-plugin</artifactId>
			  				 </plugin>
			  			 </plugins>
			  		 </build>
			  		 <properties>
			  			 <!-- default Spring profiles -->
			  			 <spring.profiles.active>local${profile.swagger}${profile.no-liquibase}</spring.profiles.active>
			  		 </properties>
			  	 </profile>
			  ```
	- ## kjt-sms-connect-service
		- ### pom.xml
			- ``` xml
			  		<!--added local profiles-->	
			  		 <profiles>
			  			 <profile>
			  				 <id>local</id>
			  				 <activation>
			  					<activeByDefault>true</activeByDefault>
			  				 </activation>
			  				 <build>
			  					 <plugins>
			  						 <plugin>
			  							 <groupId>org.springframework.boot</groupId>
			  							 <artifactId>spring-boot-maven-plugin</artifactId>
			  							 <configuration>
			  								 <profiles>
			  									<profile>local</profile>
			  								 </profiles>
			  							 </configuration>
			  						 </plugin>
			  					 </plugins>
			  				 </build>
			  			 </profile>
			  		 </profiles>
			  
			  ```
		- ### redis-config.xml
			- ``` xml
			  		<!--commented the variable ${master.name}-->
			  		 <bean id="redisSentinelConfigurationWithMaster" class="org.springframework.beans.factory.config.MethodInvokingFactoryBean">
			  			 <property name="targetObject" ref="redisSentinelConfiguration" />
			  			 <property name="targetMethod" value="master" />
			  			 <!-- <property name="arguments" value="${master.name}" /> -->
			  			 <property name="arguments" value="redis-master" />
			  		 </bean>
			  
			  		<!--commented the variable sentinel.host and sentinel.port-->
			  		<bean id="redisSentinelConfigurationWithMasterAndFirstSentinel" class="org.springframework.beans.factory.config.MethodInvokingFactoryBean">
			  			 <property name="targetObject" ref="redisSentinelConfigurationWithMaster" />
			  			 <property name="targetMethod" value="sentinel" />
			  			 <property name="arguments">
			  				 <list>
			  					 <!-- <value>${first.sentinel.host}</value>
			  					 <value>${first.sentinel.port}</value> -->
			  					 <value>localhost</value>
			  					 <value>26379</value>
			  				 </list>
			  			 </property>
			  		 </bean>
			  
			  		 <bean id="redisSentinelConfigurationWithMasterAndSecondSentinel" class="org.springframework.beans.factory.config.MethodInvokingFactoryBean">
			  			 <property name="targetObject" ref="redisSentinelConfigurationWithMasterAndFirstSentinel" />
			  			 <property name="targetMethod" value="sentinel" />
			  			 <property name="arguments">
			  				 <list>
			  					 <!-- <value>${second.sentinel.host}</value>
			  					 <value>${second.sentinel.port}</value> -->
			  					 <value>localhost</value>
			  					 <value>26379</value>
			  				 </list>
			  			 </property>
			  		 </bean>
			  
			  		 <bean id="redisSentinelConfigurationWithMasterAndThirdSentinel" class="org.springframework.beans.factory.config.MethodInvokingFactoryBean">
			  			 <property name="targetObject" ref="redisSentinelConfigurationWithMasterAndSecondSentinel" />
			  			 <property name="targetMethod" value="sentinel" />
			  			 <property name="arguments">
			  				 <list>
			  					 <!-- <value>${third.sentinel.host}</value>
			  					 <value>${third.sentinel.port}</value> -->
			  					 <value>localhost</value>
			  					 <value>26379</value>
			  				 </list>
			  			 </property>
			  		 </bean>
			  
			  		<!--commented to change the password and database variable-->
			  		 <!-- <bean id="jedisConnFactory" class="org.springframework.data.redis.connection.jedis.JedisConnectionFactory"
			  		 p:use-pool="true" p:password="${redis.password}" p:database="${redis.dbindex}">
			  		 <constructor-arg ref="redisSentinelConfigurationWithMasterAndThirdSentinel" />
			  		 </bean> -->
			  		 <bean id="jedisConnFactory" class="org.springframework.data.redis.connection.jedis.JedisConnectionFactory"
			  		 p:use-pool="true" p:password="" p:database="0">
			  			<constructor-arg ref="redisSentinelConfigurationWithMasterAndThirdSentinel" />
			  		 </bean>
			  
			  ```
	- ## sms-customer-client/customerlocationsms.html
		- ``` js
		  	 const getBaseUrl = () => {
		  		 const currentUrl = window.location.href;
		  		 if (currentUrl.indexOf("localhost") > -1) {
		  			return "http://localhost";
		  		 } else if (currentUrl.indexOf("int.sesame") > -1) {
		  			return "https://int.sesame.menu";
		  		 } else if (currentUrl.indexOf("qa.sesame") > -1) {
		  			return "https://qa.sesame.menu";
		  		 } else {
		  			return "http://sesame.menu";
		  		 }
		  	 };
		  ```
	- ## user-config-server
		- ### application-local.yml
			- ``` yml
			  	# username and password changed
			  	application: 
			  		datasource: 
			  			type: com.zaxxer.hikari.HikariDataSource
			  			jdbc: jdbc:mysql://localhost:3306/kjt?autoReconnect=true&characterEncoding=UTF-8&noAccessToProcedureBodies=true&useSSL=false&serverTimezone=America/New_York
			  			username: root
			  			password: p@ssw0rd
			  ```
		- ### pom.xml
			- ``` xml
			  	<!--added local profiles-->	
			  	<profile>
			  		<id>local</id>
			  		<activation>
			  			<activeByDefault>true</activeByDefault>
			  		</activation>
			  		<dependencies>
			  			<dependency>
			  				<groupId>org.springframework.boot</groupId>
			  				<artifactId>spring-boot-starter-undertow</artifactId>
			  			</dependency>
			  			<dependency>
			  				<groupId>org.springframework.boot</groupId>
			  				<artifactId>spring-boot-devtools</artifactId>
			  				<optional>true</optional>
			  			</dependency>
			  		</dependencies>
			  		<build>
			  			<plugins>
			  				<plugin>
			  					<groupId>org.springframework.boot</groupId>
			  					<artifactId>spring-boot-maven-plugin</artifactId>
			  					<configuration>
			  						<profiles>
			  							<profile>local</profile>
			  						</profiles>
			  					</configuration>
			  				</plugin>
			  			</plugins>
			  		</build>
			  	</profile>
			  ```
		- ### redis-config.xml
			- ``` xml
			  	<!--commented to change the password and database variable-->
			  	<!-- <bean id="jedisConnFactory" 						class="org.springframework.data.redis.connection.jedis.JedisConnectionFactory"
			   p:use-pool="true"
			   p:password="${application.redis.password}"
			   p:database="${application.redis.dbindex.cache}"
			   p:poolConfig-ref="jedisPoolConfig">
			  		<constructor-arg ref="redisSentinelConfigurationWithMasterAndThirdSentinel" />
			  	</bean> -->
			  
			  	 <bean id="jedisConnFactory" class="org.springframework.data.redis.connection.jedis.JedisConnectionFactory"
			  	 p:use-pool="true"
			  	 p:password=""
			  	 p:database="0"
			  	 p:poolConfig-ref="jedisPoolConfig">
			  	 	<constructor-arg ref="redisSentinelConfigurationWithMasterAndThirdSentinel" />
			  	 </bean>
			  
			  	<!--commented to change the max total and idle variable-->
			  	<!-- <bean id="jedisPoolConfig" class="redis.clients.jedis.JedisPoolConfig"
			  	p:maxTotal="${application.redis.connection.max.total}"
			  	p:maxIdle="${application.redis.connection.max.idle}">
			  	 </bean> -->
			  
			  	<bean id="jedisPoolConfig" class="redis.clients.jedis.JedisPoolConfig"
			  	p:maxTotal="8"
			  	p:maxIdle="8">
			  	</bean>
			  
			  	<!--commented the variable sentinel.host and sentinel.port-->
			  	 <bean id="redisSentinelConfigurationWithMasterAndThirdSentinel" class="org.springframework.beans.factory.config.MethodInvokingFactoryBean">
			  		 <property name="targetObject" ref="redisSentinelConfigurationWithMasterAndSecondSentinel" />
			  		 <property name="targetMethod" value="sentinel" />
			  		 <property name="arguments">
			  			 <list>
			  				 <!-- <value>${application.third.sentinel.host}</value>
			  				 <value>${application.third.sentinel.port}</value> -->
			  				 <value>localhost</value>
			  				 <value>26379</value>
			  			 </list>
			  		 </property>
			  	 </bean>
			  
			  	 <bean id="redisSentinelConfigurationWithMasterAndSecondSentinel" class="org.springframework.beans.factory.config.MethodInvokingFactoryBean">
			  		 <property name="targetObject" ref="redisSentinelConfigurationWithMasterAndFirstSentinel" />
			  		 <property name="targetMethod" value="sentinel" />
			  		 <property name="arguments">
			  			 <list>
			  				 <!-- <value>${application.second.sentinel.host}</value>
			  				 <value>${application.second.sentinel.port}</value> -->
			  				 <value>localhost</value>
			  				 <value>26379</value>
			  			 </list>
			  		 </property>
			  	 </bean>
			  
			  	 <bean id="redisSentinelConfigurationWithMasterAndFirstSentinel" class="org.springframework.beans.factory.config.MethodInvokingFactoryBean">
			  		 <property name="targetObject" ref="redisSentinelConfigurationWithMaster" />
			  		 <property name="targetMethod" value="sentinel" />
			  		 <property name="arguments">
			  			 <list>
			  				 <!-- <value>${application.first.sentinel.host}</value>
			  				 <value>${application.first.sentinel.port}</value> -->
			  				 <value>localhost</value>
			  				 <value>26379</value>
			  			 </list>
			  		 </property>
			  	 </bean>
			  ```
	- ## nginx.conf
		- ### added **/map** on the uri to make route to customerlocationsms.html work
			- ``` conf
			  	 location /KJTCore/resources/map/ {
			  		 alias "D:/work/wonders corp/projects/sms-customer-client/";
			  		 try_files $uri $uri.html $uri/;
			  		 autoindex off;
			  		 expires -1;
			  	 }
			  ```
	-
- # Tasks
	- ## 101121 Enhance SMS Address Confirmation
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
				- Currently [sesame.menu](file:///S://sesame.menu) yung nasa domain na sini-send sa sms. ok lang ba to sa future? since possible mawala sa future yung sesame.menu - Ok lang, via nginx yung change sa future
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
-
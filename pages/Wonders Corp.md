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
-
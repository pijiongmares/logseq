- #Work #Wonders-Corp
- Description : My local setup and configurations for Wonders Corporation
-
- # My Workstation Environment
  collapsed:: true
	- # MySQL Workstation
	  collapsed:: true
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
	  collapsed:: true
		- ## kjt-db-kjtcore and kjt-db-kjtcallctr github
			- Clone [kjt-db-kjtcore git repo](https://github.com/kjt01/kjt-db-kjtcore)
			- Clone [kjt-db-kjtcallctr](https://github.com/kjt01/kjt-db-kjtcallctr)
		- ## Liquibase Maven commands
			- mvn liquibase:status -Plocal -Dliquibase.contexts=local -Dliquibase.changeLogFile=changelog-master -Dliquibase.username=appuser -Dliquibase.password=123
			- mvn liquibase:update -Plocal -Dliquibase.contexts=local -Dliquibase.changeLogFile=changelog-master -Dliquibase.username=appuser -Dliquibase.password=123
			- mvn liquibase:rollback -Plocal -Dliquibase.contexts=local -Dliquibase.changeLogFile=changelog-master Dliquibase.username=appuser -Dliquibase.password=123 -Dliquibase.rollbackCount=1
	- # Redis
	  collapsed:: true
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
	- ## content-config-service
	  collapsed:: true
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
	  collapsed:: true
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
		- ### application-local.properties
			- ```properties
			  # com.kjt.sms.web.socket.con=wss://localhost:8143/
			  com.kjt.sms.web.socket.con=ws://localhost:8143/
			  ```
	- ## sms-customer-client/customerlocationsms.html
	  collapsed:: true
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
	  collapsed:: true
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
		  <!-- <bean id="jedisConnFactory" class="org.springframework.data.redis.connection.jedis.JedisConnectionFactory"
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
	  collapsed:: true
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
	- ## kjt-pos-callctr-client
	  collapsed:: true
		- ### webrtc-common.js
			- ``` js
			  // added localhost to dns for websocket initialization on screenshare.js
			  let dns = {
			    localhost: {
			      app: "localhost",
			      voip: "localhost",
			      stun: "localhost:19302",
			      sswebsocket: "localhost",
			      turn: "localhost:3478",
			      alwaysonServer: 1
			    },
			    int_env: {
			      app: "int.letsdochinese.com",
			      voip: "int.letsdochinese.com",
			      stun: "stun.l.google.com:19302",
			      sswebsocket: "int.letsdochinese.com",
			      turn: "turn-qa.letsdochinese.com:3478",
			      alwaysonServer: 1
			    },
			    qa_env: {
			      app: "qa.letsdochinese.com",
			      voip: "lizard.letsdochinese.com",
			      stun: "stun.l.google.com:19302",
			      sswebsocket: "qa.letsdochinese.com",
			      turn: "turn-qa.letsdochinese.com:3478",
			      alwaysonServer: 1
			    },
			    qa2_env: {
			      app: "qa.letsdochinese.com",
			      voip: "lizard2.letsdochinese.com",
			      stun: "stun.l.google.com:19302",
			      sswebsocket: "qa.letsdochinese.com",
			      turn: "turn-qa.letsdochinese.com:3478",
			      alwaysonServer: 2
			    },
			    dev_env: {
			      app: "dev.letsdochinese.com",
			      voip: "dev.letsdochinese.com",
			      stun: "stun.l.google.com:19302",
			      sswebsocket: "dev.letsdochinese.com",
			      turn: "turn-qa.letsdochinese.com:3478",
			      alwaysonServer: 1
			    },
			    prod_env: {
			      app: "lic-api.letsdochinese.com",
			      voip: "lynx.letsdochinese.com",
			      stun: "lynx.letsdochinese.com:3478",
			      sswebsocket: "corenginx.letsdochinese.com",
			      turn: "turn.letsdochinese.com:4478",
			      alwaysonServer: 3
			    },
			    prod_dr_env: {
			      app: "dr-api.letsdochinese.com", // DR Akorbi
			      voip: "lynx.letsdochinese.com",
			      stun: "lynx.letsdochinese.com:3478",
			      sswebsocket: "corenginx.letsdochinese.com",
			      turn: "turn.letsdochinese.com:4478",
			      alwaysonServer: 3
			    },
			    prod_dr_adv_env: {
			      app: "dr-adv-api.letsdochinese.com", // DR Advensus
			      voip: "lynx.letsdochinese.com",
			      stun: "lynx.letsdochinese.com:3478",
			      sswebsocket: "corenginx.letsdochinese.com",
			      turn: "turn.letsdochinese.com:4478",
			      alwaysonServer: 3
			    },
			    prod_qfn_env: {
			      app: "qfn-api.letsdochinese.com", // PH Qualfon Duma
			      voip: "pavo.letsdochinese.com",
			      stun: "pavo.letsdochinese.com:3478",
			      sswebsocket: "corenginx.letsdochinese.com",
			      turn: "turn.letsdochinese.com:4478",
			      alwaysonServer: 2
			    },
			    prod_qfm_env: {
			      app: "qfm-api.letsdochinese.com", // PH Qualfon Manila
			      voip: "pavo.letsdochinese.com",
			      stun: "pavo.letsdochinese.com:3478",
			      sswebsocket: "corenginx.letsdochinese.com",
			      turn: "turn.letsdochinese.com:4478",
			      alwaysonServer: 2
			    },
			    prod_kmc_env: {
			      app: "kmc-api.letsdochinese.com", // PH KMC
			      voip: "norma.letsdochinese.com",
			      stun: "norma.letsdochinese.com:3478",
			      sswebsocket: "corenginx.letsdochinese.com",
			      turn: "turn.letsdochinese.com:4478",
			      alwaysonServer: 1
			    },
			    prod_mnl_env: {
			      app: "mnl-api.letsdochinese.com", // PH Internet Cafe
			      voip: "voip-edge.letsdochinese.com",
			      stun: "voip-edge.letsdochinese.com:3478",
			      sswebsocket: "coreapp.letsdochinese.com",
			      turn: "coreapp.letsdochinese.com:4478",
			      alwaysonServer: 6
			    },
			    prod_ph_env: {
			      app: "ph-api.letsdochinese.com", // PH ph-api
			      voip: "lacerta.letsdochinese.com",
			      stun: "lacerta.letsdochinese.com:3478",
			      sswebsocket: "corenginx.letsdochinese.com",
			      turn: "turn.letsdochinese.com:4478",
			      alwaysonServer: 5
			    },
			    prod_dgt_env: {
			      app: "dgt-api.letsdochinese.com", // DGT Vitro Data Center
			      voip: "antares.letsdochinese.com",
			      stun: "antares.letsdochinese.com:3478",
			      sswebsocket: "corenginx.letsdochinese.com",
			      turn: "turn.letsdochinese.com:4478",
			      alwaysonServer: 4
			    }
			  };
			  
			  // added localhost validation to return its sswebsocket in the dns object
			  function getSSWebsocketDns() { // get the voip server dns by hostname
			    var hostname = location.hostname;
			    if (hostname == dns.prod_env.app) {
			      return dns.prod_env.sswebsocket;
			    } else if (hostname == dns.prod_kmc_env.app) {
			      return dns.prod_kmc_env.sswebsocket;
			    } else if (hostname == dns.prod_qfn_env.app) {
			      return dns.prod_qfn_env.sswebsocket;
			    } else if (hostname == dns.prod_qfm_env.app) {
			      return dns.prod_qfm_env.sswebsocket;
			    } else if (hostname == dns.prod_dr_env.app) {
			      return dns.prod_dr_env.sswebsocket;
			    } else if (hostname == dns.prod_dr_adv_env.app) {
			      return dns.prod_dr_adv_env.sswebsocket;
			    } else if (hostname == dns.prod_mnl_env.app) {
			      return dns.prod_mnl_env.sswebsocket;
			    } else if (hostname == dns.prod_ph_env.app) {
			      return dns.prod_ph_env.sswebsocket;
			    } else if (hostname == dns.prod_dgt_env.app) {
			      return dns.prod_dgt_env.sswebsocket;
			    } else if (hostname == dns.int_env.app) {
			      return dns.int_env.sswebsocket;
			    } else if (hostname == dns.qa_env.app) {
			      return dns.qa_env.sswebsocket;
			    } else if (hostname == dns.dev_env.app) {
			      return dns.dev_env.sswebsocket;
			    } else if (hostname == dns.localhost.app) {
			      return dns.localhost.sswebsocket;
			    } else {
			      console.log("WARNING: Using unknown environment. Please refer to getSSWebsocketDns function.");
			      return;
			    }
			  }
			  ```
		- ### chrome-screenshare-app.js
			- ``` js
			  function connectAndRegister(platform, registeruser, turnserver) {
			      globalturnserver = turnserver;
			      serverAddress = platform;
			    	// disable secures websocket through https
			      // serverString = 'wss://' + serverAddress + ':8143';
			      serverString = 'ws://' + serverAddress + ':8143';
			      if (chromesssock != null && chromesssock.readyState == 1) {
			          console.log('Closing the prior websocket connection');
			          chromesssock.close();
			          chromesssock = null;
			      }
			      chromesssock = new ReconnectingWebSocket(serverString);
			      chromesssock.addEventListener("message", onWebSocketMessage, false);
			  
			      chromesssock.onopen = function(e) {
			          console.log('Connection established!');
			          var millisecondsToWait = 1250;
			          setTimeout(function() {
			              console.log('Trying to register the user on the screenshare websocket');
			              chromesssock.send(JSON.stringify({
			                  "user": registeruser,
			                  "messageType": "registerUser"
			              }));
			              fromUsr = registeruser;
			          }, millisecondsToWait);
			          // registerUser(registeruser);
			      };
			  }
			  ```
-
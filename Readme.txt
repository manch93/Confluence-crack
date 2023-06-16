Instruction for JIRA Software & JIRA Core, installed as service on windows:

NOTE: JRE SHOULD BE ALREADY INSTALLED ON YOUR SYSTEM. IF IT'S NOT, INSTALL IT FIRST!

0. Install JIRA Software or JIRA Core as service (By Default)
	DO NOT RUN JIRA AFTER INSTALLATION (Untick "Start" AT END OF SETUP)

1. Copy atlassian-agent.jar to root of drive C:\
	So it will be: "C:\atlassian-agent.jar"

2. From start menu, search for services & open it
	2.1. Find Atlassian Jira Service, Double click on it, Copy Service Name (Example: JiraSoftware060122091949)
	     Close this window

3. From start menu, search for CMD & open it
	3.1. Type CD <bin directory of your Jira application installation directory> & Enter
		If installed on default directory, it will be: cd C:\Program Files\Atlassian\Jira\bin
	
	3.2. Type tomcat8w //ES//<Service Name> & Enter
		Example: tomcat8w //ES//JiraSoftware060122091949

4. On opened window (Atlassian Jira Properties), go to Java tab, Add -javaagent:C:\atlassian-agent.jar to end of 
   Java Options (add it as last line). Click OK, Close CMD.

5. From Start menu, search for Stop Jira Service & run it, then search for Start Jira Service & run it
   then right click on Atlassian Jira Service (on Services window) & Select start (if it's available)

6. Run Jira from http://localhost:8080/ (Or access Jira on start menu)
	if it's not accessible, wait some minutes & try again later

7. Choose i’ll set it up my self & proceed steps

8. When asked for license, open cmd
	8.1. Type CD C:\ & enter
	8.2. Type java -jar atlassian-agent.jar -m <your email> -o <your organization> -p <product to activate> -s <Server ID> & Enter
		Example for JIRA Software: java -jar atlassian-agent.jar -m downloadly@somemail.com -o downloadly -p jira -s BOUT-MSPD-VUPT-3PYD
		Example for JIRA Core: java -jar atlassian-agent.jar -m downloadly@somemail.com -o downloadly -p jc -s BOUT-MSPD-VUPT-3PYD
		
		NOTE1: Server ID is shown at License request step on JIRA Setup wizard
		NOTE2: Product codes & more parameters can be obtained by executing java -jar atlassian-agent.jar
	
	8.3. Copy produced license to Jira License request field

9. ENJOY!

NOTE: if you installed JIRA whitout service, adding a javaagent requires different steps
      you can find corresponding steps by searching on web (how to add javaagent to jira <product> <platform> <with or without service>
      once javaagent configured, do from step 6 above!

-----------------------------------------------------
Bellow is the official Detailed Instructions translated:

[Atlassian Agent v1.3.1]

Support (almost any version, include 8.0):
JIRA Software 
JIRA Core
JIRA Service Desk
JIRA plugin: Capture
JIRA plugin: Training
JIRA plugin: Portfolio
Confluence
Confluence plugin: Questions
Confluence plugin: Team Calendars
Bamboo 
Bitbucket 
FishEye 
Crowd 
Crucible 
Third party plugins

[Instructions for use]

Advantage
It supports almost all Atlassian products, and supports plug-ins (including third-party plug-ins in the plug-in market).
Support DataCenter mode.
Compared with the traditional crack, you can easily upgrade your service without having to crack it again.
Provide java-based command line keygen, which is more convenient to use in the terminal environment.
Open source projects, you know what you did when you cracked it.

Using help
You can try to execute java -jar atlassian-agent.jar see the help output.
The help here uses Atlassian's Confluence service as an example.

Configure Agent
1.Put it atlassian-agent.jarin a location that you won't delete randomly (all Atlassian services on your server can share the same one atlassian-agent.jar).
2.Set the environment variable JAVA_OPTS(this is actually the environment variable of Java, used to specify the -javaagentparameters attached when starting the java program), and attach the parameters. Specifically, you can do this:
	You can put: export JAVA_OPTS="-javaagent:/path/to/atlassian-agent.jar ${JAVA_OPTS}"such commands in .bashrcor .bash_profilesuch files.
	You can put: export JAVA_OPTS="-javaagent:/path/to/atlassian-agent.jar ${JAVA_OPTS}"such a command in bin目录the setenv.shor under the service installation setenv.bat（供windows使用）.
	You can also directly execute the command line: JAVA_OPTS="-javaagent:/path/to/atlassian-agent.jar" /path/to/start-confluence.shto start your service.
	Or you know other ways to modify environment variables, but if you have unrelated services on your machine, it is not recommended to modify global JAVA_OPTSenvironment variables.
	In short, you find a way to attach the -javaagentparameters to the java process to be started.
3.Please restart your Confluence service after the configuration is complete.
4.If you want to verify whether the configuration is successful, you can do this:
	Execute similar commands: ps aux|grep javafind the corresponding process to see if the -javaagentparameters are correctly attached.
	The software installation directory is similar /path/to/confluence/logs/catalina.out: ========= agent working =========the output of : should be found in the Tomcat log .

Use KeyGen
You have to confirm that the agent has been configured, refer to the above instructions.
When you try to execute java -jar /path/to/atlassian-agent.jarit, you should be able to see the output of KeyGen parameter help.
Please take a closer look at the function of each parameter, especially -pthe value range of the parameter. -pIt is best to wrap the parameter content in quotation marks, otherwise it may affect the parameter parsing.
The third-party plug-in takes it Application key/plugin key as a -pparameter. like:-p 'com.gliffy.integration.confluence'
When Atlassian service is installed, you should see AAAA-BBBB-CCCC-DDDDa server id similar to:, please pay attention.
Running KeyGen with correct parameters will output the calculated activation code on the terminal.
Copy the generated activation code to activate the service you want to use.
Give a chestnut:java -jar atlassian-agent.jar -p conf -m aaa@bbb.com -n my_name -o https://zhile.io -s ABCD-1234-EFGH-5678

Confluence FAQ
Points to note for activation of Confluence under Windows
Do not use start-service.bat to start (if you have to start this way, go to the registry to change the -javaagent parameter)
Start using bin\start-confluence.bat
Add -javaagent parameter in bin\setenv.bat
There is a bug in Confluence under Windows, which needs to be fixed by changing setenv.bat
set CATALINA_OPTS=-Xloggc:"%atlassian_logsdir%\gc-%atlassian_timestamp%.log" %CATALINA_OPTS%
//Change to
set CATALINA_OPTS=-Xloggc:"%atlassian_logsdir%\gc-%%t.log" %CATALINA_OPTS%
=================
www.downloadly.ir
cdi-alternative: Demostrates CDI Alternatives
======================================================
Author: Nevin Zhu
Level: Intermediate
Technologies: CDI, Servlet, JSP
Summary: Demonstrates the use of CDI Alternatives where the bean is selected during deployment 

What is it?
-----------

When more than one version of a bean is implemented for different purposes, the ability to switch between the versions during the development phase by injecting one qualifier or another is shown in this demo.

Instead of having to change the source code of the application, one can make the choice at deployment time by using alternatives.

Alternatives are commonly used for purposes like the following:

1)  To handle client-specific business logic that is determined at runtime
2)  To specify beans that are valid for a particular deployment scenario (for example, when country-specific sales tax laws require country-specific sales tax business logic)
3)  To create dummy (mock) versions of beans to be used for testing

To make a bean available for lookup, injection, or EL resolution using this mechanism, give it a javax.enterprise.inject.Alternative annotation and then use the alternative element to specify it in the beans.xml file.


System requirements
-------------------

All you need to build this project is Java 6.0 (Java SDK 1.6) or better, Maven 3.0 or better.

The application this project produces is designed to be run on JBoss Enterprise Application Platform 6 or JBoss AS 7. 

 
Configure Maven
---------------

If you have not yet done so, you must [Configure Maven](../README.md#mavenconfiguration) before testing the quickstarts.


Start JBoss Enterprise Application Platform 6 or JBoss AS 7
-------------------------

1. Open a command line and navigate to the root of the JBoss server directory.
2. The following shows the command line to start the server with the web profile:

        For Linux:   JBOSS_HOME/bin/standalone.sh
        For Windows: JBOSS_HOME\bin\standalone.bat


Build and Deploy the Quickstart
-------------------------

_NOTE: The following build command assumes you have configured your Maven user settings. If you have not, you must include Maven setting arguments on the command line. See [Build and Deploy the Quickstarts](../README.md#buildanddeploy) for complete instructions and additional options._

1. Make sure you have started the JBoss Server as described above.
2. Open a command line and navigate to the root directory of this quickstart.
3. Type this command to build and deploy the archive:

        mvn clean package jboss-as:deploy
        
4. This will deploy `target/ear/cdi-alternative.ear` to the running instance of the server.


Access the application
---------------------

The application will be running at the following URL <http://localhost:8080/cdi-alternative/Demo>.

A message will display for the bean being injected during run time. 

The alternative version of the beans can be updated in /WEB-INF/beans.xml by removing the <alternative> tag 

or 

change the class name to a different alternative. 

In this quickstart, in order to switch back to the default implementation, 
comment the <alternative> block. 

Undeploy the Archive
--------------------

1. Make sure you have started the JBoss Server as described above.
2. Open a command line and navigate to the root directory of this quickstart.
3. When you are finished testing, type this command to undeploy the archive:

        mvn jboss-as:undeploy


Run the Quickstart in JBoss Developer Studio or Eclipse
-------------------------------------
You can also start the server and deploy the quickstarts from Eclipse using JBoss tools. For more information, see [Use JBoss Developer Studio or Eclipse to Run the Quickstarts](../README.md#useeclipse) 

Debug the Application
------------------------------------

If you want to debug the source code or look at the Javadocs of any library in the project, run either of the following commands to pull them into your local repository. The IDE should then detect them.

    mvn dependency:sources
    mvn dependency:resolve -Dclassifier=javadoc

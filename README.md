# How to Set Up Real-Time SDK Java Application with Maven on the Eclipse IDE

- version: 1.0.0
- Last update: January 20222
- Environment: Windows, Linux
- Compiler: Java
- Prerequisite: [Demo prerequisite](#prerequisite)

## <a id="Introduction"></a>Introduction


[Refinitiv Real-Time SDK (Java Edition)](https://developers.refinitiv.com/en/api-catalog/refinitiv-real-time-opnsrc/rt-sdk-java) (RTSDK, formerly known as Elektron SDK) is a suite of modern and open source APIs that aim to simplify development through a strong focus on ease of use and standardized access to a broad set of Refinitiv proprietary content and services via the proprietary TCP connection named RSSL and proprietary binary message encoding format named OMM Message. The capabilities range from low latency/high-performance APIs right through to simple streaming Web APIs. 

The SDK has been mavenized to support [Apache Maven](https://maven.apache.org/) and [Gradle](https://gradle.org/) build automation tools since version 1.2. This supports helps Java developers to build the RTSDK Java application, manage its dependencies (Java Developers do not need to manually manage different versions of jar files anymore), and better collaboration in the team.

The [previous article](https://developers.refinitiv.com/en/article-catalog/article/how-to-set-up-refinitiv-real-time-sdk-java-application-with-mave) ([Medium](https://wasin-waeosri.medium.com/how-to-deploy-and-run-real-time-java-application-with-maven-in-docker-58e66dd1e247)) shows how to set up the EMA Java project with Maven via a command line. However, many Java developers are still using the [Eclipse IDE](https://www.eclipse.org/), which is the classic, multi-features, and tons of plugins.  This example project shows how to create the RTSDK - Java's Maven project with Eclipse. Developers do not need to run any commands manually via the command line. 

Disclaimer: I am using the [IntelliJ IDEA](https://www.jetbrains.com/idea/) and [Visual Studio Code](https://code.visualstudio.com/) as my main IDE/editor.

## <a id="prerequisite"></a>Prerequisite

To use the Eclipse IDE with Maven, you need the following software.

### Eclipse IDE

This example project is based on the Eclipse IDE for Java Developers version 2012-12 (4.22.0). You can download the installation package from [the Eclipse Foundation](https://www.eclipse.org/) website.

### Java SDK and Maven 

You need the [Oracle Java Development Kit](https://jdk.java.net/) or [Open JDK](https://openjdk.java.net/), and [Apache Maven](https://maven.apache.org/) in your machine. Please check the RTSDK - Java README file or [API Compatibility Matrix file](https://developers.refinitiv.com/en/api-catalog/refinitiv-real-time-opnsrc/rt-sdk-java/documentation) for more detail regarding the supported JDK versions.

This project is based on the Open JDK version "11" (2018-09-25) and Maven 3.6.3

### M2Eclipse

The [M2Eclipse](https://www.eclipse.org/m2e/) plugin provides integration for Apache Maven into the Eclipse IDE. Please check the [Installation section](https://github.com/eclipse-m2e/m2e-core/blob/master/README.md#-installation) on the project GitHub page regarding how to install the plugin. 

### Internet Access to Maven Central Repository

The Refinitiv Real-Time SDK Java is now available in [Maven Central Repository](https://search.maven.org/). You can define the following dependency in Maven's pom.xml file to let Maven automatically download the [EMA Java library](https://search.maven.org/artifact/com.refinitiv.ema/ema/) and [ETA Java library](https://search.maven.org/artifact/com.refinitiv.eta/eta) for the application.

![figure-1](images/01_ema_maven.png "EMA Java Dependencies")

![figure-2](images/02_eta_maven.png "ETA Java Dependencies")

Note: 
- This article is based on EMA Java version 3.6.4 L1 (RTSDK Java Edition 2.0.4 L1). 

## The Basic of RTSDK Java with Maven

This example project is focusing on setting the Eclipse IDE for the RTSDK Java project with Maven only. You can find the basic knowledge of how to use the RTSDK Java with Maven, Maven pom.xml setting for EMA Java, Standard Directory Layout, etc. from the [How to Set Up Refinitiv Real-Time SDK Java Application with Maven](https://developers.refinitiv.com/en/article-catalog/article/how-to-set-up-refinitiv-real-time-sdk-java-application-with-mave) article ([Medium](https://wasin-waeosri.medium.com/how-to-deploy-and-run-real-time-java-application-with-maven-in-docker-58e66dd1e247)).

## IDE Set Up

### Step 1: Creating a new workspace

Firstly, create a new workspace. I pick *C:\rtsdk_maven_eclipse* folder as my workspace location. The location and file name are based on your machine preference.

You can create a new workspace by setting the *C:\rtsdk_maven_eclipse* location in the Eclipse IDE launcher. 

![figure-3](images/04_eclipse_1.png "new workspace")

Then, a new workspace is created.

![figure-4](images/05_eclipse_2.png "new workspace")

### Step 2: Set Up Default Maven and JDK

The next step is setting up the default Maven and JDK runtime path in Eclipse. 

Let's open the IDE toolbar **Window -> Preferences** menu and choose **Maven --> Installation** option. Then add your local Maven installation path and tick the checkbox in front of it.

![figure-5](images/06_eclipse_3.png "Maven setup")

Note: You need to install the [M2E plugin](https://github.com/eclipse-m2e/m2e-core/blob/master/README.md#-installation) before this step.

Moving on to the JDK setting. In the **Window -> Preferences** menu, choose **Java --> Installed JREs** option. Add your local JDK 11 installation path and tick the checkbox in front of it.

![figure-6](images/07_eclipse_4.png "JDK setup")

Stay in the  Java setting, choose the **Compiler** option and set the **Compiler compliance level:** to **1.8**.

![figure-7](images/08_eclipse_5.png "JDK setup 2")

### Step 3: Create a new Maven Project

That brings us to the Maven Project creation with Eclipse. You can create a new Maven project with the **File --> New --> Other..." menu option

![figure-8](images/09_eclipse_6.png "New Eclipse Project")

Then select the **Maven Project** option and click Next.

![figure-9](images/10_eclipse_7.png "New Eclipse Project")

Choose the **Create a simple project (skip archetype selection)** option, and then click the next button.

![figure-10](images/11_eclipse_8.png "Create a simple Project")

Now it is time to set the basic Maven pom.xml properties. I set this example project with the following properties:
- Group Id: ```com.refinitiv.ema```
- Artifact Id: ```EMA_Java_204L1_Maven```
- Version: ```1.0.0-SNAPSHOT```
- Name: ```EMA_Java_204L1_Maven```

![figure-11](images/12_eclipse_9.png "Pom.xml basic set up")

Then click the Finish button, a new Maven project is newly created. 

![figure-12](images/13_eclipse_10.png "new project finish")

### Step 4: Set up the Project setting for RTSDK

Before we add the EMA Java code and configurations, there are some project-specific settings that we need to set them first.

Right-click on the project in the Package Explorer panel, and choose the **Properties** option.

![figure-13](images/14_eclipse_11.png "set Project properties")

**Uncheck** the **Enable project specific settings** option.

![figure-14](images/15_eclipse_12.png "set Project properties")

### Step 5: Set up Maven Pom.xml file

### Step 6: Add EMA Java Example Source Code to the Project

The EMA Java example source code is available at the **RTSDK Java package/Java/Ema/Example/src/main** folder. 

![figure-15](images/16_source_code_1.png "RTSDK Code 1")


You can copy an entire **main** folder to replace the **Workspace/EMA_Java_204L1_Maven/src/main** folder.

![figure-16](images/17_source_code_2.png "RTSDK Code 2")

Then, right-click on the project and choose the **Refresh** option to make the newly added codes to the project. 

![figure-17](images/18_source_code_3.png "RTSDK Code 3")

Now the *EMA_Java_204L1_Maven* project and Eclipse IDE are ready to run the RTSDK Java.


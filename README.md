# How to Set Up Real-Time SDK Java Application with Maven on the Eclipse ID

- version: 1.0.0
- Last update: January 20222
- Environment: Windows, Linux
- Compiler: Java
- Prerequisite: [Demo prerequisite](#prerequisite)

## <a id="Introduction"></a>Introduction


[Refinitiv Real-Time SDK (Java Edition)](https://developers.refinitiv.com/en/api-catalog/refinitiv-real-time-opnsrc/rt-sdk-java) (RTSDK, formerly known as Elektron SDK) is a suite of modern and open source APIs that aim to simplify development through a strong focus on ease of use and standardized access to a broad set of Refinitiv proprietary content and services via the proprietary TCP connection named RSSL and proprietary binary message encoding format named OMM Message. The capabilities range from low latency/high-performance APIs right through to simple streaming Web APIs. 

The SDK has been mavenized to support [Apache Maven](https://maven.apache.org/) and [Gradle](https://gradle.org/) build automation tools since version 1.2. This supported helps Java developers to build RTSDK Java application, manage its dependencies (Java Developers do not need to manual manage different versions of jar files anymore), and better collaboration in the team.

The [previous article](https://developers.refinitiv.com/en/article-catalog/article/how-to-set-up-refinitiv-real-time-sdk-java-application-with-mave) ([Medium](https://wasin-waeosri.medium.com/how-to-deploy-and-run-real-time-java-application-with-maven-in-docker-58e66dd1e247)) shows how to set up and the EMA Java project with Maven via a command line. However, many Java developers are still using with the [Eclipse IDE](https://www.eclipse.org/),which is the classic, multi-features, and tons of plugins. 

This example project shows how to create the RTSDK - Java's Maven project with Eclipse. Developer do not need to run any commands manually via command line. 
# SpringPractice
This repo uses an example for Maven to generate a simple Java project structure, and demonstrates how to retrieve Spring bean and prints a “hello world” string.
Maven + Spring hello world example
By mkyong | March 2, 2010 | Updated : November 7, 2012 | Viewed : 696,115 times +1,281 pv/w

This quick guide example uses Maven to generate a simple Java project structure, and demonstrates how to retrieve Spring bean and prints a “hello world” string.

Technologies used in this article :

Spring 2.5.6
Maven 3.0.3
Eclipse 3.6
JDK 1.6.0.13
Spring 3 example
For Spring 3, refer to this Maven + Spring 3 hello world example.
1. Generate project structure with Maven
In command prompt, issue following Maven command :

mvn archetype:generate -DgroupId=com.mkyong.common -DartifactId=SpringExamples
	-DarchetypeArtifactId=maven-archetype-quickstart -DinteractiveMode=false
Maven will generate all the Java’s standard folders structure for you (besides resources folder, which you need to create it manually)


 
2. Convert to Eclipse project
Type “mvn eclipse:eclipse” to convert the newly generated Maven style project to Eclipse’s style project.

mvn eclipse:eclipse
Later, import the converted project into Eclipse IDE.

Create a resources folder
Create a resources “/src/main/resources” folder, the Spring’s bean xml configuration file will put here later. Maven will treat all files under this “resources” folder as resources files, and copy it to output classes automatically.

 

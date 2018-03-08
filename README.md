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

 
3. Add Spring dependency
Add Spring dependency in Maven’s pom.xml file.

File : pom.xml

<project xmlns="http://maven.apache.org/POM/4.0.0"
	xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
	xsi:schemaLocation="http://maven.apache.org/POM/4.0.0
	http://maven.apache.org/maven-v4_0_0.xsd">
	<modelVersion>4.0.0</modelVersion>
	<groupId>com.mkyong.common</groupId>
	<artifactId>SpringExamples</artifactId>
	<packaging>jar</packaging>
	<version>1.0-SNAPSHOT</version>
	<name>SpringExamples</name>
	<url>http://maven.apache.org</url>
	<dependencies>

		<!-- Spring framework -->
		<dependency>
			<groupId>org.springframework</groupId>
			<artifactId>spring</artifactId>
			<version>2.5.6</version>
		</dependency>

	</dependencies>
</project>
Issue “mvn eclipse:eclipse” again, Maven will download the Spring dependency libraries automatically and put it into your Maven’s local repository. At the same time, Maven will add the downloaded libraries into Eclipse “.classpath” for dependency purpose.

4. Spring bean (Java class)
Create a normal Java class (HelloWorld.java) at “src/main/java/com/mkyong/common/HelloWorld.java”. Spring’s bean is just a normal Java class, and declare in Spring bean configuration file later.

package com.mkyong.common;

/**
 * Spring bean
 *
 */
public class HelloWorld {
	private String name;

	public void setName(String name) {
		this.name = name;
	}

	public void printHello() {
		System.out.println("Hello ! " + name);
	}
}
5. Spring bean configuration file
Create an xml file (Spring-Module.xml) at “src/main/resources/Spring-Module.xml“. This is the Spring’s bean configuration file, which declares all the available Spring beans.

File : Spring-Module.xml

<beans xmlns="http://www.springframework.org/schema/beans"
	xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
	xsi:schemaLocation="http://www.springframework.org/schema/beans
	http://www.springframework.org/schema/beans/spring-beans-2.5.xsd">

	<bean id="helloBean" class="com.mkyong.common.HelloWorld">
		<property name="name" value="Mkyong" />
	</bean>

</beans>
6. Review project structure
Review it and make sure the folder structure as follows

spring hello world example
7. Run It
Run App.java, it will load the Spring bean configuration file (Spring-Module.xml) and retrieve the Spring bean via getBean() method.

File : App.java

package com.mkyong.common;

import org.springframework.context.ApplicationContext;
import org.springframework.context.support.ClassPathXmlApplicationContext;

public class App {
	public static void main(String[] args) {
		ApplicationContext context = new ClassPathXmlApplicationContext(
				"Spring-Module.xml");

		HelloWorld obj = (HelloWorld) context.getBean("helloBean");
		obj.printHello();
	}
}
8. Output
Hello ! Mkyong
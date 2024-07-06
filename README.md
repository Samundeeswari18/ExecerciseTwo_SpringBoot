Guided Lab - 309.5.1 - SP3
How to use @Controller, @RequestMapping, and @GetMapping 

Lab Objective
In this lab, we will create a Spring Boot application and we will utilize some core Spring Boot annotations such as @controller, @RequestMapping, and @GetMapping.

Learner Objectives:
Perform an step-by-step exercise to build a basic application using Spring Boot, developing an application using the spring initializr.


Begin
1. Create the Spring Boot Project
To start our Spring Boot Application, let’s create a Spring Boot web application by using Spring Initializr as shown in the screenshot below.
Project: Maven Project is selected by default.
Language: Java is selected by default.
Spring Boot version: Select the latest release version (selected by default).
Project metadata: You can keep these as they are and add them as you like.
Packaging: of the project (i.e. either jar of war). 
Java version: Java 11 is selected by default. We will use  Java 11.



Add dependencies: Click on the Add dependencies button and a popup list of dependencies will appear. Add the following dependencies.
Spring Web WEB: Build Web, including RESTful, applications using Spring MVC. Uses Apache Tomcat as the default embedded container.
Spring Boot DevTools DEVELOPER TOOLS: Provides fast application restarts, LiveReload, and configurations for enhanced development experience.
Thymeleaf TEMPLATE ENGINES: A modern server-side Java template engine for both web and standalone environments. Allows HTML to be correctly displayed in browsers and as static prototypes.
Lombok DEVELOPER TOOLS: Java annotation library, which helps to reduce boilerplate code.







Generate Project - Click on the GENERATE button to download the zip file.

GENERATE button: When we click on the GENERATE button, it starts packing the project, and downloads the Jar or War file, which you have selected.


Copy that zip file into your IDE workspace and extract this zip file.
You will have a similar project structure as shown in the screenshot below.

Open the pom.xml file.This is how our pom.xml will look:
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
  xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 https://maven.apache.org/xsd/maven-4.0.0.xsd">
  <modelVersion>4.0.0</modelVersion>
  <parent>
     <groupId>org.springframework.boot</groupId>
     <artifactId>spring-boot-starter-parent</artifactId>
     <version>2.5.5</version>
     <relativePath/> <!-- lookup parent from repository -->
  </parent>
  <groupId>com.perscholas</groupId>
  <artifactId>ExecerciseOne_Rest</artifactId>
  <version>0.0.1-SNAPSHOT</version>
  <name>ExecerciseOne_Rest</name>
  <description>Demo project for Spring Boot</description>
  <properties>
     <java.version>11</java.version>
  </properties>
  <dependencies>
     <dependency>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-thymeleaf</artifactId>
     </dependency>
     <dependency>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-web</artifactId>
     </dependency>

     <dependency>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-devtools</artifactId>
        <scope>runtime</scope>
        <optional>true</optional>
     </dependency>
     <dependency>
        <groupId>org.projectlombok</groupId>
        <artifactId>lombok</artifactId>
        <optional>true</optional>
     </dependency>
     <dependency>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-test</artifactId>
        <scope>test</scope>
     </dependency>
  </dependencies>

  <build>
     <plugins>
        <plugin>
           <groupId>org.springframework.boot</groupId>
           <artifactId>spring-boot-maven-plugin</artifactId>
           <configuration>
              <excludes>
                 <exclude>
                    <groupId>org.projectlombok</groupId>
                    <artifactId>lombok</artifactId>
                 </exclude>
              </excludes>
           </configuration>
        </plugin>
     </plugins>
  </build>

</project>



<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
        xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 https://maven.apache.org/xsd/maven-4.0.0.xsd">
   <modelVersion>4.0.0</modelVersion>
   <parent>
       <groupId>org.springframework.boot</groupId>
       <artifactId>spring-boot-starter-parent</artifactId>
       <version>3.3.1</version>
       <relativePath/> <!-- lookup parent from repository -->
   </parent>
   <groupId>com.perscholas</groupId>
   <artifactId>Execercise_OneRest</artifactId>
   <version>0.0.1-SNAPSHOT</version>
   <name>Execercise_OneRest</name>
   <description>Execercise_OneRest</description>
   <url/>
   <licenses>
       <license/>
   </licenses>
   <developers>
       <developer/>
   </developers>
   <scm>
       <connection/>
       <developerConnection/>
       <tag/>
       <url/>
   </scm>
   <properties>
       <java.version>17</java.version>
   </properties>
   <dependencies>
       <dependency>
           <groupId>org.springframework.boot</groupId>
           <artifactId>spring-boot-starter-thymeleaf</artifactId>
       </dependency>
       <dependency>
           <groupId>org.springframework.boot</groupId>
           <artifactId>spring-boot-starter-web</artifactId>
       </dependency>


       <dependency>
           <groupId>org.springframework.boot</groupId>
           <artifactId>spring-boot-devtools</artifactId>
           <scope>runtime</scope>
           <optional>true</optional>
       </dependency>
       <dependency>
           <groupId>org.projectlombok</groupId>
           <artifactId>lombok</artifactId>
           <optional>true</optional>
       </dependency>
       <dependency>
           <groupId>org.springframework.boot</groupId>
           <artifactId>spring-boot-starter-test</artifactId>
           <scope>test</scope>
       </dependency>
   </dependencies>


   <build>
       <plugins>
           <plugin>
               <groupId>org.springframework.boot</groupId>
               <artifactId>spring-boot-maven-plugin</artifactId>
               <configuration>
                   <excludes>
                       <exclude>
                           <groupId>org.projectlombok</groupId>
                           <artifactId>lombok</artifactId>
                       </exclude>
                   </excludes>
               </configuration>
           </plugin>
       </plugins>
   </build>


</project>




2: Create Controller
A: Create a package named “TestController’ under “com.perscholas.”

B: Create a class named “MyController” under the above package as shown below.

Add the code below in MyController class.

First, mark the class with the @Controller annotation together with @RequestMapping and specify the path to /home.

import org.springframework.stereotype.Controller;
import org.springframework.web.bind.annotation.RequestMapping;
@Controller
@RequestMapping("home")
public class MyController {
   @RequestMapping({"/login"})   // either type '/' or index
   public String showlogin()
   {
       return "inboxpage";
   }
   @RequestMapping("/")
   public String simplemethod() {
       //mapped to hostname:port/home/
       return "inboxpage";
   }
   @RequestMapping("/index")
   public String showindex() {
       //mapped to hostname:port/home/index/
       return "inboxpage";
   }
}



package com.perscholas.execercise_onerest.TestCotroller;


import org.springframework.stereotype.Controller;
import org.springframework.web.bind.annotation.RequestMapping;
@Controller
@RequestMapping("home")
public class MyController {
   @RequestMapping({"/login"})   // either type '/' or index
   public String showlogin()
   {
       return "inboxpage";
   }
   @RequestMapping("/")
   public String simplemethod() {
       //mapped to hostname:port/home/
       return "inboxpage";
   }
   @RequestMapping("/index")
   public String showindex() {
       //mapped to hostname:port/home/index/
       return "inboxpage";
   }
}





The @SpringBootApplication annotation enables auto-configuration and component scanning.
The @Controller annotation extends the use-case of @Component and marks the annotated class as a business or presentation layer. When a request is made, this will inform the DispatcherServlet to include the controller class in scanning for methods mapped by the @RequestMapping annotation.
@RequestMapping annotation is applied at class level and the method level.
This showlogin() method will be invoked when we type http://localhost:8080/home/login and will return a String. 
3: Create View (HTML Page)
Create an HTML page named inboxpage.html file under src/main/resources/templates folder.


Add the below HTML code under <body>tag.
<h2>hello User welcome</h2>
<h1>Learning Spring Boot</h1>
<hr/>
<h2>Hello World,</h2>
<h2>This is my first Spring Boot web application</h2>



<!DOCTYPE html>
<html lang="en">
<head>
   <meta charset="UTF-8">
   <title>SpringBoot Application</title>
</head>
<body>
<h2>hello User welcome</h2>
<h1>Learning Spring Boot</h1>
<hr/>
<h2>Hello World,</h2>
<h2>This is my first Spring Boot web application</h2>


</body>
</html>




Restart the application and type the following URLs in your browser to access inboxpage.html 

http://localhost:8080/home/
http://localhost:8080/home/login
http://localhost:8080/home/index
You will see the screen below in your browser.







If you get an error message as shown below, open your main class (entry point) and replace @SpringBootApplication  with   @SpringBootApplication(scanBasePackages = {"com.perscholas"})

 Remember: Use your package name under scanBasePackages.







Example - Spring @GetMapping
@GetMapping is a specialized version of @RequestMapping annotation that acts as a shortcut for @RequestMapping(method = RequestMethod.GET).
@GetMapping annotated methods handle the HTTP GET requests matched with a given URL expression.
A: Create a new package named “controllerstwo” under  “com.perscholas.”
B: Create a class named “MyControllertwo” under the above package.
C: Add the following code in the above class.

@Controller
public class MyControllertwo{
   @GetMapping({ "login"})   // either type '/' or index
   public String showIndex()
   {
                  return "index";
   }
}

This time, we used the @GetMapping annotation rather than the @RequestMapping. When you type localhost:8080/login, showIndex() method will be invoked.


Create View (HTML Page)
Create an HTML page named index.html file under src/main/resources/templates folder.
Add below HTML code under <body> tag.


<h2>hello welcome</h2>
<h3> this is a Example of @GetMapping annotation  </h3>






Explanation


When you access a URL (localhost:8080/login) in the browser, a corresponding controller method mapped to the URL is invoked, which returns a String.


Spring will use this returned String, append .html, look for this file name in the configured template location (default or user-defined), and render the template matching it.


If the controller method returns "login,"  a template file with the name index.html must be present in the configured template location, and it will be displayed by the browser.




Summary
Spring Boot auto-configuration provides an intelligent mechanism to scan our application and provide a setup to run the application with minimal code. In our case, auto-configuration detects spring-boot-starter-web in our classpath, and will configure the embedded Tomcat and other configurations automatically for us.
The @SpringBootApplication annotation performs the following three operations for us:
@Configure
@EnableAutoConfiguration
@ComponentScan
In our case, the @SpringBootApplication annotation performs the following tasks for us:
Automatically detects our application type and will configure and set up the default configuration (e.g., setting up dispatcher servlet and scanning the component with the @Controller, and similar annotations).
Configures the embedded tomcat.
Enables the Spring MVC default setup.

The controller classes act as a request handler to allow Spring to recognize it as a RESTFUL service during runtime. The @Controller annotation indicates that the annotated class is a Web controller,

In this lab, we learned to create a Hello World Web application in Spring Boot with HTML.






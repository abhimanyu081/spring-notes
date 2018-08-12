## Q1.What is spring frameowork?
Java EE Framework
Core Conecpts are DI and AOP.
modules for specific tasks 
e.g spring jdbc, spring security , spring mvc etc.

## 2. What are some of the important features and advantages of Spring Framework?

Spring framwework is built on top of two principles.
* DI
* AOP

Some of the features of the spring are below.

* Lightweight and little overhead of using framework in our application.
* DI and IOC to write components that are independent of each other.
* support for various tasks such as Tx managment, JDBC operations, application security, File uploading, Exception handling with very little configuration overhead.

###  Advantages
* Decoupling different componenrs of the application, spring takes care to provide all required dependencies.
* Writing unit test cases is easy. Since components are loosly coupled , we can easily inject our mock bean to test the business logic.
* Reduces amount of boiler-plate code e.g JdbcTemplate
* Spring frameowrk divided into several modules that helps us make our application lightweight because we need to include only the required module. e.g if we dont need decurity we wont include spring-security module.
* Spring support most of the Java EE features.

## 3. What is dependency injection?


## 4. How constuctor based and setter based injection are different?
 if my application can’t work at all without the service class then I would prefer constructor based DI or else I would go for setter method based DI to use it only when it’s really needed.

 

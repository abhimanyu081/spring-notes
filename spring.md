## **@Component and Stereotype Annotations**
org.springframework.stereotype.@Component :- To mark a class that would be a bean
When we mark a java class as @Component Spring creates a bean of this class with name same as the class but starting with a lower case letter.

There are other stereotypical annotatioons like below


**@ComponentScan**

Configures which packages to scan for classes with annotation configuration
Arguments to this annotations.

* basePackages - packages to scan for classe
* basePackageClasses - point to classes in the base packages
* No Argument - If no argument is specified, the scanning happens from the same package where the @ComponentScan annotated class is present.

```
@ComponentScan(basePackages = "com.baeldung.annotations")

```
```
<context:component-scan base-package="com.baeldung" />

```

**@ComponentScans**

specify multiple @ComponentScan configurations

```
@ComponentScans({ 
  @ComponentScan(basePackages = "com.baeldung.annotations"), 
  @ComponentScan(basePackageClasses = VehicleFactoryConfig.class)
})

```

**@Component**

Mark the class to be a bean 
By default, the bean instances of this class have the same name as the class name with a lowercase initial.
we can specify a different name using the optional value argument of this annotation


**@Repository**
Define DAO classes or data objects as beans.
One advantage of using this annotation is that it has automatic persistence exception translation enabled.
When using a persistence framework such as Hibernate, native exceptions thrown within classes annotated with @Repository will be automatically translated into subclasses of Spring’s DataAccessExeption.
To enable exception translation, we need to declare our own PersistenceExceptionTranslationPostProcessor bean:

In most cases spring does this automatically.

```
@Bean
public PersistenceExceptionTranslationPostProcessor exceptionTranslation() {
    return new PersistenceExceptionTranslationPostProcessor();
}

<bean class="org.springframework.dao.annotation.PersistenceExceptionTranslationPostProcessor"/>

```

## @Service

Define service layer (business logic) beans.

## @Controller
Define controller beans


## @Configuration
Configuration classes can contain bean definition methods annotated with @Bean


**@Repository, @Service, @Configuration, and @Controller are all meta-annotations of @Component, they share the same bean naming behavior. Also, Spring automatically picks them up during the component scanning process
@Component is more generic but defineing one of the above annotations we give more specific info and role of the beans to the spring container.**

When we mark a class as @Component only one bean of that type can exist. -- check

These annotations are called stereotypes.
The concept of stereotypes is like this. When we write enterprise application in spring you would have
some standard spring beans that perform some standard roles. you would have a data object, a service class, a view , a controller. all these are stereiotypical roles some spring beans perform in any enterprise application.
So spring let us define one of thosse pertcular roles.


## Stereotype Annotations and AOP

When we use Spring stereotype annotations, it’s easy to create a pointcut that targets all classes that have a particular stereotype.

For example, suppose we want to measure the execution time of methods from the DAO layer. We’ll create the following aspect (using AspectJ annotations) taking advantage of @Repository stereotype

```
@Aspect
@Component
public class PerformanceAspect {
    @Pointcut("within(@org.springframework.stereotype.Repository *)")
    public void repositoryClassMethods() {};
 
    @Around("repositoryClassMethods()")
    public Object measureMethodExecutionTime(ProceedingJoinPoint joinPoint) 
      throws Throwable {
        long start = System.nanoTime();
        Object returnValue = joinPoint.proceed();
        long end = System.nanoTime();
        String methodName = joinPoint.getSignature().getName();
        System.out.println(
          "Execution of " + methodName + " took " + 
          TimeUnit.NANOSECONDS.toMillis(end - start) + " ms");
        return returnValue;
    }
}

```

In this example, we created a pointcut that matches all methods in classes annotated with @Repository. We used the @Around advice to then target that pointcut and determine the execution time of the intercepted methods calls.

Using this approach, we may add logging, performance management, audit, or other behaviors to each application layer.


## Advantages of these annotations
* clean code
* layered design
* seperation between concerns of an application
* smaller configuration


**What is the advantage of these annotations over @Component?**

**In how many ways we can define a bean in spring container?**





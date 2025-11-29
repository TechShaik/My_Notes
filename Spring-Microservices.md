**Introduction to Spring Framework**

The Spring Framework is a lightweight Java framework widely used for building scalable, maintainable enterprise applications. It offers a comprehensive programming and configuration model for Java-based development.



⭐ **Why Spring? (Key Features)**

Inversion of control

Dependency Injection

AOP

Transaction management

Spring MVC

Spring Security

Spring data

Spring Batch

Integration with other frameworks

----------------------------------------------------------------------------------------

**Spring Inversion of Control (IOC):**

Inversion of Control (IoC) is a Spring principle in which the framework takes over the responsibility of creating, configuring, and managing the lifecycle of objects (beans). This promotes loose coupling and makes the code more maintainable and testable.

🔧 How IoC Works?



IoC uses the following concepts:



✔ 1. Beans



Objects created by Spring.



✔ 2. IoC Container



The engine that creates \& manages beans

Examples:



ApplicationContext



BeanFactory



✔ 3. Dependency Injection (DI)



The technique IoC uses to supply dependencies automatically



**Dependency Injection:**



Dependency Injection (DI) is a technique used to achieve Inversion of Control.It is used to managae dependencies btwn objects in an application.

used to bring loose coupling btwn classes.

**Types of DI:**

**1.Constructor Injection:**

Spring injects the dependency through the constructor.



@Component

public class EmailService {

&nbsp;   public void sendEmail() {

&nbsp;       System.out.println("Email Sent!");

&nbsp;   }

}



@Component

public class UserService {



&nbsp;   private final EmailService emailService;



&nbsp;   @Autowired

&nbsp;   public UserService(EmailService emailService) {

&nbsp;       this.emailService = emailService;

&nbsp;   }



&nbsp;   public void processUser() {

&nbsp;       emailService.sendEmail();

&nbsp;   }

}

⭐ Why use Constructor Injection?



Best for immutability



Good for testing



Ensures dependency is always available



**2.Setter Injection:**

Spring injects dependency through a setter method.



@Component

public class PaymentService {

&nbsp;   public void processPayment() {

&nbsp;       System.out.println("Payment Processed!");

&nbsp;   }

}



@Component

public class OrderService {



&nbsp;   private PaymentService paymentService;



&nbsp;   @Autowired

&nbsp;   public void setPaymentService(PaymentService paymentService) {

&nbsp;       this.paymentService = paymentService;

&nbsp;   }



&nbsp;   public void placeOrder() {

&nbsp;       paymentService.processPayment();

&nbsp;   }

}



⭐ When to use Setter Injection?



When dependency is optional



When you want to allow modification after object creation



**3.Field Injection:**

Spring injects dependency directly into the field**.**



@Component

public class NotificationService {

&nbsp;   public void notifyUser() {

&nbsp;       System.out.println("User Notified!");

&nbsp;   }

}



@Component

public class AccountService {



&nbsp;   @Autowired

&nbsp;   private NotificationService notificationService;



&nbsp;   public void updateAccount() {

&nbsp;       notificationService.notifyUser();

&nbsp;   }

}

⚠ Why not recommended?



Hard to unit test



Violates immutability



Hidden dependencies



🎯 One-line Difference (Useful in Interviews)



📌 IoC is about giving control to Spring. DI is how Spring gives that control effect by injecting dependencies.



🌱 What is a Bean in Spring?



A Spring Bean is simply an object managed by the Spring IoC Container.



In normal Java, you create objects using new.

In Spring, objects are created, configured, and managed automatically by the Spring Container, and such objects are called Beans.



✅ @Component (Automatic Bean Creation)

✔ What it is:



@Component is a class-level annotation used for automatic (component-scan) based bean creation.



✔ When used:



Apply it on the class you want Spring to detect automatically.



✅ @Bean (Manual Bean Creation)

✔ What it is:



@Bean is a method-level annotation used to explicitly define a bean inside a @Configuration class.



✔ When used:



When you need full control over bean creation.



🎯 Interview One-Line Answers



@Service:

“A specialized @Component used to represent business logic.”



@Repository:

“A specialized @Component with additional database-exception translation for DAO layer.”



**🌟 What is @SpringBootApplication?**



@SpringBootApplication is a meta-annotation in Spring Boot that combines three important Spring annotations:



✔ 1. @SpringBootConfiguration



A specialized form of @Configuration



Tells Spring this class contains bean definitions



✔ 2. @EnableAutoConfiguration



Automatically configures Spring Boot based on the dependencies in your classpath



Example:



If you add Spring Web → auto-configures Tomcat



If you add Spring Data JPA → auto-configures Hibernate \& DataSource



✔ 3. @ComponentScan



Automatically scans the package and sub-packages for:



@Component



@Service



@Repository



@Controller



@RestController

And registers them as Spring Beans.

⭐ Interview Tip



If asked:

“What is @SpringBootApplication?”



Answer:



📌 It is a meta-annotation that enables auto-configuration, component scanning, and Spring Boot configuration, allowing the application to start with minimal setup.



🌱 Spring Bean Lifecycle

🌟 Simple Interview-Friendly Explanation



A Spring Bean goes through:



1️⃣ Creation → Spring creates the object

2️⃣ Dependency Injection → injects its dependencies

3️⃣ Initialization → initialized by init()(init method)

4️⃣ Ready to Use → bean is fully initialized

5️⃣ Destruction → on application shutdown, Spring calls destroy methods



**Spring Bean Scopes**



In Spring, bean scope defines how many instances of a bean are created and how long they live in the application context. By default, Spring creates only one instance of each bean, but the scope can be customized based on requirements.



Spring provides several scopes for different environments (Servlet-based application vs. standalone application).



1\. Singleton (Default Scope)



Definition:

Only one instance of the bean is created per Spring container. All requests for that bean return the same shared instance.



Use Case:

For stateless service classes, utility components, DAOs, repositories.



Example:



@Scope("singleton")

@Component

public class MyService {}



2\. Prototype



Definition:

A new bean instance is created every time the bean is requested from the container.



Use Case:

When the bean holds state or when you need a fresh object each time (e.g., objects being modified per request).



Example:



@Scope("prototype")

@Component

public class MyPrototypeBean {}



3\. Request Scope (Web Applications Only)



Definition:

A new bean instance is created for each HTTP request.

After the request completes, the bean is destroyed.



Use Case:

For request-specific data such as HTTP headers, request metadata, etc.



Example:



@Scope("request")

@Component

public class RequestBean {}



4\. Session Scope (Web Applications Only)



Definition:

One bean instance is created per HTTP session.

It remains alive until the user session ends.



Use Case:

Storing user-related session data.



Example:



@Scope("session")

@Component

public class SessionBean {}


# What is Dependency Injection (DI)?

Dependency Injection is a design pattern where the Spring container injects dependencies (objects) into a class instead of the class creating them itself. This improves flexibility, testability, and maintainability.

```java
//Without DI
public class Car {
    private Engine engine = new Engine(); // Hardcoded dependency

    public void start() {
        engine.run();
    }
}
```
> Problem: `Car` is tightly coupled to `Engine`, making it difficult to replace `Engine` with another implementation.


## Using DI
Spring Boot uses IoC containers (like ApplicationContext) to manage dependencies. It automatically injects objects where needed, removing the need to manually instantiate them.

1. **Field Injection**:
   Using @Component and @Autowired
    ```java
    import org.springframework.stereotype.Component;
    
    @Component  // Marks this as a Spring-managed bean
    public class Engine {
        public void run() {
        System.out.println("Engine started...");
        }
    }
    ```
    
    ```java
    import org.springframework.beans.factory.annotation.Autowired;
    import org.springframework.stereotype.Component;
    
    @Component
    public class Car {
        @Autowired  // Injects Engine bean automatically
        private Engine engine;
    
        public void start() {
            engine.run();
        }
    }
    
    ```
   
2. Constructor Injection
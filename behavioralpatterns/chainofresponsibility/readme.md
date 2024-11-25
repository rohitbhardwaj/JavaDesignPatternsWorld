Behavioral Design Patterns: Chain of Responsibility Pattern
Objective
The Chain of Responsibility Pattern is a behavioral design pattern that allows a request to pass through a chain of handlers. Each handler determines whether to process the request or pass it to the next handler in the chain. This pattern promotes loose coupling between senders and receivers of requests.

What is the Chain of Responsibility Design Pattern?
It decouples the sender and receiver, letting the request pass through a sequence of handlers until one of them processes it.
Commonly used for logging systems, event handling, and access control.
Key Characteristics
Loose Coupling:

The sender doesn't need to know which object will handle the request. Similarly, handlers don't need to know the source of the request.
Dynamic Chain:

Handlers can be added, removed, or reordered at runtime without affecting the client.
Single Responsibility Principle:

Each handler is responsible for either processing the request or passing it along.
Sequential Order:

Requests are processed in the order they move through the chain.
When to Use Chain of Responsibility Pattern
Multiple Handlers for a Request:

When a request might be processed by different objects, but only one should handle it.
Dynamic Processing Logic:

When the order or composition of handlers needs to be adjusted at runtime.
Logging Systems:

For different levels of logging (DEBUG, INFO, WARN, ERROR).
Access Control:

To verify permissions or roles in a step-by-step manner.
Implementation
Use Case:
A logging system with levels (DEBUG, INFO, ERROR). Each level processes messages it is responsible for, passing unhandled messages to the next level in the chain.

1. Handler Interface
Define a common interface for all handlers:

java
Copy code
/**
 * Handler interface defining the contract for processing requests.
 */
public interface Logger {
    void log(String message, LogLevel level);
}
2. LogLevel Enum
Define an enumeration for logging levels:

java
Copy code
/**
 * Enum representing logging levels.
 */
public enum LogLevel {
    DEBUG, INFO, ERROR
}
3. Abstract Handler
Create an abstract class to manage the chain of handlers:

java
Copy code
/**
 * Abstract logger that defines the chain mechanism.
 */
public abstract class AbstractLogger implements Logger {
    protected AbstractLogger nextLogger; // Next logger in the chain

    public void setNextLogger(AbstractLogger nextLogger) {
        this.nextLogger = nextLogger;
    }

    protected abstract void write(String message); // Abstract method to write the log

    @Override
    public void log(String message, LogLevel level) {
        if (canHandle(level)) {
            write(message);
        } else if (nextLogger != null) {
            nextLogger.log(message, level);
        }
    }

    protected abstract boolean canHandle(LogLevel level); // Determines if the logger can handle the level
}
4. Concrete Handlers
Implement specific loggers for each level:

DEBUG Logger:

java
Copy code
public class DebugLogger extends AbstractLogger {
    @Override
    protected void write(String message) {
        System.out.println("DEBUG: " + message);
    }

    @Override
    protected boolean canHandle(LogLevel level) {
        return level == LogLevel.DEBUG;
    }
}
INFO Logger:

java
Copy code
public class InfoLogger extends AbstractLogger {
    @Override
    protected void write(String message) {
        System.out.println("INFO: " + message);
    }

    @Override
    protected boolean canHandle(LogLevel level) {
        return level == LogLevel.INFO;
    }
}
ERROR Logger:

java
Copy code
public class ErrorLogger extends AbstractLogger {
    @Override
    protected void write(String message) {
        System.out.println("ERROR: " + message);
    }

    @Override
    protected boolean canHandle(LogLevel level) {
        return level == LogLevel.ERROR;
    }
}
5. Client
Set up the chain of responsibility and log messages:

java
Copy code
public class Main {
    public static void main(String[] args) {
        // Create loggers
        AbstractLogger debugLogger = new DebugLogger();
        AbstractLogger infoLogger = new InfoLogger();
        AbstractLogger errorLogger = new ErrorLogger();

        // Set up the chain
        debugLogger.setNextLogger(infoLogger);
        infoLogger.setNextLogger(errorLogger);

        // Log messages
        debugLogger.log("This is a debug message", LogLevel.DEBUG);
        debugLogger.log("This is an info message", LogLevel.INFO);
        debugLogger.log("This is an error message", LogLevel.ERROR);
    }
}
Output
plaintext
Copy code
DEBUG: This is a debug message
INFO: This is an info message
ERROR: This is an error message
Benefits of Chain of Responsibility Pattern
Loose Coupling:

Decouples the sender and receiver, simplifying the code.
Dynamic Configuration:

The chain can be adjusted at runtime, allowing flexibility.
Responsibility Distribution:

Each handler focuses on a specific type of request.
Fallback Mechanism:

Ensures requests are either handled or passed along the chain.
Challenges
Missed Handling:

If the chain is not configured properly, some requests might go unhandled.
Performance Overhead:

A long chain can introduce performance issues due to multiple checks.
Debugging Complexity:

It can be difficult to trace the flow of a request through a long chain.
When Not to Use Chain of Responsibility
Simple Request Handling:

If there’s only one handler, a chain is unnecessary.
Fixed Responsibility:

If the handling logic is static and doesn’t need runtime flexibility.
Performance-Critical Systems:

Avoid for performance-sensitive systems where chain traversal adds overhead.
Real-World Applications
Logging Frameworks:

Systems like SLF4J or Log4j use a chain of responsibility to process log messages at different levels.
UI Event Handling:

Events like mouse clicks or key presses can be passed through a chain of listeners.
Access Control:

Security systems check user roles, permissions, and authentication sequentially.
Key Takeaways
The Chain of Responsibility Pattern provides a flexible way to delegate request handling.
It simplifies sender-receiver interactions and promotes loose coupling.
Use this pattern when requests might need to pass through multiple potential handlers.
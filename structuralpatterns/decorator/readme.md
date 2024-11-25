Structural Design Patterns: Decorator Pattern
Objective
The Decorator Design Pattern enhances the functionality of individual objects dynamically without modifying their code or affecting other objects. It is particularly useful when you need to add or combine behaviors at runtime while adhering to the Open/Closed Principle.

What is the Decorator Pattern?
The Decorator Pattern is a structural design pattern that allows you to dynamically extend the behavior of objects. It involves wrapping objects with decorator classes that add new functionality without altering the object's original implementation.

Key Characteristics
Dynamic Behavior:

Add functionalities to objects at runtime.
Open/Closed Principle:

New decorators can be introduced without modifying existing code.
Composition Over Inheritance:

Promotes reuse by avoiding the need to create multiple subclasses for different combinations of behaviors.
Real-World Analogy
Adding Toppings to Ice Cream:

The base ice cream represents the core object.
Toppings like chocolate, nuts, and sprinkles are decorators that add new features to the ice cream dynamically.
Implementation
Use Case:
Enhancing UI components dynamically by adding features like borders, shadows, or scrollbars to a TextView.

1. Component Interface
Define the base interface for UI components:
2. Concrete Component
Create a concrete implementation of the UIComponent:

3. Base Decorator
Create an abstract decorator that implements the UIComponent interface and contains a reference to the wrapped component:

4. Concrete Decorators
Implement specific decorators to add new functionalities:
Border Decorator:
Shadow Decorator:
5. Client
The client dynamically decorates the TextView with various features:

Output
plaintext
Copy code
Rendering basic TextView:
Rendering TextView.

Rendering TextView with Border:
Rendering TextView.
Adding border to the component.

Rendering TextView with Border and Shadow:
Rendering TextView.
Adding border to the component.
Adding shadow to the component.

Benefits of Decorator Pattern
Flexibility:

Dynamically add or remove functionalities at runtime without modifying the original object.
Open/Closed Principle:

Existing components are not modified; new decorators can be added independently.
Combining Behaviors:

Multiple decorators can be stacked to combine features.
Avoids Subclass Explosion:

Eliminates the need for creating multiple subclasses for every possible combination of behaviors.
Challenges
Complexity:

Decorator chains can become difficult to debug due to layered wrapping.
Overhead:

Multiple decorators increase the number of objects in memory.
When to Use Decorator Pattern
Dynamic Behavior Addition:

When you need to add functionality to objects at runtime.
Avoid Inheritance:

When subclassing leads to too many combinations of classes.
Reusable Features:

When you need features that can be reused across different objects.
Real-World Examples
Graphical User Interfaces (GUIs):

Adding scrollbars, borders, or shadows to components dynamically.
Text Formatting:

Applying bold, italic, or underline styles to text dynamically.
Data Streams:

Wrapping input/output streams with functionalities like buffering or encryption (e.g., Java’s BufferedInputStream).
Key Takeaways
The Decorator Pattern is ideal for enhancing object functionality dynamically.
It promotes modularity, reusability, and flexibility by composing behaviors at runtime.
While powerful, it can lead to complexity when dealing with extensive decorator chains.


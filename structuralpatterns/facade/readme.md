Structural Design Patterns: Facade Pattern
Objective
The Facade Design Pattern simplifies interaction with a complex subsystem by providing a unified and simplified interface. It allows clients to interact with a system without dealing with the underlying complexities, promoting subsystem independence and portability.

What is the Facade Pattern?
The Facade Pattern is a structural design pattern that provides a simplified interface to a complex system of classes, libraries, or subsystems. It decouples clients from intricate subsystem implementations, improving code maintainability and usability.

Real-World Analogy
House Facade:

From the outside, you interact with a house via its main entrance (the facade).
Internally, the house has plumbing, electrical wiring, and HVAC systems. The facade simplifies the interaction by hiding these complexities.
When to Use Facade Pattern
Simplified Subsystem Interaction:

When a subsystem is complex and clients need an easy-to-use interface.
Decouple Clients from Subsystems:

When subsystems are tightly coupled, the facade provides a single entry point, reducing dependencies.
Portability and Independence:

Promotes independence and makes subsystems easier to replace or evolve.
Implementation
Use Case:
A Home Theater System has multiple components (DVD Player, Projector, Sound System, Lights). The Facade Pattern provides a unified interface to control the system.

1. Subsystem Components
Define the individual components of the system:

Projector

Sound System

Lights
2. Facade Class
3. Client
The client interacts only with the HomeTheaterFacade:


Benefits of Facade Pattern
Simplified Subsystem Access:

Provides an easy-to-use interface for complex subsystems.
Reduces Dependencies:

Decouples clients from intricate subsystem details.
Improved Maintainability:

Changes to the subsystem don’t impact the client, as they interact only with the facade.
Promotes Modularity:

Subsystems can evolve independently, simplifying upgrades or replacements.


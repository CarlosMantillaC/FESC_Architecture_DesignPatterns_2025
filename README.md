# FESC_MVC_DesignPatterns_2025

## 📌 Overview
This repository contains an educational project demonstrating the implementation of **Model-View-Controller (MVC) architecture** combined with several **software design patterns**.  
It is based on the executive document prepared for the FESC course in August 2025.

The project includes:
- Explanation of **software architecture** and its purpose.
- Example implementation of **MVC architecture**.
- Research and code samples for **22 GoF design patterns**.

---

## 🎯 Objectives
- Understand the **role of software architecture** in system design.
- Apply **MVC architecture** to separate concerns between data, logic, and presentation.
- Explore **design patterns** as reusable solutions to recurring problems.
- Provide clear, maintainable, and scalable example code.

---

## 🏗 Architecture Selected: MVC
The **Model-View-Controller** architecture divides the system into three main components:

1. **Model**  
   - Manages data, business logic, and rules.
   - Independent from UI elements.
   
2. **View**  
   - Handles user interface and presentation.
   - Receives data from the Controller and displays it.

3. **Controller**  
   - Receives user input.
   - Communicates between Model and View.
   - Updates the View based on Model changes.

**Benefits of MVC:**
- Clear separation of concerns.
- Easier maintainability and testing.
- Independent development of UI and business logic.

---

## 📚 Design Patterns Implemented
The repository includes documentation and code examples for the **23 GoF design patterns**, grouped into:

### 1. Creational Patterns
- Singleton
- Factory Method
- Abstract Factory
- Builder
- Prototype

### 2. Structural Patterns
- Adapter
- Bridge
- Composite
- Decorator
- Facade
- Flyweight
- Proxy

### 3. Behavioral Patterns
- Chain of Responsibility
- Command
- Interpreter
- Iterator
- Mediator
- Memento
- Observer
- State
- Strategy
- Template Method
- Visitor

---

## 💻 Example Project: Task Management App
A **simple MVC-based Task Management application** was developed to demonstrate:
- MVC architecture in action.
- Usage of **Observer pattern** for real-time UI updates.
- Usage of **Factory Method** for creating different types of tasks.

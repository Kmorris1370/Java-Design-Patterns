# Java Design Patterns

Implementation of classic Gang of Four design patterns with practical examples and UML diagrams.

![Java](https://img.shields.io/badge/Java-ED8B00?style=flat-square&logo=java&logoColor=white)
![Design Patterns](https://img.shields.io/badge/Design%20Patterns-OOP-success?style=flat-square)

## 📚 Patterns Implemented

### 1. Observer Pattern (Behavioral)
A messaging system demonstrating the one-to-many dependency pattern where observers automatically receive updates from a subject.

**Use Case:** Subject sends messages to multiple observers  
**Key Benefit:** Loose coupling between sender and receivers

[📖 Read More](observer-pattern/README.md) | [💻 View Code](observer-pattern/src/)

---

### 2. Bridge Pattern (Structural)
A graphics system showing separation between abstraction (shapes) and implementation (drawing methods).

**Use Case:** Drawing shapes with different color renderers  
**Key Benefit:** Decouple abstraction from implementation

[📖 Read More](bridge-pattern/README.md) | [💻 View Code](bridge-pattern/src/)

---

## 🚀 Quick Start

### Prerequisites
- Java JDK 8 or higher

### Running Observer Pattern
```bash
cd observer-pattern/src
javac observerpattern/*.java
java observerpattern.ObserverPattern
```

### Running Bridge Pattern
```bash
cd bridge-pattern/src
javac bridgepattern/*.java
java bridgepattern.BridgePattern
```

## 📖 What I Learned

- **SOLID Principles** - Single Responsibility, Open/Closed, Dependency Inversion
- **Loose Coupling** - Reducing dependencies between components
- **Composition over Inheritance** - Using interfaces and composition for flexibility
- **Design Trade-offs** - Understanding when to apply specific patterns

## 🎯 Pattern Selection Guide

| Pattern | When to Use | Avoid When |
|---------|-------------|------------|
| Observer | One-to-many updates, event systems | Tight coupling needed, simple callbacks sufficient |
| Bridge | Multiple dimensions of variation | Single dimension, simple inheritance works |

## 📚 Resources

- [Refactoring Guru - Design Patterns](https://refactoring.guru/design-patterns)
- "Design Patterns" - Gang of Four
- "Head First Design Patterns" - Freeman & Freeman

## 📝 License

MIT License - See [LICENSE](LICENSE) file for details

# Bridge Pattern - Shape Drawing System

A practical implementation of the Bridge structural pattern using a graphics rendering system with shapes and colors.

## Pattern Overview

The Bridge pattern separates an abstraction (Shape) from its implementation (DrawAPI) so that both can vary independently.

## The Problem Without Bridge

Without the pattern, you'd need:
- RedCircle, GreenCircle, RedRectangle, GreenRectangle (4 classes)
- Adding Blue color: +2 classes (6 total)
- Adding Triangle: +3 classes (9 total)
- **Exponential growth** 😱

## The Solution With Bridge

With the pattern:
- 2 Shapes (Circle, Rectangle)
- 2 Colors (RedDraw, GreenDraw)
- Total: 4 classes
- Adding Blue: +1 class (5 total)
- Adding Triangle: +1 class (6 total)
- **Linear growth** ✅

## Class Diagram

## Code Structure

### Abstraction Layer (Shape)
```java
public abstract class Shape {
    protected DrawAPI drawAPI;  // Bridge to implementation
    
    protected Shape(DrawAPI drawAPI) {
        this.drawAPI = drawAPI;
    }
    
    public abstract void draw();
}
```

### Refined Abstraction (Circle, Rectangle)
```java
public class Circle extends Shape {
    private int x, y, radius;
    
    public void draw() {
        drawAPI.drawCircle(radius, x, y);  // Delegates to implementation
    }
}
```

### Implementation Layer (DrawAPI)
```java
public interface DrawAPI {
    void drawCircle(int radius, int x, int y);
    void drawRectangle(int x, int y);
}
```

### Concrete Implementations (RedDraw, GreenDraw)
```java
public class RedDraw implements DrawAPI {
    public void drawCircle(int radius, int x, int y) {
        System.out.println("Drawing Circle[ color: red, radius: " + 
                          radius + ", x: " + x + ", y: " + y + "]");
    }
}
```

## Running the Demo
```bash
# Compile
javac bridgepattern/*.java

# Run
java bridgepattern.BridgePattern
```

## How It Works
```java
// Create objects by combining abstraction + implementation
Shape redCircle = new Circle(100, 100, 10, new RedDraw());
Shape greenCircle = new Circle(100, 100, 10, new GreenDraw());

// Draw using the bridged combination
redCircle.draw();    // Circle uses RedDraw implementation
greenCircle.draw();  // Circle uses GreenDraw implementation
```

## Real-World Applications

- ✅ **GUI Frameworks** - Abstract widgets with platform-specific rendering
- ✅ **Database Drivers** - JDBC API with different database implementations
- ✅ **Graphics Systems** - Shapes with vector/raster/3D renderers
- ✅ **Remote Services** - Abstract service with local/remote implementation
- ✅ **Logging** - Logger interface with file/console/network output

## Pattern Benefits

✅ **Separation of Concerns** - Abstraction and implementation independent  
✅ **Platform Independence** - Same interface, different implementations  
✅ **Extensibility** - Add shapes or colors without modifying existing code  
✅ **Runtime Binding** - Choose implementation at runtime

## Pattern Drawbacks

⚠️ **Complexity** - More classes and indirection  
⚠️ **Overhead** - Extra layer may impact performance slightly  
⚠️ **Overkill** - Too complex for simple scenarios

## Extending This Example

### Add a Blue Color
```java
public class BlueDraw implements DrawAPI {
    public void drawCircle(int radius, int x, int y) {
        System.out.println("Drawing Circle[ color: blue, ...]");
    }
    // ... implement drawRectangle
}

// Use it
Shape blueCircle = new Circle(50, 50, 5, new BlueDraw());
```

### Add a Triangle Shape
```java
public class Triangle extends Shape {
    private int x1, y1, x2, y2, x3, y3;
    
    public void draw() {
        // Would need to add drawTriangle to DrawAPI interface
        drawAPI.drawTriangle(x1, y1, x2, y2, x3, y3);
    }
}
```

## Bridge vs Adapter

| Bridge | Adapter |
|--------|---------|
| Designed upfront | Retrofitted to existing code |
| Both sides designed together | Makes incompatible interfaces work |
| Prevents class explosion | Wraps single incompatible class |

## What I Learned

- Favoring composition over inheritance
- Designing for extensibility from the start
- Managing complexity through proper separation
- When abstraction and implementation should vary independently
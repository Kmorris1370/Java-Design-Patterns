# Observer Pattern - Message Broadcasting System

A practical implementation of the Observer behavioral pattern using a message broadcasting system.

## Pattern Overview

The Observer pattern establishes a one-to-many dependency where when one object (Subject) changes state, all dependent objects (Observers) are notified automatically.

## Class Diagram
┌─────────────┐
     │   Subject   │
     ├─────────────┤
     │ -observers  │
     ├─────────────┤
     │ +attach()   │
     │ +notify()   │
     │ +sendMsg()  │
     └──────┬──────┘
            │
            │ notifies
            ▼
     ┌──────────────┐
     │ObserverClass │◄─────┐
     ├──────────────┤      │
     │ +update()    │      │
     └──────┬───────┘      │
            │              │
            │ extends      │
            ▼              │
     ┌──────────────┐      │
     │   Observer   │──────┘
     ├──────────────┤   observes
     │ -name        │
     │ +update()    │
     └──────────────┘

     ## How It Works

1. **Subject** maintains a list of observers
2. **Observers** register (attach) themselves to the subject
3. When subject sends a message, it **notifies all observers**
4. Each observer receives and processes the message

## Code Structure

### Subject.java
Manages the list of observers and broadcasts messages:
```java
public void attach(ObserverClass observer) {
    observers.add(observer);
}

public void sendMessage(String message) {
    System.out.println("\nSubject sending: " + message);
    notifyObservers(message);
}
```

### Observer.java
Receives and displays messages:
```java
public void update(String message) {
    System.out.println(name + " received " + message);
}
```

## Running the Demo
```bash
# Compile
javac observerpattern/*.java

# Run
java observerpattern.ObserverPattern
```

## Real-World Applications

- ✅ Event handling systems (GUI buttons, listeners)
- ✅ Newsletter/notification systems
- ✅ Social media feed updates
- ✅ Stock market tickers
- ✅ MVC architecture (Model notifies Views)

## Pattern Benefits

✅ **Loose Coupling** - Subject doesn't need to know observer details  
✅ **Dynamic Relationships** - Add/remove observers at runtime  
✅ **Broadcast Communication** - One action updates many objects  
✅ **Open/Closed Principle** - Add observers without modifying subject

## Pattern Drawbacks

⚠️ **Memory Leaks** - Observers must be properly detached  
⚠️ **Unpredictable Order** - No guarantee of notification sequence  
⚠️ **Update Cascades** - Can trigger complex chains of updates  
⚠️ **Performance** - Many observers = slower notifications

## Enhancements You Could Add

- [ ] Add `detach()` method to unsubscribe observers
- [ ] Priority-based notification ordering
- [ ] Conditional updates (observers filter messages)
- [ ] Asynchronous notifications using threads
- [ ] Observer categories/topics for selective updates

## Related Patterns

- **Mediator** - Centralized vs distributed communication
- **Publish-Subscribe** - Extended observer with message filtering
- **Event Listener** - Specialized observer for GUI events
# Architectural Smells

Arcan bases the estimate of Technical Debt on the detection of Architectural Smells, software design decisions that negatively impact the software quality. Smells violates design principles.

At the moment, Arcan detects four types of Architectural Smells:

- Cyclic Dependency
- God Component
- Hub-Like Dependency
- Unstable Dependency

## Cyclic Dependency

When two or more architectural components are involved in a chain of relationships. 

### Drawbacks
The architectural components involved in a Cyclic Dependency are:

- hard to release
- hard to maintain
- hard to reuse in isolation

The smell violates the [Acyclic Dependencies Principle](https://devlead.io/DevTips/AcyclicDependenciesPrinciple) defined by [R. C. Martin](https://www.amazon.it/Software-Development-Principles-Patterns-Practices/dp/0132760584).


![CD](https://www.arcan.tech/wp-content/uploads/2023/01/cycle_1.jpg)


## God Component

this smell occurs when an architectural component is excessively large in terms of LOC (Lines Of Code). 

### Drawbacks

The architectural component affected by God Component:

- centralizes logic
- has low cohesion within
- has increasing complexity

The smell violates the [Modularity Principle](http://www.cs.sjsu.edu/~pearce/modules/lectures/ood/principles/Modularity.htm) defined by [R. C. Martin](https://www.amazon.it/Software-Development-Principles-Patterns-Practices/dp/0132760584).


![GC](https://www.arcan.tech/wp-content/uploads/2023/01/god.jpg)

## Hub-Like Dependency

When an architectural component has (outgoing and ingoing) dependencies with a large number of other components. The component affected by HL ,  and . 

### Drawbacks
The component affected by the smell:

- centralizes logic
- is a unique point of failure
- favors change ripple effects

The smell violates the [Modularity Principle](http://www.cs.sjsu.edu/~pearce/modules/lectures/ood/principles/Modularity.htm) defined by [R. C. Martin](https://www.amazon.it/Software-Development-Principles-Patterns-Practices/dp/0132760584).


![HL](https://www.arcan.tech/wp-content/uploads/2023/01/hub.jpg)

## Unstable Dependency

describes an architectural component that depends on other components that are less stable than itself. [Instability](https://codinghelmet.com/articles/how-to-use-module-coupling-and-instability-metrics-to-guide-refactoring) (proneness to change) is measured using [R. C. Martin](https://www.amazon.it/Software-Development-Principles-Patterns-Practices/dp/0132760584)’s formula.

### Drawbacks

The component affected by the smell can:

- favors change ripple effects
- be subjected to frequent changes

The smell violates the [Stable Dependency Principle](https://devlead.io/DevTips/StableDependenciesPrinciple) defined by [R. C. Martin](https://www.amazon.it/Software-Development-Principles-Patterns-Practices/dp/0132760584).

![UD](https://www.arcan.tech/wp-content/uploads/2023/01/unstable.jpg)
# Architectural Smells and refactoring

Arcan bases the estimate of Technical Debt on the detection of Architectural Smells, software design decisions that negatively impact the software quality. Smells violates design principles.

At the moment, Arcan detects four types of Architectural Smells:
- Cyclic Dependency
- God Component
- Hub-Like Dependency
- Unstable Dependency

## Cyclic Dependency

When two or more architectural components are involved in a chain of relationships. The parts of code affected by CD are hard to release, to maintain and to reuse in isolation.

![CD](https://www.arcan.tech/wp-content/uploads/2023/01/cycle_1.jpg)


## God Component

this smell occurs when an architectural component is excessively large in terms of LOC (Lines Of Code). God components centralize logic and are a sign of low cohesion within the affected component, increasing complexity. 

![GC](https://www.arcan.tech/wp-content/uploads/2023/01/god.jpg)

## Hub-Like Dependency

When an architectural component has (outgoing and ingoing) dependencies with a large number of other components. The component affected by HL centralizes logic, is a unique point of failure and favors change ripple effects. 

![HL](https://www.arcan.tech/wp-content/uploads/2023/01/hub.jpg)

## Unstable Dependency

describes an architectural component that depends on other components that are less stable than itself. This can cause a ripple effect of changes in the system. Instability (proneness to change) is measured using R.C. Martin’s formula

![UD](https://www.arcan.tech/wp-content/uploads/2023/01/unstable.jpg)
# Architectural Smells

Arcan bases the estimate of Technical Debt on the detection of Architectural Smells, software design decisions that negatively impact the software quality. Smells violates design principles.

At the moment, Arcan detects four types of Architectural Smells:

- [Cyclic Dependency](architectural_smells.md#cyclic-dependency)
- [God Component](architectural_smells.md#god-component)
- [Hub-Like Dependency](architectural_smells.md#hub-like-dependency)
- [Unstable Dependency](architectural_smells.md#unstable-dependency)

## Cyclic Dependency

When two or more architectural components are involved in a chain of relationships. 

### Drawbacks
The architectural components involved in a Cyclic Dependency are:

- hard to release
- hard to maintain
- hard to reuse in isolation

The smell violates the [Acyclic Dependencies Principle](https://devlead.io/DevTips/AcyclicDependenciesPrinciple) defined by [R. C. Martin](https://www.amazon.it/Software-Development-Principles-Patterns-Practices/dp/0132760584).

### Detection strategy

The detection of Cyclic Dependency (CD) in Arcan is done using the [dependency graph](glossary.md#dependency-graph) of the system that we are analysing, i.e., the graph representation of the system's architectural components and dependencies.

CD is detected on both [units](glossary.md#unit) and [containers](glossary.md#container) (e.g., classes and packages in Java). A cycle is detected whenever two or more architectural components depend upon each other in a cycle. Arcan detects CD on different types of components and uses well-known cycle detection algorithm to identify components that belong to the same cycles. The algorithms supported by Arcan are:

- **Sedgewick-Wayne** algorithm, a simple DFS-based algorithm to detect cycles. More information [here](https://sedgewick.io/books/algorithms/). This is the default implementation used by Arcan. 
- **Tarjan's strongly connected components** (SCC) algorithm. You can find more [here](https://epubs.siam.org/doi/10.1137/0201010)
- **Laval-Falleri's shortest cycles** algorithm. You can find more [here](https://link.springer.com/chapter/10.1007/978-3-642-21952-8_19). This is the default implementation used by Arcan for Layered Cyclic Dependencies.



![CD](https://www.arcan.tech/wp-content/uploads/2023/01/cycle_1.jpg)


## God Component

This smell occurs when an architectural component is excessively large in terms of LOC (Lines Of Code). 

### Drawbacks

The architectural component affected by God Component:

- centralizes logic
- has low cohesion within
- has increasing complexity

The smell violates the [Modularity Principle](http://www.cs.sjsu.edu/~pearce/modules/lectures/ood/principles/Modularity.htm) defined by [R. C. Martin](https://www.amazon.it/Software-Development-Principles-Patterns-Practices/dp/0132760584).

### Detection strategy

The detection of the God component (GC) smell is done using the size, in terms of number of lines of code, of the system analysed.

GC is detected at the container-level (e.g., packages in Java). The smell detection is based on Lippert and Rook's definition of GC, which is based on the total number of lines of code contained in the package.
While Lippert and Rook suggest to use a fixed threshold of 27.000 lines of code to detect the smell, our approach is more sophisticated and data-driven.
We calculate the detection threshold dynamically. The threshold is calculated as `LinesOfCode = Max(LinesOfCode_System, LinesOfCode_Benchmark)` where each individual `LinesOfCode_*` is calculated using frequency analysis of the metric `LinesOfCode` computed on the system and the benchmark separately. The metric is calculated as the total number of lines of code of all the elemnts belonging to a specific component.
The specific approach used to calculate the threshold is detailed [here](https://ieeexplore.ieee.org/abstract/document/7181590/?casa_token=Hiyr0DFJbBkAAAAA:-Q6s9b_--cb1ALK6AEblsofWUjr82E6cTRV7oIFiwd9cIJRG65XN2d5gE-3B-n1M8zxX1pPU).


![GC](https://www.arcan.tech/wp-content/uploads/2023/01/god.jpg)

## Hub-Like Dependency

When an architectural component has (outgoing and ingoing) dependencies with a large number of other components. 

### Drawbacks
The component affected by the smell:

- centralizes logic
- is a unique point of failure
- favors change ripple effects

The smell violates the [Modularity Principle](http://www.cs.sjsu.edu/~pearce/modules/lectures/ood/principles/Modularity.htm) defined by [R. C. Martin](https://www.amazon.it/Software-Development-Principles-Patterns-Practices/dp/0132760584).

### Detection strategy

The detection of Hublike Dependency (HL) in Arcan is done starting from the [dependency graph](glossary.md#dependency-graph) of the system under analysis.

HL, or simply "hub", is detected on both units and containers (e.g., classes and packages in Java). A hub is detected whenever a component in the system has "too many" incoming and outgoing dependencies (FanIn and FanOut, respectively). The "too many" is calculated using a dynamic threshold that is based on both a benchmark of 100+ systems (from the [Qualitas Corpus](http://qualitascorpus.com/)) and the system under analysis.
This allows us to not pick the the threshold arbitrarily, but instead use a **data-driven** approach.

In particular, the threshold is calculated as `Threshold = Max(Threshold_System, Threshold_Benchmark)` where each individual `Threshold_*` is calculated using frequency analysis of the metric `TotalDeps` computed on the system and the benchmark separately, where `TotalDeps(x) = FanIn(x) + FanOut(x)` for all components `x`.
The specific approach used to calculate the threshold is detailed [here](https://ieeexplore.ieee.org/abstract/document/7181590/?casa_token=Hiyr0DFJbBkAAAAA:-Q6s9b_--cb1ALK6AEblsofWUjr82E6cTRV7oIFiwd9cIJRG65XN2d5gE-3B-n1M8zxX1pPU).


![HL](https://www.arcan.tech/wp-content/uploads/2023/01/hub.jpg)

## Unstable Dependency

Describes an architectural component that depends on other components that are less stable than itself. [Instability](https://codinghelmet.com/articles/how-to-use-module-coupling-and-instability-metrics-to-guide-refactoring) (proneness to change) is measured using [R. C. Martin](https://www.amazon.it/Software-Development-Principles-Patterns-Practices/dp/0132760584)’s formula.

### Drawbacks

The component affected by the smell can:

- favors change ripple effects
- be subjected to frequent changes

The smell violates the [Stable Dependency Principle](https://devlead.io/DevTips/StableDependenciesPrinciple) defined by [R. C. Martin](https://www.amazon.it/Software-Development-Principles-Patterns-Practices/dp/0132760584).

### Detection strategy

The detection of Unstable dependency (UD) is done using the [dependency graph](glossary.md#dependency-graph) of the system under analysis.

UD is detected at the container-level (e.g., packages in Java) only, whenever a container depends on other containers that are less stable than itself.
By *Instability* we mean R.C. Martin's Instability metric, whose definition can be found [here](https://www.oreilly.com/library/view/clean-architecture-a/9780134494272/). Instability calculates how easy it is for a container to change because of other containers (e.g. packages) in the system have changed. Namely, it is a measure of the risk of ripple change effects.

The detection rule is the following: `Intability(x) > Instability(y) + delta` for all containers `y` such that `x` depends upon, and  `x` is the container (e.g., package) that we are checking for the presence of UD.


![UD](https://www.arcan.tech/wp-content/uploads/2023/01/unstable.jpg)
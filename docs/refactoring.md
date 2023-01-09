# Refactoring best practices

## Cyclic Dependency
The main goal when refactoring a cycle is to break one or more dependencies. 

### Refactoring of Cyclic Dependencies affecting UNITS
To better exemplify the techniques, we will consider a cycle made of two units, A and B. The techniques can be applied to break larger cycles by iterating the refactoring steps.

<figure markdown>
![CD_1](https://www.arcan.tech/wp-content/uploads/2023/01/slide_modification_cycle_1.jpg)
  <figcaption>Figure 1: graphical example of Cyclic Dependency smell</figcaption>
</figure>

Depending on the characteristics of the dependency to break, different refactoring techniques can be adopted:

- **Move function**: move one or more functions (e.g., Java method) into the target unit. This technique is feasible when the function is not invoked within the unit itself and the only problem is that the function is misplaced.
- **Extract unit**: create a new unit and place all the code responsible for the cyclic dependency in it. 

<figure markdown>
![CD_2](https://www.arcan.tech/wp-content/uploads/2023/01/slide_modification_cycle_2.jpg)
  <figcaption>Figure 2: example of “Extract unit” refactoring technique</figcaption>
</figure>

- **Create interface**: Introduce an interface for one of the abstractions involved in the cycle. The new interface contains all methods that A calls on B. A only knows the interface that is implemented by B. Mind that this technique can be used if A only uses B and does not generate instances of B.

<figure markdown>
![CD_3](https://www.arcan.tech/wp-content/uploads/2023/01/slide_modification_cycle_3.jpg)
  <figcaption>Figure 3: example of “Create interface” refactoring technique</figcaption>
</figure>

- **Merge units**: if the units involved in the cycle represent a semantically single object, merge the units into a single unit.



### Refactoring of Cyclic Dependencies affecting CONTAINERS

In the case of Cyclic Dependencies affecting containers (e.g., Java packages), you can face two possibilities:
- The cycle is caused by a cycle among units. In such a case, you can apply the same techniques for breaking cycles among units.
- The cycle only exists among packages. In such a case, it is likely that there is a misplaced unit of function. You must move one of the pieces of code generating the dependency.
    - Apply move unit from one container to another in the case an entire unit or units are misplaced.
    - Apply move function from one unit to another in the case one or more functions are misplaced.

<figure markdown>
![CD_4_5](https://www.arcan.tech/wp-content/uploads/2023/01/slide_modification_cycle_4_5.jpg)
  <figcaption>Figure 4_a: example of container cycle caused by a cycle among units - Figure 4_b: example of container cycle caused by misplaced code</figcaption>
</figure>










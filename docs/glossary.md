## Glossary

### Project
The software project that you want to analyse with Arcan. It can be a folder containing source code or a Git repository (local or remote, e.g., hosted on Github).

### Version
Every time you change something in your project's source code, Arcan tracks a new version. You can run Arcan multiple times on different versions of the same project. Versions can be mapped to commits if you run Arcan on a Git repository.

### Analysis
A single execution of Arcan. An analysis is associated to a specific project’s version.

### Page
A page of Arcan which contains dashboards or results.

### Architectural smell
A software architecture problem affecting one or more parts of a codebase. See [here](architectural_smells.md) for more information.

### Plot
A graphic showing an insight or result.

### Dependency Graph
The high-level representation of the project’s architecture. 

### Container
In Arcan, the architectural components at the highest level of abstraction. Language reference: 

- Java: package=container;
- C/C++: folder=container;
- C#: namespace=container;
- Python: python package=container, directory=container.

### Unit
In Arcan, the architectural components at the lowest level of abstraction. Language reference: 

- Java: class=unit;
- C/C++: file=unit;
- C#: class=unit;
- Python: [python module](https://docs.python.org/3/tutorial/modules.html)=unit, file=unit.


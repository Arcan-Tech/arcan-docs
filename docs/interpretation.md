# Results interpretation

## Technical Debt score

The following table illustrates how to interpret the [Technical Debt score](inspect_project.md#project-card) value.

| Score | Ranking                            | Description                                                                                                                                                                                                                                         |
|:-----:|------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|   A   | Better than 80-100% of projects    | Best possible scenario. Little to no technical debt was detected. Keep monitoring to ensure new code does not introduce any.                                                                                                                        |
|   B   | Better than 60%-80% of projects    | Technical debt is under control, but some [Architectural Smells](architectural_smells.md) might become problematic in the near future.                                                                                                                                         |
|   C   | Better than 40%-60% of projects    | There’s an average amount of technical debt in the system, with some Architectural Smells being critical. These could be ideal candidates for refactorings. The system is relatively maintainable, but maintainability is starting to get affected. |
|   D   | Better than 20%-40% of projects    | There’s a conspicuous amount of technical debt in the system, although the system is still maintainable. The suggested course of action is to identify a few critical smells and refactor them (either incrementally or all at once).               |
|   F   | Better than 0%-20% of the projects | The system is riddled with technical debt, and maintainability is greatly affected. A major refactoring should be considered, although, given the amount of technical debt, it could not be possible.                                               |

## How to identify refactoring opportunities:

1. Head to the [“Assessment”](inspect_project.md#assessment-page) page of your project.
2. Order the Architectural Smells by highest Severity or highest TechDebt Index. This will let you identify the most critical smells in your project:
3. Identify one or two smells to focus on. What you can do next:
    - Invest time now to save on maintenance by removing the smell that gives you the most problems. In that case, see our [refactoring suggestions and best practices](refactoring.md).
OR
    - Save time now by not refactoring, but be aware that future maintenance will be harder. In this case, we suggest integrating Arcan with your CI pipeline and running it twice weekly and before new releases to prevent the introduction of additional Technical Debt.
  
Once you discover the presence of new smells, you should tackle them immediately. Smells in the first phase of their life are easier to refactor than older ones.

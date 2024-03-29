# Welcome to Arcan Documentation

Arcan is an automatic tool for software quality analysis and (Architectural) Technical Debt detection, evaluation and visualisation.

Arcan helps you keep Technical Debt under control and avoid its shortcomings. The tool analyses 5 programming languages
and integrates into your CI pipeline to ensure that your code continuously meets high-quality standards.

The analysis is available for the following programming languages:

* Java
* C
* C++
* C#
* Python

More languages are coming next! Learn more on language version compatibility [here](compatibility.md).

## Architectural Technical Debt

The backbone of a software system is its [architecture](https://martinfowler.com/architecture/). Software architectures need to continuously update, adapt and change. Software maintenance and evolution become expensive, time-consuming, and sometimes impossible if architecture quality is not continuously assessed. 

The accumulation of sub-optimal architectural solutions inside a software system results in the growth of *Architectural Technical Debt*, a segment of a bigger problem ([Technical Debt](https://martinfowler.com/bliki/TechnicalDebt.html)) that costs [500 billion dollars worldwide](https://stripe.com/files/reports/the-developer-coefficient.pdf). 

> 33% of the time of a developer is *wasted* to manage technical debt.

This problem manifests itself in specific contexts, for instance when there is the need to migrate an obsolete technology or when there is the need to fast scale up the number of features of a software application. However, the deepest sources causing this problem can hardly be detected by hand, and software developers lack the tools to detect them. 

We offer a platform for automatic source code analysis that assesses the [quality](https://iso25000.com/index.php/en/iso-25000-standards/iso-25010) of software architectures in a few minutes. Arcan indicates the exact pain points in the code so that developers can fix them and make the code easy to program. The most innovative facet of Arcan is the ability to extract strategic data regarding Architectural Technical Debt so that managers can make informed decisions about software production and optimization. 

![The developer coefficent](https://www.arcan.tech/wp-content/uploads/2023/01/arcan-pitch-deck-ENG-investors_600.jpg)

### Architectural Smells

A symptom of Architectural Technical Debt is the presence of *Architectural Smells*, design decisions that negatively impact the system internal quality. Arcan main aim is to automatically detect Architectural Smells, indicate where they are located in code and suggest best practices about how to remove them. 
[Refactoring Architectural Smells](refactoring.md) is the activity of removing Architectural Smells from the system by reorganising the code and/or the architecture of the affected artefacts according to a new design. This is a effortful activity, thus it is only adopted as the last resort. Typically, it is preferred to avoid at all the introduction of Technical Debt (e.g. Architectural Smells) by ensuring only clean new code is committed to the codebase.

Architectural Smells come in different types. [Here](architectural_smells.md) you can find the updated lists of the ones detected by Arcan and [here](refactoring.md) are the descriptions of the best practices to remove them.

## Getting started

To download our 30-days trial, please visit [www.arcan.tech](https://www.arcan.tech/get-started/).
You will need [docker](https://docs.docker.com/get-docker/) installed on your machine to run Arcan, but don't worry! You don’t need to know how Docker works to use Arcan.

> You can also have a quick look to the tool with the Arcan [online demo](https://demo.arcan.tech/).

### Resources
* [Quickstart](get_started.md)
* [Arcan glossary](glossary.md)
* [Guide to results inspection](inspect_project.md)
* [Walkthrough video (ENG)](https://youtu.be/YLSGT4E_Fbg)
* [Walkthrough video (ITA)](https://youtu.be/MFo9Yocq-q8)

## Get a yearly license

Arcan is distributed on-premise and in the cloud with yearly licence.
Pricing depends on the size of the application portfolio to analyse and the number of needed floating licenses.

Contact us at <info@arcan.tech> or leave a message on our [website](https://www.arcan.tech/contact/) to get a quote.

## Community and Support

Need help or more information? There are many ways to contact us, choose your favorite [here](support.md).

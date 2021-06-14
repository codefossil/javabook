# Software Architecture Document Template

## Introduction and Goals

> underlying business goals, essential features and functional requirements for the system

> Short description of the functional requirements, driving forces, extract (or abstract) of requirements. Link to (hopefully existing) requirements documents (with version number and information where to find it).

## Stakeholders

> Document roles and responsibilities of the each user type

Add text here

| Role/Name   | Contact                   | Expectations              |
| ----------- | ------------------------- | ------------------------- |
| Role-1      | Contact-1                 | *&lt;Expectation-1*&gt;   |
| Role-2      | Contact-2                 | *&lt;Expectation-2*&gt;   |

## Constraints

> Any constraint that you need to keep in mind for your design
>
> Examples:
>
> 1. Technology constraints
> 2. Cost constraints
> 3. Time constraints

Add text here

## Assumptions

> Any assumptions that you have made while coming up with the design

Add text here

## Business scope and context

> Important business processes that you have considered while documenting the design. 

Add text here

## Non-functional Requirements (Quality Attributes)

> Most important quality attributes based on the business goals

Add text here

### Back of the envelope calculations

> Do quick calculations for storage needs, read vs writes, etc.

Add text here

## Solution Context and Container (Style and Technology Choices)

> Detail isn't important here as this is your zoomed out view showing a big picture of the system landscape. The focus should be on people (actors, roles, personas, etc) and software systems

> Which architecture style you are proposing to build the application

> platform selection, language selection, framework selection

Add text here

## Solution Component

> context map

> List of functional components that will make the system. Which actor will work on which functional part.

> The list of technologies that you will use to build the system and the reason you choose them.

Add text here

## Solution Building Structure (Runtime Views)

> important use cases or features: how do building blocks execute them?interactions at critical external interfaces: how do building blocks cooperate with users and neighboring systems?

Remark: The main criterion for the choice of possible scenarios (sequences, workflows) is their architectural relevance. It is not important to describe a large number of scenarios. You should rather document a representative selection.

## Solution Deployment

> Put the artifacts into existing environment. 

> how is config, logging, monitor working.


## Architecture Decisions

> Important architecture decision that you want development team to follow

Add text here

## Risks and Technical Debts

> A list of identified technical risks or technical debts, ordered by priority

## Reference

https://github.com/NetworkedAssets/arc42-in-markdown-template/blob/master/2.%20Single%20File/Arc42%20Template%20in%20Markdown.md

https://shekhargulati.com/2021/04/24/software-architecture-document-template/

[IBM Garage Architecture Center](https://medium.com/ibm-garage/gitarchitecture-a-better-way-to-capture-architectural-decisions-b3574a3d604)
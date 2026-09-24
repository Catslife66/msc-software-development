# Week 1

## Reading list - Software Engineering - Ian Sommerville (10th Edition)

### Chapter 1 - Introduction

Key points:

- Software engineering is an engineering discipline that is concerned with all aspects of software production. 

- Software is not just a program or programs but also includes all electronic documentation that is needed by system users, quality assurance staff, and developers. Essential software product attributes are maintainability, dependability and security, efficiency, and acceptability. 

- The software process includes all of the activities involved in software development. The high-level activities of specification, development, validation, and evolution are part of all software processes. 

- There are many different types of system, and each requires appropriate software engineering tools and techniques for their development. Few, if any, specific design and implementation techniques are applicable to all kinds of system. 

- The fundamental ideas of software engineering are applicable to all types of software system. These fundamentals include managed software processes, software dependability and security, requirements engineering, and software reuse. 

- Software engineers have responsibilities to the engineering profession and society. They should not simply be concerned with technical issues but should be aware of the ethical issues that affect their work. 

- Professional societies publish codes of conduct that embed ethical and professional standards. These set out the standards of behaviour expected of their members.

### Chapter 2 - Software Processes

#### Software process models

A software process model sometimes called a software development life cycle or SDLC model.

The general process models:

1. The waterfall model:
   - requirements definition
   - system’s service, contains, goals -> established by the system users
   - system and software design -> establish an overall system architecture
   - implementation and unit testing
   - integration and system testing 
   - operation and maintenance -> the system is installed and put into practical use

2. Incremental development 

   The system is developed as a series of versions(increments) with each version adding functionality to the previous version

   A fundamental part of agile development methods.

   Increment development reflects the way that we solve problems. We rarely work out a complete problem solution in advance but move toward a solution in a series of steps, back-tracking when we realise that we have made a mistake. It is cheaper and easier to make changes in the software as it it being developed. 

   Three advantages over the waterfall model:
   1. the cost of implementing requirements changes is reduced.
   2. it is easier to get customer feedback on the development work that has been done.
   3. early delivery and deployment of useful software to the customer is possible

   Problems:
   1. the process is not visible
   2. system structure tends of degrade as new increments are added.

3. Integration and configuration - reusable components or systems 

   The stages in this process are:
   - Requirements specification
   - Software discovery and evaluation 
   - Requirements refinement
   - Application system configuration
   - Component adaptation and integration

#### Process activities

1. software specification
   - Requirements elicitation and analysis
   - Requirements specification -> user and system requirements
   - Requirements validation
2. software design and implementation 
   - Architectural design - identify the overall structure of the system and the principal components, their relationship and how they are distributed.
   - Database design - the statement data structures and how these are to be represented in a database
   - Interface design - define the interfaces between system components 
   - Component selection and design - search for reusable components and design new software components
3. software validation
   The stages in the testing process are:
   1. component testing
   2. system testing
   3. customer testing
4. software evolution

#### Coping with change

Tow related approaches may be used to reduce the costs of rework:

1. change anticipation
2. change tolerance

Two ways of coping with change and changing system requirements:

1. system prototyping 
2. incremental delivery

#### process improvement

The stages in this process are:

1. process measurement
2. process analysis
3. process change

#### Key points

- Software processes are the activities involved in producing a software system. Software process models are abstract representations of these processes. 

- General process models describe the organisation of software processes. Examples of these general models include the waterfall model, incremental development, and reusable component configuration and integration.

- Requirements engineering is the process of developing a software specification. Specifications are intended to communicate the system needs of the customer to the system developers. 

- Design and implementation processes are concerned with transforming a requirements specification into an executable software system. 

- Software validation is the process of checking that the system conforms to its specification and that it meets the real needs of the users of the system. 

- Software evolution takes place when you change existing software systems to meet new requirements. Changes are continuous, and the software must evolve to remain useful. 

- Processes should include activities to cope with change. This may involve a prototyping phase that helps avoid poor decisions on requirements and design. Processes may be structured for iterative development and delivery so that changes may be made without disrupting the system as a whole. 

- Process improvement is the process of improving existing software processes to improve software quality, lower development costs, or reduce development time. It is a cyclic process involving process measurement, analysis, and change.

---

## Summary from the reading

### 1. What is software engineering?

**Software engineering is concerned with all aspects of software production**, not simply writing programs.

```
What problem am I solving?
        ↓
What should the application do?
        ↓
How should I structure it?
        ↓
Frontend / API / database
        ↓
Implement features
        ↓
Test/debug
        ↓
Deploy
        ↓
Fix and improve it
```

### 2. A software product needs quality attributes

| Attribute                    | Engineering question                               | Your previous training                                 |
| ---------------------------- | -------------------------------------------------- | ------------------------------------------------------ |
| **Maintainability**          | Can we safely understand and change it?            | SOLID, layering, separation of responsibilities        |
| **Dependability & security** | Can users rely on it and can we protect it?        | authentication, authorization, HTTPS, failure handling |
| **Efficiency**               | Does it use resources appropriately?               | algorithms, indexing, caching, DB performance          |
| **Acceptability**            | Does it actually work appropriately for its users? | UI/API design, usability                               |

### 3. The fundamental software process

1. Specification
   _What should we build?_
2. Development - Design & implementation
   _How should we build it?_
3. Validation
   _Did we build what was required?_
4. Evolution
   _What happens when the world changes?_

### 4. Different systems require different approaches

For example, architecture appropriate for:

```
personal portfolio website
```

isn't necessarily appropriate for:

```
online banking
```

which isn't necessarily appropriate for:

```
aircraft control software
```

Therefore:

**good engineering ≠ blindly following a particular architecture**

Instead:

**requirements + constraints → engineering decisions**

### 5. Software process models

```
How should those activities be organised?

             SOFTWARE PROCESS MODELS
                       │
        ┌──────────────┼───────────────┐
        │              │               │
    Waterfall      Incremental      Integration & Configuration
```

---

## Engineering-process Reasoning

**Problem / stakeholder need**  
↓  
**Requirements**  
_What should the system do?_  
↓  
**Software process**  
_How will we organise development?_  
↓  
**Architecture & design**  
_How should responsibilities be structured?_  
↓  
**Implementation**  
_How do we build it?_  
↓  
**Verification & validation**  
_Did we build it correctly, and did we build the right thing?_  
↓  
**Deployment & operation**  
↓  
**Evolution**  
_How does it survive change?_

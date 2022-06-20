---
title: Model
weight: 7
bookToc: false
---
# Model

The following rules apply to a **Planet** populated by **Products**, made by a **Process** that may extract Raw Material **RM** from the **Planet**.

- The **Process** is specified by **Cyclos** that are grouped in **Stages**.
- The **Facility** provides infrastructural & operational **Resources**. 
- **Stages** consumes **Resources**, both from **Facility** and from **Cyclo**.
- The **Stage** allocates **Resources** from the **Facility** to accomplish its task.
- Every **Stage** requires **Skills** to accomplish its task.
- The **Skill** is provided by a combination of **Workers** and/or **Tools**.
- The **Stage** also allocates **Resources** from the **Cyclo** to accomplish its task.
- The **Stage** extracts **RM** from **Planet** as Work In Process **WiP**.
- The **Stage** transforms **WiP** through the **Cyclo** until it becomes **Product**.
- **Product** and **RM** are both derived from **WiP**, with some logistic between them.
- **WiP** becomes **Product** that may become **RM** to another **Cyclo**.

The **Stage**, detailed below, allocates **Facility** resources divided into two categories:

- **FacilityInfra**: includes infrastructure items, like Shop Floor Area, Energy, etc.
- **FacilityOp**: includes operational items with **Skills**, like Tools and Workers.

{{< mermaid >}}
classDiagram
    Planet --> "1..n" Product : populated_by
    Planet --> "1..n" RM : provides
    Product --> "1..n" Process : made_by
    Product --> WiP : Sell
    Process --> "1..n" Cyclo : composed_of
    Cyclo --> "1..n" Stage : composed_of
    Stage --> "1..n" WiP : 3.transforms
    Stage --> "1..n" Facility : 2.allocates
    Stage --> Stage : previous_next
    WiP --> RM : Buy
    FacilityInfra <|-- Energy
    FacilityInfra <|-- Area
    FacilityInfra <|-- Other
    Worker --> "1..n" Skill : has_skill
    Worker --> "0..n" Worker : commands
    Worker --> "0..n" Tool : commands
    Tool --> "0..n" Tool : commands
    Tool --> "1..n" Skill : has_skill
    Facility <|-- FacilityInfra : infrastructure
    FacilityOp <|-- Worker
    FacilityOp <|-- Tool
    Facility <|-- FacilityOp : operation
    Stage --> "1..n" Skill : 1.requires
{{< /mermaid >}}


{{< hint info >}}
**Published in [Business Amplifier](https://www.amazon.com/Business-Amplifier-M-Sc-Motta-Lopes/dp/B083XGK14Q), also [e-book](https://www.amazon.com/Business-Amplifier-Jose-Motta-Lopes-ebook-dp-B086L6V6QY/dp/B086L6V6QY/) and [Amplificador de Negócios](https://www.amazon.com/M-Sc-Jose-Motta-Lopes/dp/8592301009).**
{{< /hint >}}

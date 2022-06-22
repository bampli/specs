---
title: Model
weight: 7
bookToc: false
---
# Model

The following rules apply to a **Planet** populated by **Products**, made by a **Process** that may extract Raw Material **RM** from the **Planet**.

- The **Process** is specified by **Cyclos**, grouped in **Stages**.
- The **Facility** provides infrastructural & operational **Resources**. 
- **Stage** and **WiP** are first class citizens of **Cyclo** operation.
- The **Stage** allocates **Resources** to accomplish its task.
- Every **Stage** requires **Skills** to accomplish its task.
- The **Skill** is provided by a combination of **Workers** and/or **Tools**.
- The **Stage** buys **RM** from **Planet** as Work In Process **WiP**.
- The **Stage** transforms **WiP** through the **Cyclo**.
- The **Stage** sells **Product** to **Planet** as Work In Process **WiP**.
- **Product** and **RM** are extensions of **WiP**, with some logistic between them.
- **WiP** becomes **Product** that becomes **RM** that becomes **WiP** at another **Cyclo**.

The **Stage**, detailed below, allocates **Facility** resources divided into two categories:

- **Facility Infrastructure**: includes items like Shop Floor Area, Energy, Equipment, etc.
- **Facility Operation**: includes operational items with **Skills**, like **Worker** and **Tool**.

{{< mermaid >}}
classDiagram
    Planet --> "1..n" Product : populated_by
    Planet --> "1..n" RM : provides
    Product --> "1..n" Process : made_by
    Product --> WiP : sells
    Process --> "1..n" Cyclo : composed_of
    Cyclo --> "1..n" Stage : composed_of
    Stage --> "1..n" WiP : 3.transforms
    Stage --> "1..n" Facility : 2.allocates
    Stage --> Stage : previous_next
    WiP --> RM : buys
    Infrastructure <|-- Energy
    Infrastructure <|-- Area
    Infrastructure <|-- Other
    Worker --> "1..n" Skill : has_skill
    Worker --> "0..n" Worker : commands
    Worker --> "0..n" Tool : commands
    Tool --> "0..n" Tool : commands
    Tool --> "1..n" Skill : has_skill
    Facility <|-- Infrastructure
    Operation <|-- Worker
    Operation <|-- Tool
    Facility <|-- Operation
    Stage --> "1..n" Skill : 1.requires
{{< /mermaid >}}


{{< hint info >}}
**Published in [Business Amplifier](https://www.amazon.com/Business-Amplifier-M-Sc-Motta-Lopes/dp/B083XGK14Q), also [e-book](https://www.amazon.com/Business-Amplifier-Jose-Motta-Lopes-ebook-dp-B086L6V6QY/dp/B086L6V6QY/) and [Amplificador de Negócios](https://www.amazon.com/M-Sc-Jose-Motta-Lopes/dp/8592301009).**
{{< /hint >}}

---
title: Model
weight: 7
bookToc: false
---
# Model

The following rules apply to a **Planet** populated by **Products**, made by a **Process** inside a **Facility**.

- The **Process** is specified by **Cyclos**, grouped in **Stages**.
- The **Facility** provides infrastructural & operational **Resources**. 
- **Stage** and **WiP** (Work In Process) are first class citizens of **Cyclo**.
- The **Stage** allocates **Resources** to accomplish its task.
- Every **Stage** requires **Skills** to accomplish its task.
- The **Skill** is provided by a combination of **People** and/or **Tools**.
- The **Stage** buys **Product** from **Planet** as **WiP**.
- The **Stage** transforms **WiP** through the **Cyclo**.
- The **Stage** sells **Product** to **Planet** as **WiP**.
- **WiP** becomes **Product** that becomes **WiP** at another **Cyclo**.

The **Stage**, detailed below, allocates **Facility** resources divided into two categories:

- **Facility Infrastructure**: includes items like Shop Floor Area, Energy, Equipment, etc.
- **Facility Operation**: includes operational items with **Skills**, like **People** and **Tool**.

{{< mermaid >}}
classDiagram
    Planet --> "1..n" Product : populated_by
    Product --> "1..n" Process : made_by
    Stage --> "1..n" Skill : require
    Product --> WiP : sell
    Process --> "1..n" Cyclo : composed_of
    Cyclo --> "1..n" Stage : composed_of
    Stage --> "1..n" Facility : alloc
    Stage --> Stage : next
    Stage --> "1..n" WiP : transform
    WiP --> Product : buy
    Infrastructure <|-- Energy
    Infrastructure <|-- Area
    Infrastructure <|-- Other
    People --> "1..n" Skill : has_skill
    People --> "0..n" People : command
    People --> "0..n" Tools : command
    Tools --> "0..n" Tools : command
    Tools --> "1..n" Skill : has_skill
    Facility <|-- Operation
    Facility <|-- Infrastructure
    Operation <|-- People
    Operation <|-- Tools
{{< /mermaid >}}


{{< hint info >}}
**Published in [Business Amplifier](https://www.amazon.com/Business-Amplifier-M-Sc-Motta-Lopes/dp/B083XGK14Q), also [e-book](https://www.amazon.com/Business-Amplifier-Jose-Motta-Lopes-ebook-dp-B086L6V6QY/dp/B086L6V6QY/) and [Amplificador de Neg??cios](https://www.amazon.com/M-Sc-Jose-Motta-Lopes/dp/8592301009).**
{{< /hint >}}

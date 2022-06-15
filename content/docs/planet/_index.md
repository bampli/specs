---
title: "Planet"
bookFlatSection: false
weight: 45
---

# Planet

The **Planet** shown below is populated by at least one **Product** made by its respective **Process**. The **Planet** also provides raw material **RM** that is extracted as work in process **WIP**. Each **Process** has at least one **Cyclo**, composed by at least one **Stage**. A **Facility** provides **Resources** and **Skills** to support **Stage** transformations in **WIP**. 

{{< mermaid >}}
classDiagram
    Planet --> "1..n" Product : populated_by
    Planet --> "1..n" RM : provides
    Product --> "1..n" Process : made_by
    Process --> "1..n" Cyclo : composed_of
    Cyclo --> "1..n" Stage : composed_of
    Stage --> Stage : previous_next
    WIP <|-- RM : extract
    Stage --> "1..n" Facility : allocates
    Stage <|-- WIP : transform
    Stage --> "1..n" Skill : requires
{{< /mermaid >}}

{{< hint info >}}
**Published in [Business Amplifier](https://www.amazon.com/Business-Amplifier-M-Sc-Motta-Lopes/dp/B083XGK14Q), also [e-book](https://www.amazon.com/Business-Amplifier-Jose-Motta-Lopes-ebook-dp-B086L6V6QY/dp/B086L6V6QY/) and [Amplificador de Negócios](https://www.amazon.com/M-Sc-Jose-Motta-Lopes/dp/8592301009).**
{{< /hint >}}

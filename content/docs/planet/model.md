---
title: Model
weight: 7
bookToc: false
---
# Model

The **Planet** shown below is populated by at least one **Product** made by its respective **Process**. The **Planet** also provides raw material **RM** that is extracted as work-in-process **WiP**. Each **Process** has at least one **Cyclo**, composed by at least one **Stage** that requires at least one **Skill** to be accomplished. The **Facility** provides resources to support **Stage** transformations in **WiP**. 

{{< mermaid >}}
classDiagram
    Planet --> "1..n" Product : populated_by
    Product --> "1..n" Process : made_by
    Stage --> "1..n" Skill : require
    Stage --> "1..n" Facility : alloc
    Process --> "1..n" Cyclo : composed_of
    Cyclo --> "1..n" Stage : composed_of
    Stage --> Stage : next
    WiP --> Product : buy
    Stage --> WiP : transform
    Product --> WiP : sell
{{< /mermaid >}}

{{< hint info >}}
**Published in [Business Amplifier](https://www.amazon.com/Business-Amplifier-M-Sc-Motta-Lopes/dp/B083XGK14Q), also [e-book](https://www.amazon.com/Business-Amplifier-Jose-Motta-Lopes-ebook-dp-B086L6V6QY/dp/B086L6V6QY/) and [Amplificador de Negócios](https://www.amazon.com/M-Sc-Jose-Motta-Lopes/dp/8592301009).**
{{< /hint >}}

---
title: Model
weight: 7
bookToc: false
---
# Model

The **Planet** shown below is populated by at least one **Product** made by at least one **Cyclo**.

{{< mermaid >}}
classDiagram
    Planet --> "1..n" Product : populated_by
    Company --> Facility : manage
    Product --> "1..n" Cyclo : made_of
    Facility --> "1..n" Process : deploy
    Stage --> "1..n" Skill : require
    Process --> "1..n" Cyclo : contain
    Cyclo --> "1..n" Stage : contain
    Stage --> Stage : next
    WiP --> Product : buy
    Stage --> WiP : transform
    Product --> WiP : sell
{{< /mermaid >}}

The **Planet** provide all **Products**, both as final goods and/or raw materials. Extracted and transformed by **Stages**, assets move inside the **Process** as work-in-process **WiP**. Each **Process** has at least one **Cyclo**, composed by at least one **Stage** that requires at least one **Skill** to be accomplished. The **Facility** provides the resources to deploy the **Process**, supporting the **Stage** transformations in **WiP**. 

{{< hint info >}}
**Published in [Business Amplifier](https://www.amazon.com/Business-Amplifier-M-Sc-Motta-Lopes/dp/B083XGK14Q), also [e-book](https://www.amazon.com/Business-Amplifier-Jose-Motta-Lopes-ebook-dp-B086L6V6QY/dp/B086L6V6QY/) and [Amplificador de Negócios](https://www.amazon.com/M-Sc-Jose-Motta-Lopes/dp/8592301009).**
{{< /hint >}}

---
title: "Planet"
bookFlatSection: false
weight: 45
---

# Planet

The **Planet** model is shown below populated by **Products** made by their respective **Processes**. Each **Process** is a collection of **Stages** that requires **Resources** and **Skills**.

{{< mermaid >}}
classDiagram
    Planet --> "1..n" Product : populated_by
    Product --> "1..n" Process : made_by
    Process --> "1..n" Stage : composed_of
    Stage --> "1..n" Resource : allocates
    Stage --> Stage : previous_next
    Stage --> "1..n" Skill : requires
{{< /mermaid >}}


{{< hint info >}}
**Published in [Business Amplifier](https://www.amazon.com/Business-Amplifier-M-Sc-Motta-Lopes/dp/B083XGK14Q), also [e-book](https://www.amazon.com/Business-Amplifier-Jose-Motta-Lopes-ebook-dp-B086L6V6QY/dp/B086L6V6QY/) and [Amplificador de Negócios](https://www.amazon.com/M-Sc-Jose-Motta-Lopes/dp/8592301009).**
{{< /hint >}}

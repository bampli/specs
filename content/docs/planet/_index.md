---
title: "Planet"
bookFlatSection: false
weight: 45
---

# Planet Model

The **Planet** model, shown below, allocates **Facility** resources divided into two categories:

- **FacilityInfra**: includes infrastructure items, like Shop Floor Area, Energy, etc.
- **FacilityOp**: includes operational items with **Skills**, like Tools and Workers.

{{< mermaid >}}
classDiagram
    Planet --> "1..n" Product : populated_by
    Product --> "1..n" Process : made_by
    Process --> "1..n" Stage : composed_of
    Stage --> "1..n" Resource : allocates
    Stage --> Stage : previous_next
    Worker --> "1..n" Skill : has_skill
    Worker --> "0..n" Tool : commands
    Tool --> "0..n" Tool : commands
    Tool --> "1..n" Skill : has_skill
    Resource <|-- Cyclo : from_cyclo
    Cyclo <|-- RM : external
    Cyclo <|-- WIP : internal
    Resource <|-- Facility : from_facility
    Facility <|-- FacilityInfra : infrastructure
    FacilityInfra <|-- Energy
    FacilityInfra <|-- Area
    Facility <|-- FacilityOp : operation
    FacilityOp <|-- Worker
    FacilityOp <|-- Tool
    Stage --> "1..n" Skill : requires
{{< /mermaid >}}


{{< hint info >}}
**Published in [Business Amplifier](https://www.amazon.com/Business-Amplifier-M-Sc-Motta-Lopes/dp/B083XGK14Q), also [e-book](https://www.amazon.com/Business-Amplifier-Jose-Motta-Lopes-ebook-dp-B086L6V6QY/dp/B086L6V6QY/) and [Amplificador de Negócios](https://www.amazon.com/M-Sc-Jose-Motta-Lopes/dp/8592301009).**
{{< /hint >}}

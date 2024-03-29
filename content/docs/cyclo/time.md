---
title: Times of Gain
weight: 8
bookToc: false
---
# Times of Gain (ToG)

Actually, the **Stage** is a state machine that changes in a timeline, according to the phases listed below:

- resource allocation
- setup
- execution
- resource release
- free

The following diagram show the Times of Gain (**ToG**) timeline:

{{< mermaid >}}
sequenceDiagram
    autonumber
    rect rgb(255, 0, 255, .3)
        Alloc-->>Setup: Resource Allocation Time
    end
    rect rgb(255, 255, 0, .3)
        Setup-->>Execution: Stage Setup Time
    end
    rect rgb(0, 255, 0, .3)
        Execution->>Release: Stage Execution Time
    end
    rect rgb(255, 0, 255, .3)
        Release-->>Free: Resource Release Time
    end
    rect rgb(0, 0, 255, .3)
        Alloc->>Free: Stage Total Time
    end
{{< /mermaid >}}

### Resource Allocation

- **Infrastructure** are **Resources** supported by the **Facility**, like Energy and Shop Floor Area.
- The **Skills** indicate **Operational Resources** to be sought in the **Facility**, like Tools and People.
- For each required **Resource**, check its availability. If it's not available, the **Stage** awaits.
- At **Resource** allocation phase, there may be a delay due to the **Resource Allocation Time**.

### Stage Setup
- Before each **Stage** execution, there may be a delay due to the **Stage Setup Time**.
- This delay is defined by the **Process** & **Facility**, including tool setup for example.

### Stage Execution

- From the **Cyclo** may eventually come and go assets like **WiP**.
- **Stages** execute transformations according to Deming's **Process** specification: *At each **Stage** there is production, that is, something happens in the set of assets that enter a **Stage**, causing their exit in a different state*.
- The Stage execution expects to introduce a delay known as the **Stage Execution Time**.

### Resource Release

- Any resulting **WiP** must be released to the next **Stage** in the **Cyclo**.
- **Resources** allocated from the Facility are eventually released to **FacilityInfra** & **FacilityOp**.
- At **Resource** release phase, there may be a delay due to the **Resource Release Time**.

{{< hint info >}}
**Published in [Business Amplifier](https://www.amazon.com/Business-Amplifier-M-Sc-Motta-Lopes/dp/B083XGK14Q), also [e-book](https://www.amazon.com/Business-Amplifier-Jose-Motta-Lopes-ebook-dp-B086L6V6QY/dp/B086L6V6QY/) and [Amplificador de Negócios](https://www.amazon.com/M-Sc-Jose-Motta-Lopes/dp/8592301009).**
{{< /hint >}}

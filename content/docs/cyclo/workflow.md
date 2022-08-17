---
title: Workflow
weight: 11
bookToc: false
---
# Workflow

The diagram below shows the allocation, setup, execution and release phases available for each **Stage**.

{{< mermaid >}}
stateDiagram
    [*] --> ALLOC : Cyclo is running
    ALLOC --> SETUP
    SETUP --> READY
    READY --> RELEASE
    RELEASE --> [*]
    state ALLOC {
        [*] --> FacilityInfra
        [*] --> Skill
        FacilityInfra --> Energy
        FacilityInfra --> Area
        Energy --> [*] : energy_ok
        Area --> [*] : area_ok
        Skill --> FacilityOp
        FacilityOp --> Tool
        Tool --> [*] : tool_skill_ok
        FacilityOp --> Worker
        Worker --> [*] : worker_skill_ok
    }
    state SETUP {
        setup
    }
    state READY {
        getWiP --> EXEC
        EXEC --> putWiP
        putWiP
    }
    state RELEASE {
        [*] --> Area
        Area --> FacilityInfra : area_free
        [*] --> Energy
        Energy --> FacilityInfra : energy_free
        [*] --> Tool
        Tool --> FacilityOp : tool_skill_free
        [*] --> Worker
        Worker --> FacilityOp : worker_skill_free
    }
{{< /mermaid >}}

{{< hint info >}}
**Published in [Business Amplifier](https://www.amazon.com/Business-Amplifier-M-Sc-Motta-Lopes/dp/B083XGK14Q), also [e-book](https://www.amazon.com/Business-Amplifier-Jose-Motta-Lopes-ebook-dp-B086L6V6QY/dp/B086L6V6QY/) and [Amplificador de Negócios](https://www.amazon.com/M-Sc-Jose-Motta-Lopes/dp/8592301009).**
{{< /hint >}}

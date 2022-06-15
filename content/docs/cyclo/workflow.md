---
title: Workflow
weight: 9
bookToc: false
---
# Workflow

When the **Cyclo** is running, each **Stage** should allocate all required **Resources** before receiving the "green" light to be executed. The diagram below shows the allocation, execution and release phases for each **Stage**.

{{< mermaid >}}
stateDiagram
    [*] --> Resource_Allocation : Cyclo is running
    Resource_Allocation --> Stage_Execution
    Stage_Execution --> Resource_Release
    Resource_Release --> [*]
    state Resource_Allocation {
        [*] --> Cyclo
        [*] --> FacilityInfra
        [*] --> Skill
        Cyclo --> RM
        Cyclo --> WIP
        RM --> [*] : rm_ok
        WIP --> [*] : wip_ok
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
    state Stage_Execution {
        execution
    }
    state Resource_Release {
        [*] --> WIP
        WIP --> Cyclo : wip_free
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


Some optimization may prevent unnecessary release/reallocation delays, according to rule five of Deming's **Process** specification: *Each Stage cooperates with the next and the previous, seeking optimization*.



{{< hint info >}}
**Published in [Business Amplifier](https://www.amazon.com/Business-Amplifier-M-Sc-Motta-Lopes/dp/B083XGK14Q), also [e-book](https://www.amazon.com/Business-Amplifier-Jose-Motta-Lopes-ebook-dp-B086L6V6QY/dp/B086L6V6QY/) and [Amplificador de Negócios](https://www.amazon.com/M-Sc-Jose-Motta-Lopes/dp/8592301009).**
{{< /hint >}}

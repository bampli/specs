---
title: Stage
weight: 9
bookToc: false
---
# Stage

When the **Cyclo** is running, each **Stage** should allocate all required **Resources**, before receiving the "green" light to execute.

## State

- **FREE**: Stage that requires Skills is created at Facility and free to use.
- **ALLOC**: Stage is allocating Resources from Facility Infrastrucure & Operation.
- **SETUP**: Stage with Skills satisfied, preparing to start Production.
- **READY**: Stage is ready for Production, maybe now EXEC or IDLE.
- **RELEASE**: Stage is releasing Resources from Facility Infrastrucure & Operation.

Some optimization may prevent unnecessary release/reallocation delays, according to rule five of Deming's **Process** specification: *Each Stage cooperates with the next and the previous, seeking optimization*.

## Time Distributions

During its lifespan within the [**Working Time**](/posts/tpm), the **Stage** should evaluate the following *elapsed time* frequency distributions:

- **StageFreeTime**: Time the Stage is freely available available at Facility.
- **ResourceAllocTime**: Time spent allocating Resources from Facility.
- **StageSetupTime**: Time spent with Stage setup.
- **StageReadyTime**: Time the Stage is ready for Production.
- **ResourceReleaseTime**: Time spent decomissioning the Stage.

*WorkingTime = StageFreeTime + ResourceAllocTime + StageSetupTime + StageReadyTime + ResourceReleaseTime* 

But StageReadyTime, which means the **Stage** is ready for Production, can be split even more:

- StageGetWipTime: Time to get the necessary WiPs from previous Stage.
- StageExecTime: Time the Stage takes to effectively transform the WiPs.
- StagePutWipTime: Time to put properly the WiP for the next Stage.
- StageIdleTime: Time the Stage is ready for Production, but idle due to WiP shortage.

*StageReadyTime = StageGetWipTime + StageExecTime + StagePutWipTime + StageIdleTime*  

## Workflow

The diagram below shows the allocation, execution and release phases for each **Stage**.

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
        Cyclo --> WiP
        RM --> [*] : rm_ok
        WiP --> [*] : wip_ok
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
        [*] --> WiP
        WiP --> Cyclo : wip_free
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

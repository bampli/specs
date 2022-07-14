---
title: Stage
weight: 9
bookToc: false
---
# Stage

When the **Cyclo** is running, each **Stage** should allocate all required **Resources**, before receiving the "green" light to execute.

## State

- **FREE**: Stage that requires Skills is created at Facility and available.
- **ALLOCATION**: Stage is allocating Resources from Facility Infrastructure & Operation.
- **SETUP**: Stage with Skills satisfied, preparing to initiate Production.
- **READY**: Stage is ready for Production, getting the WiP.
- **EXEC**: Stage is effectively transforming the WiP.
- **WIP**: Stage is putting the WiP.
- **RELEASE**: Stage is releasing Resources from Facility Infrastructure & Operation.

Some optimization may prevent unnecessary release/reallocation delays, according to rule five of Deming's **Process** specification: *Each Stage cooperates with the next and the previous, seeking optimization*.

## Time Distributions

During its lifespan within the [**Working Time**](/posts/tpm), the **Stage** should evaluate the following *elapsed time* [frequency distributions](/posts/stats):

- **FreeTime**: Time the Stage is freely available at Facility.
- **AllocationTime**: Time spent allocating Resources from Facility.
- **SetupTime**: Time spent with Stage setup.
- **ReadyTime**: Time the Stage is ready for Production.
- **ReleaseTime**: Time spent decomissioning the Stage.

*WorkingTime = FreeTime + AllocationTime + SetupTime + ReadyTime + ReleaseTime* 

The **ReadyTime**, when the **Stage** is ready for Production, can be split even more:

- **GetWipTime**: Time to gather the necessary **WiP**.
- **ExecTime**: Time the Stage takes to effectively transform the **WiP**.
- **PutWipTime**: Time the Stage takes to put properly the **WiP**.

*ReadyTime = GetWipTime + ExecTime + PutWipTime*  

## Timing

The following diagram represents the timeline including all states:

{{< mermaid >}}
sequenceDiagram
    rect rgb(255, 0, 255, .3)
        ALLOCATION-->>SETUP: AllocationTime
    end
    rect rgb(255, 255, 0, .3)
        SETUP-->>READY: SetupTime
    end

    rect rgb(0, 255, 0, .3)
        READY->>EXEC: GetWipTime
    end
    rect rgb(0, 255, 0, .3)
        EXEC->>WIP: ExecTime
    end
    rect rgb(0, 255, 0, .3)
        WIP->>RELEASE: PutWipTime
    end
    rect rgb(0, 255, 0, .3)
        READY->>RELEASE: ReadyTime
    end
    rect rgb(255, 0, 255, .3)
        RELEASE-->>FREE: ReleaseTime
    end
    rect rgb(0, 0, 255, .3)
        ALLOCATION->>FREE: TotalTime
    end
{{< /mermaid >}}

## Workflow

The diagram below shows the allocation, setup, execution and release phases available for each **Stage**.

{{< mermaid >}}
stateDiagram
    [*] --> ALLOCATION : Cyclo is running
    ALLOCATION --> SETUP
    SETUP --> READY
    READY --> RELEASE
    RELEASE --> [*]
    state ALLOCATION {
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

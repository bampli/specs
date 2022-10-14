---
title: Stage
weight: 9
bookToc: false
---
# Stage

The actual amount of time each **Stage** will require at run time is defined by the **Process**, responsible for the **Cyclo** design, and counting on with support provided by the **Facility**. All timing should be analyzed as [**statistical distributions**](/posts/stats), subject to variations due to existing **common** and **special causes** in the **Process**, according to **SPC** (Statistical Process Control) and [**TPM**](/posts/tpm/) (Total Productive Maintenance) directives.

Before the **Cyclo** can receive the "green" light to execute, each **Stage** should satisfy the necessary **Skills** expected by the **Process**. This is done after all infrastructural and operational **Resources** are provided by the Facility, and the **Stage** can execute its final setup. Then, the **Cyclo** is ready to start processing the **WiP**.

Each **Stage** can be in one of the following states:

- **FREE**: Stage that requires Skills is initialized at Facility.
- **ALLOC**: Stage is allocating Resources from Facility Infrastructure & Operation.
- **SETUP**: Stage with all Skills satisfied, executing final setup for production.
- **READY**: Stage is ready for Production, waiting for the next WiP.
- **EXEC**: Stage is effectively transforming the WiP.
- **WIP**: Stage is putting the WiP towards the next Stage.
- **RELEASE**: Stage is releasing Resources from Facility Infrastructure & Operation.

## Times of Gain (ToG)

The following diagram represents the ToG timeline, including all states:

{{< mermaid >}}
sequenceDiagram
    rect rgb(255, 0, 255, .3)
        ALLOC-->>SETUP: AllocationTime
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
        ALLOC->>FREE: WorkingTime
    end
{{< /mermaid >}}


In its lifespan within the [**Working Time**](/posts/tpm), the **Stage** should elaborate the following *elapsed time* [statistical distributions](/posts/stats):

- **FreeTime**: Time the Stage is freely available at Facility.
- **AllocationTime**: Time spent allocating Resources from Facility.
- **SetupTime**: Time spent with Stage setup.
- **ReadyTime**: Time the Stage is ready for Production.
- **ReleaseTime**: Time spent decomissioning the Stage.

**WorkingTime = FreeTime + AllocationTime + SetupTime + ReadyTime + ReleaseTime**

The **ReadyTime**, when the **Stage** is ready for Production, can be split even more:

- **GetWipTime**: Time to gather the necessary **WiP**.
- **ExecTime**: Time the Stage takes to effectively transform the **WiP**.
- **PutWipTime**: Time the Stage takes to put properly the **WiP**.

**ReadyTime = GetWipTime + ExecTime + PutWipTime**  

Some optimization may prevent unnecessary release/reallocation delays, according to rule five of Deming's **Process** specification: *Each Stage cooperates with the next and the previous, seeking optimization*.

{{< hint info >}}
**Published in [Business Amplifier](https://www.amazon.com/Business-Amplifier-M-Sc-Motta-Lopes/dp/B083XGK14Q), also [e-book](https://www.amazon.com/Business-Amplifier-Jose-Motta-Lopes-ebook-dp-B086L6V6QY/dp/B086L6V6QY/) and [Amplificador de Negócios](https://www.amazon.com/M-Sc-Jose-Motta-Lopes/dp/8592301009).**
{{< /hint >}}

Here is the extracted knowledge from the provided sources, with colloquial language removed and important concepts bolded for clarity:

**1. Multiprocessing Architectures for Real-Time Systems**
*   **Asymmetric Multiprocessing (AMP)**:
    *   Is the normal **state of practice for real-time systems**.
    *   Consists of multiple **CPU cores, each with its own local memory** and a message passing connection.
    *   Each processor runs its **own operating system (OS) instance and application-specific workload**.
    *   This model is simple, resembling a distributed system but with potentially low-latency interconnections.
    *   AMP can be **emulated on Symmetric Multiprocessing (SMP) systems using thread affinity** to disable load balancing and assign threads to specific cores, preventing migration.
    *   AMP is a **safe and well-proven architecture**, recommended unless specific requirements necessitate more complex solutions.
*   **Symmetric Multiprocessing (SMP)**:
    *   Linux is configured for SMP by default.
    *   Features **multiple CPU cores, often with common shared memory** (Uniform Memory Access - UMA, or Non-Uniform Memory Access - NUMA).
    *   **One OS instance manages multiple cores**, typically running on a designated "monarch" core (e.g., core zero).
    *   **Interrupts and tasks can be migrated or load-balanced** across cores, which makes modeling behavior difficult and reduces determinism.
    *   SMP and virtual machine architectures are currently more of a **research topic** in real-time systems than a state of practice.

**2. Real-Time Scheduling Policies and Schedulers**
*   **Priority Preemptive Run-to-Completion Scheduling**:
    *   Is **critical to Rate Monotonic Policy, Theory, and Analysis**.
    *   The **highest priority task or thread in a ready queue is dispatched**.
    *   It **preempts any running task of lower priority**.
    *   If no preemption occurs, a task runs to completion without time slicing.
*   **Linux Schedulers for Real-Time**:
    *   **SCHED_FIFO**:
        *   Best models **priority preemptive run-to-completion** behavior in Linux, similar to RTOS tasks.
        *   Is **unfair and deterministic**, which are desired characteristics for real-time systems.
        *   Tasks run at their assigned priority until completion, explicit yielding, requesting to sleep (transition to delayed state), activating a higher priority task, blocking on a resource (transition to pending/preempted), or an interrupt affects the ready queue.
        *   Is the recommended option for **hard real-time** systems in Linux.
    *   **SCHED_RR**:
        *   Is fixed priority and preemptive but includes **time slicing**.
        *   Is **fair** and has **higher overhead** due to periodic interrupts for scheduling adjustments.
        *   While it may be deterministic, fairness is generally undesired in real-time systems focused on deterministic behavior and higher priority task precedence.
    *   **SCHED_OTHER (Completely Fair Scheduler - CFS)**:
        *   Is the **default scheduler in the Linux kernel**.
        *   Is **fair** and **difficult to model**.
        *   Includes advanced features like "nice" levels and priority decay to prevent CPU hogging.
        *   Is well-suited for **scalable workloads and desktop computing**, but not for deterministic real-time applications.
        *   Typically uses a **10-millisecond time slice (quantum)**, requiring 100 interrupts per second for scheduling adjustments.
        *   Provides progress for all tasks but **lacks predictable response**.
    *   **SCHED_DEADLINE**:
        *   A newer Linux feature, potentially unavailable in all kernel versions or distributions.
        *   Is **adaptive with dynamic priorities**, representing a more advanced real-time concept.
        *   Primarily used for **soft real-time** systems, implementing deadline-driven scheduling.
        *   Is **harder to model** due to its adaptive and dynamic nature.

**3. Real-Time Operating System (RTOS) vs. Linux Real-Time Extensions**
*   **RTOS (e.g., VxWorks)**:
    *   Tasks primarily exist in **ready-to-execute or executing states**.
    *   An executing task runs to completion or is preempted by a higher priority task entering the ready queue (e.g., from an interrupt or semaphore).
    *   Tasks can transition to **pending** (e.g., acquiring a lock) or **delayed** (e.g., calling `taskDelay`). A division by zero can lead to a suspended state.
    *   All RTOS operations are considered to exist in **kernel space**.
*   **Linux with Real-Time Extensions**:
    *   **SCHED_FIFO threads exhibit similar behavior** to RTOS tasks, transitioning between ready and executing states.
    *   They can be preempted, returning to the ready queue.
    *   Transitions to **pending** (e.g., acquiring a lock/binary semaphore) and **delayed** (e.g., `sleep` or `pause`) are also present.
    *   Implemented via the **native POSIX Threads library**, mapping user-space threads to kernel-level tasks.
    *   **SCHED_FIFO threads take priority over all non-real-time threads**.
    *   User-space threads are dispatched from a specific SCHED_FIFO ready queue in kernel space, functionally similar to RTOS schedulers.
    *   Allows dispatching threads with **rate-monotonic policies** within defined priority ranges (RTmax and RTmin).
*   **Comparison and Practical Considerations**:
    *   Linux with RT extensions offers **equivalent scheduling capabilities and control** to RTOS.
    *   Linux typically requires **patches (e.g., RT-Preempt) and careful configuration** for safe real-time use, especially for hard real-time applications.
    *   **Vanilla Linux needs to be "pared down"** by using specific features and avoiding unnecessary ones, while a minimal **RTOS kernel needs to be "built up"** with additional code and libraries.
    *   **RTOS are generally more deterministic**; Linux provides **predictable response**, though deterministic behavior is harder to achieve in user space and more feasible in kernel space.
    *   If all services are implemented in Linux kernel space, an **RTOS may be a more appropriate choice**.

**4. Canonical Service Implementation using State Machines**
*   **Conceptual Model**: Services can be abstractly represented as **state machines**.
    *   They typically progress from a **start state** through **initialization**.
    *   Upon successful initialization, they enter an **online mode** to provide service.
    *   The online mode often involves a **canonical service loop** of **sensing input, executing/processing data, and actuating output**.
    *   Errors lead to an **error state** or **termination**. Services can also undergo a **shutdown** process to go offline.
    *   State machine analysis (e.g., using state transition tables) can be applied for design analysis and completeness.
    *   Implementation can be hardware (e.g., Mealy/Moore state machine for digital logic) or software (e.g., UML extended finite state machine).
*   **Software Implementation Details**:
    *   A software service is typically implemented as a **thread or task**.
    *   Ideally, tasks should **only block when waiting for new sensor input** (e.g., on a request semaphore). Blocking should be avoided during execution or actuation phases.
    *   A common pattern involves a **real-world event** triggering a sensor, which raises an **interrupt**. An **Interrupt Service Routine (ISR)** then performs a **semaphore `give`**. A service task blocks on this semaphore, performs its service upon reception, and then returns to waiting.
    *   **Timeouts** can be implemented if a semaphore is not received, triggering an aliveness check before returning to a waiting state.
    *   **Context switches occur on semaphore `give` operations**, allowing a pending task to transition to the ready queue for dispatch.
    *   The **scheduler itself operates as a state machine**, as do the services it manages.
    *   State machine design for services contributes to **deterministic execution and status**.
*   **Linux Implementation of Sequencers**:
    *   **Software interval timers** (e.g., `itimer.c` via `timer_create` and `timer_settime`) in Linux user space can **emulate hardware interval timers and interrupts** by raising **software signals** (e.g., `SIGALRM`).
    *   These timers can be used to **periodically request services** for generic sequencing.
    *   A **sequencer can be implemented as a signal handler** for such an interval timer, removing the need for `nanosleep` loops and providing more stable and accurate timing.

**5. Rate Monotonic Theory (RMT) Advantages and Pitfalls**
*   **Overview**:
    *   RMT is a **well-established standard of practice** for real-time systems, existing for over 50 years.
    *   Numerous resources support RMT, including IEEE conferences and technical committees, the Real-Time Linux organization, open-source RTOS projects (Zephyr), industry standards (ARINC 653, RTCA), and the Practitioner's Handbook for Real-Time Analysis.
*   **Rate Monotonic Least Upper Bound (RM LUB)**:
    *   Provides an **inexact but sufficient feasibility test**.
    *   If a service set passes the LUB, it is feasible. However, if it fails, it *might still be feasible*.
    *   It is a **simple, order-N calculation** suitable for early design phases or quick online dynamic admission tests.
    *   The LUB always includes a **safety margin**, meaning it can declare feasible sets as infeasible (false negatives) but never incorrectly states an infeasible set as feasible (no false positives). The margin amount is variable.
    *   For `m` services, the LUB asymptotically approaches **~70% utilization (ln 2)**. Specific values are ~83% for two tasks and ~77.98% for three tasks.
*   **Worst-Case Analysis (WCA)**:
    *   Provides an **exact (necessary and sufficient) feasibility test**.
    *   Can be performed **by hand** by simulating the scheduler's behavior.
    *   Automated by tools like **Cheddar**, which implement algorithms such as **scheduling point and completion test** (order N-cubed complexity).
    *   Assumes a **critical instant** where all services simultaneously request the CPU.
    *   Analysis is conducted over the **Least Common Multiple (LCM)** of all periods to fully characterize the schedule and slack time. Analyzing over the longest period is sufficient to determine feasibility.
    *   Exhibits a **deterministic failure mode**: in overloaded scenarios, the lowest priority service misses its deadline first, while higher priority services continue to meet theirs.
    *   **Harmonic service sets** can achieve feasibility **above the RM LUB**, even at **100% CPU utilization (zero margin)**, due to the exactness of WCA. Harmonicity is determined by fundamental frequencies, not just period multiples.
*   **Specific Pitfalls and Workarounds**:
    *   **T=D (Period=Deadline) Limitation**: Addressed by **Deadline Monotonic Theory (DMT)**, now considered a special case of RMT. DMT uses shortest deadline for priority assignment and allows deadlines to be shorter or longer than periods, useful for I/O latency or overlapping requests.
    *   **Secondary/Tertiary Resource Issues**: Resource sharing (e.g., shared memory) is addressed by **priority inheritance or priority ceiling protocol** (detailed in Course 2).
    *   **Importance Encoding**: Solved by **period transform**, which artificially raises a service's priority by assigning it a higher apparent request frequency, thereby creating slack.
    *   **Worst-Case Execution Time (WCET) Variability**: Microprocessor architectural features (e.g., multi-level caches) can introduce variability. Addressed by specialized real-time microprocessors like **ARM R-Series**, which optimize for deterministic timing over average performance.
    *   **Accuracy/Precision/Deterministic Timing Limitations of Software**: If software cannot meet strict requirements, **co-processors (FPGAs, ASICs, GP-GPUs)** can be used for hardware state machine implementations.
    *   **Scalability**: RMT traditionally used AMP (multiple instances of cyclic executives) for scaling. Modern systems emulate AMP on System-on-Chips (SoCs) using thread affinity for predictable behavior on SMP platforms. Research continues on real-time SMP and Virtual Machines.
*   **Dynamic Priority Schedulers (EDF, LLF)**:
    *   **Earliest Deadline First (EDF)**: A dynamic priority, deadline-driven scheduling policy where priority increases as the deadline approaches.
    *   **Least Laxity First (LLF)**: More complex than EDF, considering both time-to-deadline and remaining computation time.
    *   Can schedule some scenarios that RMT fixed priority cannot.
    *   Require **high scheduler overhead** due to constant priority adjustments based on changes in the ready queue or task completion.
    *   Their **failure modes are less obvious and harder to debug** compared to RMT.
    *   **EDF is most commonly used for soft real-time systems** (e.g., digital media) where occasional missed deadlines are tolerable and maximum processor utilization is desired. RMT is generally recommended for hard real-time due to its simpler implementation and deterministic failure modes.

**6. Approaches to Real-Time System Implementation**
*   **Cyclic Executive**:
    *   A **hardcoded, non-preemptive cooperative scheduling approach**.
    *   Historically used for critical systems like space shuttle flight software.
    *   **Advantages**: Custom, efficient, low overhead, purpose-built, ideal for deeply embedded systems.
    *   **Disadvantages**: High development and maintenance costs due to its rigid, hardcoded nature.
*   **Real-Time Operating System (RTOS)**:
    *   Examples include VxWorks, QNX, FreeRTOS, Zephyr, RTEMS.
    *   Lighter-weight than full general-purpose OSs, providing features for **task creation, management, and synchronous/asynchronous data sharing**.
    *   Used in many embedded systems, even those without strict real-time deadlines.
    *   **Advantages**: Medium overhead, quicker time to market, simpler maintenance due to standardized abstractions.
    *   **Disadvantages**: Can involve licensing costs, though open-source options are available. Proprietary RTOS are increasingly becoming legacy solutions, while open-source RTOS gain popularity.
*   **General Purpose Operating System (OS) with Real-Time Extensions**:
    *   Examples include Real-Time Linux (with RT-Preempt patches), Solaris, LynxOS.
    *   Provides a **rich environment for real-time services alongside best-effort applications**, leveraging existing platform features.
    *   **Advantages**: Convenient for **mixed hard/soft real-time and best-effort applications**. The open-source community maintains the kernel, but requires careful configuration and patching to stay current and achieve predictable behavior.
    *   **Disadvantages**: Tends to have the **highest overhead**. Embedded Linux is widely used.
*   **Hardware Solution (No Software)**:
    *   Involves implementing services directly as **hardware state machines** using digital logic design.
    *   Used when software cannot meet stringent accuracy, precision, or deterministic timing requirements. Example: MPEG encoders/decoders implemented as ASICs.

**7. Worst-Case Analysis Hand Diagramming**
*   **Method**: Involves playing the role of the scheduler, dispatching the highest priority task, letting it run to completion or be preempted, and filling in lower priority tasks in available time slots.
*   **Critical Instant**: All services are assumed to request the CPU simultaneously at the beginning of the analysis period.
*   **Analysis Period**: The schedule is analyzed over the **Least Common Multiple (LCM)** of all service periods to fully understand the scheduling behavior and slack time. Analyzing over the longest period is sufficient to determine feasibility.
*   **Schedule Elements**: Includes **preemption** (higher priority interrupting lower), **run-to-completion** (task executing fully without interruption), and **unused (slack) time**.
*   **Comparison to Fair Scheduling**: Rate-monotonic scheduling often succeeds in scheduling service sets (especially harmonic ones at high utilization) where **fair schedulers (e.g., simple round-robin time slicing) would fail** to meet deadlines. Fair schedulers aim for all services to progress, not necessarily meet deadlines.

**8. Cheddar Tool for Automated Analysis**
*   **Purpose**: **Automates worst-case analysis**, providing an alternative to manual hand diagramming.
*   **Utility**: Particularly useful for **larger sets of services** (e.g., 23 services on the Spitzer Space Telescope).
*   **Capabilities**: Allows specification of system details (e.g., multiple CPU cores), and performs analysis for **fixed and dynamic priority scheduling**.
*   **Operation**: Runs simulations out to the LCM of all periods and provides visual analysis of the schedule.
*   **Verification**: Can be used to **check hand-drawn schedules**, and conversely, hand-drawn schedules can verify Cheddar's accuracy.
*   **Accessibility**: It is an **open-source and free tool**.
*   **Algorithms**: Implements various theorems and algorithms, including the **order N-cubed worst-case analysis algorithms** (scheduling point and completion test).
*   **Application**: Valuable for obtaining a generalized check on **feasibility and margin** for diverse service sets and platforms.

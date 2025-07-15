---
layout: post
title:  "Real-Time Embedded Systems Theory and Analysis module 1"
date:   2025-07-01 14:56:51 +0200
categories: jekyll update
---


Here is the knowledge extracted from the sources, with colloquial language removed:

### Syslog for Tracing

*   **Syslog is used for tracing**.
*   To use syslog, the primary requirement is to include `syslog.h`. Other headers like `time.h`, `types.h`, and `unistd.h` may be included for additional logging features.
*   **Timestamps should always be included in every syslog entry**.
    *   Using `gettimeofday` is discouraged; `clock_gettime`, a POSIX real-time feature, is preferred.
    *   A **double-precision floating-point timestamp is recommended for plotting** logged data. This offers 15 digits of precision, providing nine digits for nanoseconds and six for millions of seconds.
    *   Subtracting the start time from the current time can provide an elapsed time.
*   **Logging should use simple tags that are easily searchable (e.g., with `grep`) and include field identifiers separated by spaces**. This format facilitates parsing by tools like MATLAB, Excel, or Gnuplot. Constant delimiters are important for parsing.
*   Process IDs (PIDs) can be outputted in logs; these columns can be ignored or deleted during analysis.
*   Syslog entries are typically found in `/var/log/syslog`.
*   Specific logging formats may be required for automatic grading in educational contexts.

### Rate Monotonic Theory and Analysis

Rate Monotonic Theory is a fundamental concept in real-time embedded systems, focusing on priority assignment and feasibility analysis.

**1. Rate Monotonic Policy**
*   The **Rate Monotonic Priority Assignment Policy assigns the highest priority to the highest frequency service**, which also corresponds to the shortest period service.
*   Services with the same frequency can be assigned the same priority and are dispatched in a First-In-First-Out (FIFO) order from the Ready Queue. Slight frequency adjustments (period transform) can be used to differentiate priorities or create slack time.

**2. Real-Time Service Response Timeline**
*   **Response time** is defined as the duration from a real-world event being sensed until a new real-world event is actuated or I/O completion occurs.
*   Key components affecting response time include:
    *   **Worst Case Execution Time (WCET) / CPU Capacity:** The maximum CPU time required for a service to complete.
    *   **Input/Output (I/O) Latency:** The delay incurred when a service is requested, typically via an interrupt or periodic timer.
    *   **Interference Time:** Time spent waiting due to higher-priority services preempting the current service.
    *   **Dispatch Latency:** The delay in dispatching a service from the Ready Queue.
    *   **Interrupt Service Routine (ISR) Latency and Context Switch Latency:** Critical parameters for evaluating Real-Time Operating Systems (RTOSes).

**3. Assumptions and Constraints (Liu and Layland Paper)**
The original Rate Monotonic Theory is based on several simplifying assumptions and constraints:
*   **Periodic Service Requests:** Services are requested at constant, fixed periods.
*   **Completion Time Less Than Period:** Only one instance of a specific service is outstanding (active) at any given time.
*   **Independent Service Requests:** Services do not have hard-coded, invariant schedules.
*   **Known and Deterministic Runtime:** The Worst Case Execution Time (WCET) for each service is known.
*   **Deadline Equals Period (T=D):** By definition, the deadline for a service instance is assumed to be at the end of its period. This also implies only one instance of a service is active at a time. This constraint can be relaxed with Deadline Monotonic.
*   **Fixed Priorities:** Once assigned, a service's priority remains constant throughout its execution.
*   **Preemptive Services:** Higher-priority services can interrupt and take over the CPU from lower-priority services. This also applies to multicore systems, occurring on each core.
*   **Services Run to Completion:** Once started, a service will run until its computation is finished, unless preempted by a higher-priority service.
*   **No Other Shared Resources:** The CPU is the only resource in contention among services.
*   **Critical Instant:** All services are assumed to request the CPU simultaneously at the worst possible time. This assumes no prior knowledge of service phasing.

**4. Rate Monotonic Least Upper Bound (RM LUB)**
*   The **RM LUB is a mathematical model used to determine the feasibility of a set of services** on a single processor.
*   **Formula:** The sum of the utilization (Capacity C_i / Period T_i) for all 'm' services must be less than or equal to `m * (2^(1/m) - 1)`.
*   **Properties:**
    *   **Pessimistic but Safe:** The RM LUB provides a safe, conservative bound. It may indicate a system is infeasible when it is, in fact, feasible, but it will never falsely indicate feasibility.
    *   **Ease of Computation:** It is an **order 'n' (linear) computation**, making it suitable for quick, "back-of-the-envelope" analysis.
    *   **Not Exact (Sufficient, Not Necessary and Sufficient):** The LUB is a sufficient test, meaning if a system passes the LUB test, it is guaranteed to be feasible. However, it is not necessary and sufficient, as systems can be feasible even if they exceed the LUB.
    *   **Utilization Limits:** For two services (m=2), the LUB is 83%. As the number of services ('m') increases, the LUB asymptotes down to 70%. This margin is attributed to the lack of harmony between service periods.
    *   **Exceeding the LUB:** Systems can be feasible even when their total CPU utilization exceeds the RM LUB, particularly in cases of harmonic services or when slack-stealing techniques are employed.

**5. Worst-Case Analysis (Timing Diagrams)**
*   **Timing diagrams provide an exact method for feasibility analysis** by manually simulating the scheduler's behavior over time.
*   For a complete understanding of CPU usage and free time, the analysis should extend over the **Least Common Multiple (LCM) of all service periods**. However, analysis over the longest period is sufficient for feasibility determination based on the Lehoczky, Sha, and Ding theorem.
*   Rate Monotonic policies result in **deterministic and predictable behavior** in both normal operation and failure modes.
*   Unlike fair schedulers that typically incur a context switch for every time quantum, Rate Monotonic can allow for back-to-back execution of the same service, potentially reducing context switches.

**6. Slack Stealing**
*   **Slack stealing is a technique to utilize unused CPU time** by adding a lower-priority service (a "slack user" or "slack stealer") whose period is set equal to the LCM of the other services.
*   **This technique does not cause higher-priority services to miss their deadlines**, as the slack stealer only uses leftover CPU time.
*   It can enable systems to **achieve 100% CPU utilization** with Rate Monotonic.
*   Slack stealing is an advantage of Rate Monotonic over fair schedulers, as fair schedulers would attempt to execute the slack user by "fairness," potentially causing higher-priority services to miss deadlines.

**7. Harmonic Services**
*   **Harmonic services are those where all frequencies are integer multiples of a fundamental frequency**.
*   Such systems can **achieve 100% CPU utilization** under Rate Monotonic scheduling.

**8. Deterministic Overload Failure Mode of RM**
*   A significant advantage of Rate Monotonic is its **deterministic overload failure mode**.
*   If a service overruns its WCET, it will miss its deadline. However, **all higher-priority services will remain unaffected and continue to meet their deadlines**, while all lower-priority services will also miss their deadlines. This predictability is valuable for designing mission-critical systems.

**9. Extensions and Alternatives**

*   **Deadline Monotonic (DM)**
    *   An extension of Rate Monotonic that addresses scenarios where the **period (T) is not equal to the deadline (D)**.
    *   Under DM, **priority is assigned based on the shortest deadline** (not earliest).
    *   Analysis is similar to RM worst-case analysis, but **success criteria are evaluated against deadline intervals rather than period intervals**.
    *   DM feasibility tests can be inexact (like LUB) or exact (like scheduling point completion tests).

*   **Dynamic Priority Algorithms (Deadline-Driven)**
    *   Examples include **Earliest Deadline First (EDF)** and **Least Laxity First (LLF)**.
    *   **Goal:** These algorithms aim to **achieve 100% CPU utilization**.
    *   **Priority Determination:**
        *   **EDF:** Priorities are based on the **Time To Deadline (TTD)**, with the earliest deadline having the highest priority.
        *   **LLF:** Priorities are based on **Time To Deadline minus Time Remaining to Complete (TTD - TR)**, considered a more sophisticated urgency metric.
    *   **Dynamic Adjustment:** Priorities are recomputed and adjusted whenever there is a change to the Ready Queue (e.g., new requests, completion of a service).
    *   **Advantages:** Dynamic priority algorithms offer greater flexibility and can successfully schedule service sets where fixed-priority RM might fail, especially at high utilization levels above the RM LUB. They prioritize based on real-time urgency.
    *   **Disadvantages:**
        *   **High Overhead:** The constant re-computation and adjustment of priorities introduce significant overhead.
        *   **Nondeterministic Overload Failure Modes:** When overloaded, dynamic priority policies can exhibit **cascading failures** across services, making it difficult to predict which services will fail or debug the system. This contrasts sharply with RM's predictable failure modes.
    *   **Application:** EDF is frequently used for **Soft Real-Time (SRT)** systems, whereas fixed-priority Rate Monotonic is the state of practice for **Hard Real-Time (HRT) mission-critical systems**. Linux includes `SCHED_DEADLINE`, which is an EDF scheduler.

*   **Completion Test / Scheduling Point Test (Exact Feasibility Algorithms)**
    *   These algorithms provide **exact feasibility analysis**, yielding a definitive "feasible" or "not feasible" answer.
    *   They **automate the process of manual hand timing diagram analysis**.
    *   **Computational Complexity:** These algorithms are typically **order n-cubed (polynomial bounded)**, making them more computationally intensive than the linear-time LUB calculation but still manageable for modern computers.
    *   **Purpose:** They are used when system utilization is above the RM LUB, or when a precise determination of feasibility is required beyond the LUB's conservative estimate.
    *   **Theoretical Basis:** They are based on theorems like the Lehoczky, Sha, and Ding theorem (1989) and concepts from "Finding Response Times in Real-Time Systems" (1986).
    *   **Feasibility vs. Safety:** These tests primarily determine feasibility (can it be done?), but safety (is there enough margin?) is a related but distinct concern that still requires engineering judgment.
    *   **Tools:** Tools like Cheddar implement these algorithms and can simulate schedules for verification. Understanding the underlying algorithms is crucial for trusting and verifying such tools.
    *   **Applicability:** Essential for systems with numerous services or very large LCMs where manual analysis is impractical.

**10. General Real-Time System Concepts**
*   **Hard Real-Time (HRT):** Systems where missing a timing constraint leads to critical consequences, such as loss of life, significant property damage, or substantial financial loss.
*   **Soft Real-Time (SRT):** Systems where missing a timing constraint results in a degradation of quality of service, but not catastrophic failure.
*   **Best Effort Service:** A service that attempts to complete its task without any timing guarantees or deadlines.
*   **POSIX Real-Time Extensions:** A set of standards for real-time programming, often used for implementing real-time services and controlling thread affinity to specific CPU cores.
*   **Multicore Systems:** While the original RM theory focused on single-core, its principles extend to multicore environments. Feasibility analysis methods exist for Symmetric Multiprocessing (SMP) and other scalable embedded systems. Asymmetric Multiprocessing (AMP) can emulate multicore by independently analyzing RM systems on multiple processors.

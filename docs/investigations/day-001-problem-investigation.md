SOUTH-CORE — Day 1: Problem Investigation

Date: 2026-09-15
Phase: Problem Investigation
Status: Investigation in progress

---

1. Starting Question

Before writing code or choosing a technology, we asked:

«What real-world problem are we actually trying to solve?»

We deliberately started without deciding that the solution would be a database, operating system, networking system, or any other technology.

The first goal was to understand the problem.

---

2. Environment Investigated

We began by investigating a clinic as a possible real-world environment.

This is an investigation scenario, not yet a decision that clinics are the final target of SOUTH-CORE.

---

3. Where Does Important Information Exist?

A clinic may rely on information stored in different places:

- Paper records
- Local computer storage
- Remote/server systems

A screen is not the information itself. It is a way of accessing and displaying information.

A simplified model:

REAL WORLD
    |
    +-- Paper records
    |
    +-- Local computer
    |       |
    |       +-- SSD/HDD
    |
    +-- Remote system
            |
            +-- Server

This led to an important distinction:

«Information can still exist while the ability to access it is unavailable.»

---

4. Why Are Records Valuable?

A record preserves knowledge about something that happened in the real world.

That knowledge can support:

1. Decision-making
2. Actions
3. Organisation
4. Service delivery

A simplified chain is:

Information
    ↓
Knowledge about reality
    ↓
Decision
    ↓
Action
    ↓
Service

Therefore, losing access to important information can affect more than just the computer system.

---

5. Investigating a Power Outage

We then investigated what happens when electricity becomes unavailable.

An important correction was made during the investigation:

«A power outage does not automatically mean that information stored on an SSD/HDD has been destroyed.»

Instead, the computer system used to access that information may become unavailable.

Patient record
      ↓
Storage
      ↓
Computer
      ↓
Application
      ↓
Screen

During a power outage:

POWER OFF
    ↓
Computer stops operating
    ↓
Application stops
    ↓
Normal digital access becomes unavailable

This introduced two different concepts:

Persistence

Does the information still exist?

Availability

Can the information be accessed when it is needed?

These are not the same problem.

---

6. What Happens When Previous Information Is Unavailable?

We considered a situation where a patient's previous history is not immediately available.

For example, previous information may have contained knowledge about an earlier condition or treatment.

If that information cannot be accessed, staff may need to reconstruct information by asking questions or using other available sources.

The important engineering observation is:

Previous information unavailable
        ↓
Less information available
        ↓
More investigation required
        ↓
More time required
        ↓
Decision becomes harder/slower
        ↓
Action may be delayed

We deliberately did not assume that an incorrect treatment decision would definitely occur.

That would require real-world evidence.

---

7. Existing Fallbacks

We investigated possible fallback mechanisms.

Examples include:

- Paper records
- Laptops with battery power
- Generators

However, a backup mechanism is not necessarily unlimited.

For example:

Laptop
   ↓
Battery
   ↓
Eventually runs out

And:

Generator
   ↓
Requires fuel
   ↓
Requires money
   ↓
May require time to start

Therefore, the existence of a fallback does not automatically mean that normal operation is maintained.

---

8. Degraded Operation

An important discovery was that the system does not necessarily go from:

WORKING → COMPLETELY STOPPED

There can be an intermediate state:

NORMAL OPERATION
       ↓
DIGITAL SYSTEM UNAVAILABLE
       ↓
FALLBACK / MANUAL PROCESS
       ↓
DEGRADED OPERATION

A clinic may still perform some work using paper or other available resources, but tasks such as searching, retrieving, and updating information may require more manual effort.

This means the problem may be about reduced capacity, not simply total shutdown.

---

9. Information Retrieval

We focused specifically on searching for information.

An early assumption was that a nurse might need to inspect huge numbers of paper records.

We corrected this assumption.

Paper records may already be organised using things such as:

- Patient numbers
- Names
- Dates
- Shelves
- Folders

Therefore, the real engineering question is:

«How much work and time does it actually take to locate the required information when the normal digital search capability is unavailable?»

This needs to be measured rather than guessed.

---

10. Time and Capacity

We used a hypothetical example to understand the relationship between search time and capacity.

Suppose:

- Digital search takes 30 seconds per patient.
- Manual search takes 10 minutes per patient.
- 20 patients require their records.

Manual searching would require:

20 × 10 minutes
= 200 minutes
= 3 hours 20 minutes

The point of this example is not to claim that these are real clinic measurements.

The point is to understand the relationship:

More work per patient
        ↓
More time per patient
        ↓
Fewer patients processed in the same period
        ↓
Reduced capacity
        ↓
Potential delays

This led to an important insight:

«An outage does not necessarily destroy the ability to work. It can reduce the amount of work that can be completed within a fixed period.»

---

11. Current Problem Model

Our current model is:

REAL-WORLD EVENT
       ↓
Electricity unavailable
       ↓
Computer system unavailable
       ↓
Important information becomes inaccessible
       ↓
Fallback/manual process used
       ↓
Tasks take longer
       ↓
Patient processing slows
       ↓
Waiting increases
       ↓
Clinic capacity decreases
       ↓
Some work may be delayed

This is currently a problem hypothesis, not a proven final problem definition.

---

12. Concepts Identified

During Day 1 we identified several engineering concepts:

- Information availability
- Information persistence
- Information retrieval
- Delay
- Capacity
- Service continuity
- Fallback mechanisms
- Degraded operation

These concepts will be investigated further before designing a solution.

---

13. What We Have NOT Decided

At the end of Day 1, we have intentionally not decided:

- The final problem SOUTH-CORE will solve
- That clinics are definitely the target
- That a database is the solution
- That a B+Tree is required
- That a write-ahead log is required
- That networking is required
- That Qt is required
- That we need to build an operating system

Those are solution/design decisions.

We are not making them before understanding the problem.

---

14. Engineering Principle

SOUTH-CORE follows this process:

UNDERSTAND
    ↓
BUILD
    ↓
BREAK
    ↓
FIX
    ↓
PROVE
    ↓
COMMIT

Day 1 is currently in the UNDERSTAND stage.

---

15. What Remains Unknown

We still need evidence about:

- How often these disruptions actually occur
- How long they typically last
- Which information becomes unavailable
- How clinics currently operate during disruptions
- How effective existing fallback procedures are
- How much additional time manual processes require
- Which services are most affected
- Whether the problem is significant enough to justify engineering a new system

These questions must be investigated before committing to a solution.

---

16. Day 1 Conclusion

The investigation has identified a possible relationship between:

power/infrastructure disruption → information unavailability → slower manual work → reduced operational capacity.

However, the problem has not yet been proven.

The next investigation will examine what happens when disruption occurs repeatedly rather than as a one-time event.

«Problem first. Solution later.»

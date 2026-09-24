Day 03 — Unfinished Work Capability

1. Where This Investigation Came From

Day 01 investigated the importance of information and what happens when important information becomes inaccessible.

Day 02 investigated what can happen when the disruption is repeated.

The investigation identified this chain:

Information becomes inaccessible
        ↓
Normal processing is disrupted
        ↓
Fallback/manual processes may take longer
        ↓
Processing capacity decreases
        ↓
Some work remains unfinished
        ↓
Backlog increases

The clinic was used as an investigation environment to understand this problem. The clinic is not the final target of SOUTH-CORE.

The underlying problem is broader:

«When normal access to important information is disrupted, work can remain unfinished and accumulate as backlog.»

---

2. Why SOUTH-CORE Must Remember Unfinished Work

If work is unfinished, it cannot simply disappear when the current operating period ends.

For example:

Today:

W1 → W2 → W3 → W4

W1 and W2 are completed.

W3 and W4 remain unfinished.

The system therefore needs to preserve knowledge that:

W3 = unfinished
W4 = unfinished

When normal operation resumes, the organisation can continue from the work that remains.

Without this information, people may have to reconstruct what was left unfinished.

Therefore, the first capability identified for SOUTH-CORE is:

«SOUTH-CORE must preserve information about unfinished work so that work can continue after disruption.»

This does not solve the entire information-access problem.

It solves one concrete consequence of that problem:

«Loss of continuity of unfinished work.»

---

3. Why We Started With Unfinished Work

The original investigation was about information availability and accessibility.

We did not suddenly decide to build a queue because a queue is a useful data structure.

The reasoning was:

Information becomes inaccessible
        ↓
Processing becomes harder/slower
        ↓
Capacity decreases
        ↓
Some work remains unfinished
        ↓
Backlog exists
        ↓
The unfinished work must remain known
        ↓
First small SOUTH-CORE capability

Therefore, remembering unfinished work is directly connected to the original problem investigation.

It is the first small part of the larger problem that we can build, test, break, and improve.

---

4. Work Item

The investigation already established the concept of a general Work Item.

A Work Item represents one identifiable piece of work that needs to be completed.

The clinic is only an example environment.

The concept is intentionally general so that SOUTH-CORE is not designed specifically around patients or clinics.

A Work Item has a stable identity.

Its identity does not change simply because its state changes.

Example:

Work Item 07

can move through different states while remaining Work Item 07.

---

5. Work Item State

The previously established lifecycle is:

WAITING
   ↓
IN PROGRESS
   ↓
COMPLETED

For the current capability, unfinished work consists of:

WAITING
IN PROGRESS

"COMPLETED" is no longer unfinished work.

Therefore, if a disruption occurs while work is unfinished, SOUTH-CORE must preserve enough information to know the Work Item and its unfinished state.

Example:

W17 → WAITING
W18 → IN PROGRESS
W19 → WAITING

After recovery, the system should still be able to identify:

W17 → WAITING
W18 → IN PROGRESS
W19 → WAITING

The purpose is continuity.

---

6. Queue Design Was Not Finalized

During the design discussion, we explored the idea of representing processing order:

W1 → W2 → W3 → W4

We identified that a real-world line normally joins at the back and that the front represents the next work to be processed.

However, this was deliberately not finalized as a C++ queue, linked list, or pointer-based structure.

A later question about potentially millions of Work Items showed that we should not choose a data structure before establishing exactly what information SOUTH-CORE needs to preserve.

Therefore:

Queue design = NOT YET FINAL

No implementation decision was made from this exploration.

---

7. Design Principle

Day 03 reinforced an important SOUTH-CORE engineering principle:

«Do not represent information merely because it exists in the real world. Represent information because SOUTH-CORE has a responsibility that requires it.»

The same principle applies to implementation.

We will not choose a data structure because it sounds appropriate.

We will first establish the required information and relationships, then choose the smallest suitable representation.

---

8. First Testable Capability

The first capability is now defined as:

«Preserve unfinished Work Items and their unfinished state across a disruption.»

Conceptually:

Create Work Items
        ↓
Work remains unfinished
        ↓
Disruption
        ↓
Normal operation stops
        ↓
Recovery
        ↓
Unfinished Work Items are still known
        ↓
Work can continue

The first implementation should be deliberately small.

It should not attempt to solve the entire SOUTH-CORE vision.

---

9. What Has Not Been Built Yet

At the end of Day 03, the following have not been implemented:

- database
- B+Tree
- WAL
- networking
- synchronization
- Qt interface
- distributed system
- final queue structure
- large-scale architecture

These remain future possibilities only if later requirements and experiments justify them.

---

10. Day 03 Conclusion

The first small capability of SOUTH-CORE has been justified from the original problem investigation.

The reasoning is:

Information access disruption
        ↓
Reduced processing capacity
        ↓
Unfinished work
        ↓
Backlog
        ↓
Need to preserve unfinished work
        ↓
SOUTH-CORE capability:
REMEMBER UNFINISHED WORK

The next step is not to design the entire system.

The next step is to turn this capability into the smallest working implementation, test it, deliberately break it, fix it, and improve it.

«Problem first.
Small capability second.
Code after understanding.»

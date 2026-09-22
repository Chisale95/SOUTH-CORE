# Day 2 — Backlog Investigation

## Question

What happens when disruption happens repeatedly rather than only once?

## Investigation

A single disruption can reduce the amount of work completed during that period.

Repeated disruptions introduce another possibility: unfinished work can accumulate.

Consider a simple example:

- 4 pieces of work arrive during a 30-minute disruption.
- Only 1 can be completed.
- 3 remain unfinished.
- The system returns to normal operation.
- New work continues to arrive.

The system is therefore not starting from zero after the disruption.

It must deal with:

1. unfinished work from before;
2. new incoming work.

## Backlog

We call unfinished work that remains to be processed a backlog.

A simple model is:

Backlog(next) = Backlog(current) + Arrivals - Completed

This shows that completing work does not automatically mean that backlog is decreasing.

If:

Completed > Arrivals

the backlog can decrease.

If:

Completed = Arrivals

the backlog can remain stable.

If:

Completed < Arrivals

the backlog can grow.

## Important distinction

Work being completed is not the same as backlog being cleared.

A system can continue completing work while its backlog continues to grow if new work arrives faster than work can be completed.

## Current problem model

Disruption

↓

Digital information becomes unavailable

↓

Fallback/manual process is used

↓

More time may be required

↓

Processing capacity decreases

↓

Some work remains unfinished

↓

Backlog forms

↓

New work continues to arrive

↓

The system must process both existing and new work

## Current problem statement

When access to important digital information is repeatedly disrupted, the system may be forced into slower fallback processes. Reduced processing capacity can leave work unfinished, and if incoming work continues to exceed the system's ability to process it, unfinished work can accumulate into a growing backlog.

## Unknowns

This investigation does not yet establish:

- how frequently disruptions occur;
- how long they last;
- how much processing capacity is actually lost;
- how much work normally arrives;
- how much work can normally be completed;
- how real organisations currently manage accumulated work;
- whether the clinic scenario represents the final target environment.

These require further investigation and evidence.

## Design boundary

No software solution is selected from this investigation.

The purpose of this checkpoint is to understand the problem before designing the system.

Problem first. Solution later.

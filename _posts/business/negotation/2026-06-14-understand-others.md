---
title: Negotiation Case Study -- Better Versioning Strategy Across Teams
date: 2026-06-14 11:32:25
tags: [negotiation, communication, business]
categories: business
---

## Context

The root problem was a version control design issue introduced by a partner team.

They designed a versioning system using multiple boolean flags, where each flag represented a different version. However, these flags were **not mutually exclusive**, meaning multiple versions could be enabled simultaneously through live experiments.

As a result, conflicting versions could coexist, leading to **non-deterministic loading behavior** during production experiments. This made debugging and reasoning about system behavior difficult.

We proposed replacing the multiple boolean flags with a **single string flag** to explicitly specify the active version. This would eliminate ambiguity and make behavior deterministic.

However, the partner team raised a valid concern: a string flag could allow arbitrary values, making it easier for users to accidentally configure unsupported versions.

## What Worked During the Negotiation

### 1. Listen to the Other Team’s Concerns and Adapt the Proposal

Instead of repeatedly pushing our original solution, we took time to understand the partner team’s concerns.

During the discussion, one manager proposed a compromise: introduce a **string disambiguation flag** that is only used when conflicts occur.

The proposed logic worked as follows:

* Multiple boolean version flags remain supported.
* If conflicts occur, the disambiguation flag is checked.
* If the flag points to a valid version that is already enabled by a corresponding boolean flag, that version is selected.
* Otherwise, the system falls back to a default conflict-resolution strategy.

This solution was not our original proposal, but it addressed the partner team’s concerns while improving determinism in conflict resolution.

### 2. Document Every Option Early

When multiple stakeholders are proposing different solutions, discussions can quickly become hard to track.

Creating a shared document early helped:

* Capture every proposal and tradeoff
* Prevent misunderstandings
* Make disagreements explicit
* Keep everyone aligned on decision criteria

With AI tools, documenting discussions and summarizing tradeoffs has become much easier and lower effort than before.

### 3. Bring the Right Decision Makers Into the Room

Technical discussions can stall if the actual stakeholders are not involved.

Setting up a meeting with the relevant stakeholders — especially the true decision makers — helped move the discussion forward and clarify priorities.

## What Didn’t Work

### 1. Getting Frustrated Before Fully Understanding the Other Side

At times, emotions got in the way.

Reacting too quickly without fully understanding the other team’s reasoning made the discussion less productive.

A better approach is to first clarify:

* What problem are they actually optimizing for?
* What risks are they worried about?
* Which constraints are non-negotiable?

In cross-team negotiations, listening carefully often leads to better compromises than simply defending the original proposal.

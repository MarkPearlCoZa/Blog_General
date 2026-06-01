---
layout: post
title: Fan Out Work - Understanding the Risks and High Level Strategies for Prevention
tags: 
category: General
---
I read a post by Jade Rubick that introduced the concept of fan out work. It immediately resonated with challenges I’ve observed at my current employer, where significant friction arises when one team’s changes or work creates extra work for many other teams.

## What Is Fan Out Work?

Fan-out work occurs when a single team or engineers work “fans out” to multiple other teams. For example, an engineer might make a breaking change to an API, believing it will save time. They then ask all other teams to modify their code accordingly to use the changed API signature. While this might be efficient for the originating team/engineer, it can create a domino effect of work across the organization, leading to many hours of unplanned effort and overwhelmed teams pulled between competing demands. 

Multiple requests, each seemingly minor, can strain a team and organisations capacity, causing frustration and disruption.

## Sources of Fan Out Work

While we’ve used the example above of an API change, it’s important to note that fan-out work can arise from many other sources. Security updates, such as patching critical vulnerabilities, may require coordinated changes across several systems and are triggered by Security. Similarly, compliance work, such as adhering to new data protection regulations like SOC or PCI, often involves widespread updates to ensure consistency and alignment. In each case, the ripple effect of such work highlights the importance of assessing and minimizing the impact on downstream teams.

Platform Teams Pose a High Risk of Causing Fan Out work
Platform teams frequently risk triggering fan-out work by introducing:

Technical migrations (e.g., mandating framework upgrades)

Pattern changes to pipelines, tooling, etc

These changes can quickly ripple through numerous dependent systems, forcing a significant number of teams to perform unplanned work.

The Core Problem: Missing Context
The team or engineer initiating fan-out work does not understand the workloads, priorities, or capacity of other teams they are requesting to do the work. What may seem like a minor adjustment can become a significant burden when multiplied across teams that already have full backlogs and are under pressure. 

The team or engineer being asked to do the work does not understand how this work competes with their team's priorities; thus, they have little space to negotiate trade-offs or make priority calls, leading to rushed work, outright burnout or severe frustration.

When fan out work comes from multiple sources - Platform, Security, etc - prioritising and determining what is most important becomes infinitely harder.

## How to Address Fan Out Work

### Where possible, require the Originating Team/Engineer to Own and Do the Work

If a team mandates a migration, it should handle the changes in the dependent teams’ codebases. This ensures the full cost of a decision is experienced by the team or engineer making the request, creating a natural feedback loop. 

### Obtain Senior Leadership Approval

Before initiating fan-out work requests that could impact multiple teams or streams, it is essential to obtain support from the senior leadership overseeing each affected stream. This process ensures proper prioritization of requests, minimizes conflicting demands, and promotes organizational alignment.

### Decouple Changes to Fit Local Timelines

Allow each team required to do the work to incorporate fan-out changes according to their own schedule and priorities. Indicate preferred timelines for the work to be accomplished by but make it clear that this is not a mandate and if a team needs more time than that they can /should let you know. This minimizes disruption and empowers local decision-making, helping teams balance new demands against existing commitments.

Conclusion
By recognizing and proactively managing fan-out work, we can reduce frustration, avoid overwhelming teams, and maintain a healthier, more collaborative work environment.

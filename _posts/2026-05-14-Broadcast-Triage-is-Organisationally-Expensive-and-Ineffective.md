---
layout: post
title: Broadcast Triage is Organisationally Expensive and Ineffective
tags: 
category: General
---
As organisations grow, one of the most common operational failure modes is broadcast triage — where work or issues are sent broadly to many teams with the expectation that ownership will self-organise. This is a classic example of diffuse accountability.

## What is Diffuse Accountability?

Diffuse accountability is when responsibility is spread broadly across groups of people or teams, but nobody is explicitly accountable for ensuring the outcome happens and ownership of the responsibility is unclear.

One way to identify it is if you see statements like:

* “Someone needs to look at it.”
* “Please review the list and identify any items that belong to your team.”
* “Each team should review and do X.”

These statements come across as collaborative and inclusive but in reality, they create ambiguity and are rarely actioned.

## Broadcast Triage Is Often Organisationally Expensive

Broadcast triage is when a long list of issues is sent to a broad audience with messaging such as:

“Please review the list and identify any items that belong to your team.”

In practice, this approach creates two major problems.

### The “Someone Else Will Do It First” Effect

When the list is large and sent broadly, individuals naturally assume:

* someone else will probably review it first,  
* someone closer to the issue will identify the ownership,  
* or the list will become smaller and more actionable later.  

This creates passive waiting behaviour. The larger the audience and the larger the list, the stronger this effect becomes. Everyone delays engagement because the coordination burden feels high relative to their immediate ownership clarity.

This does not always happen. High-severity incidents where the immmediate impact on the organization is clear like.. outages or urgent escalations often create immediate engagement regardless of ownership ambiguity because leadership immediately rallys to identify owners.

But for large operational backlogs, security findings, technical debt, or cross-team remediation work, the probability of delayed action increases significantly when ownership is unclear because the immediate impact on the business is low.

As a result, important work can sit untouched despite being visible to many teams and leaders.

### Multiplication of Organisational Effort

There is also a less obvious scaling problem:
broadcast triage duplicates effort across the organisation.

For example:

* 30 teams,
* each reviewing a list of 40 issues,
* means the organisation may effectively perform hundreds or thousands of ownership evaluations independently.

- Most of that effort is repetitive. Many teams will review the same items only to conclude:

“This probably does not belong to us.”

From an organisational efficiency perspective, this is extremely expensive.

A request that takes:

“just 10 minutes per team” can quickly translate into many hours of duplicated organisational effort.

Some duplication is healthy and even necessary. Overlap can help identify hidden impacts, validate assumptions, and improve resilience.

The issue is not duplication itself.

The issue is unstructured duplication at scale without clear coordination accountability = extremely expensive.

## Diffuse Accountability Is Often Invisible

One of the dangerous aspects of diffuse accountability is that it can look productive on the surface.

There are meetings.
There are emails.
There are Jira tickets.
There are Slack discussions.
There are people agreeing the work matters.

Yet nothing moves.

This creates a category of organisational dead zone:
important work that everybody acknowledges, but nobody operationally drives.

Security remediation is a common example.

An email goes to a broad distribution list:

“Relevant teams should review these findings and take ownership.”

The assumption is that affected teams will self-identify and act.

But in practice:

* Teams assume another team is more appropriate.
* Teams do not know whether they are expected to lead or contribute.
* Teams deprioritise the work because nobody explicitly assigned it.
* Teams wait for clarification that never comes.

The issue remains “unassigned” while everybody believes somebody else is probably handling it.

Why This Gets Worse as Organisations Scale

Small teams can often survive ambiguous ownership because context is shared socially.

People sit near each other.
Communication loops are short.
Gaps are obvious.
Social pressure fills operational cracks.

Large organisations do not work that way.

At scale:

* Communication becomes asynchronous.
* Teams optimise locally.
* Leaders cannot manually coordinate everything.
* Ownership boundaries become specialised.
* Dependencies increase.

Diffuse accountability compounds with scale because ambiguity multiplies across teams and systems.

A process that works for 10 engineers often breaks at 300.

Shared Responsibility Is Not the Same as Shared Accountability

This is an important distinction.

Shared responsibility can work extremely well.

Many teams can contribute to an outcome:

* Security teams define standards.
* Platform teams provide tooling.
* Product teams remediate vulnerabilities.
* Infrastructure teams support rollout.

That is healthy collaboration.

But accountability should remain explicit.

There should still be a clearly identified owner for:

* triage,
* coordination,
* escalation,
* tracking,
* and ensuring completion.

Good organisations distribute contribution while maintaining clarity of accountability.

## This Does Not Mean Centralise Everything

One possible reaction to this argument is:

“Fine, then one central team should own all triage.”

That approach can fail too.

Centralised coordination models can become:

* bottlenecks,
* overloaded queues,
* single points of failure,
* or disconnected from domain expertise.

The goal is not rigid centralisation.  The goal is intentional accountability design.

That might mean:

* a central triage function,
* a rotating ownership model,
* service ownership metadata,
* platform coordination,
* delegated ownership structures,
* or temporary accountable owners until reassignment occurs.

The important thing is that the organisation has a deliberate mechanism for resolving ambiguity, rather than relying on broad, voluntary self-selection at scale.

## Broad Visibility Still Matters

There are situations where broad visibility and open review are valuable.

Sometimes ownership genuinely is unclear.
Sometimes hidden dependencies only emerge through wider review.
Sometimes teams should proactively identify and take ownership of problems.

Healthy engineering cultures absolutely benefit from proactive ownership behaviour.

The problem arises when organisational systems rely primarily on mass voluntary ownership discovery as the default operating model.

That model becomes increasingly unreliable as organisations grow.

## The Hidden Costs

Diffuse accountability creates more than operational inconvenience.

It creates systemic drag:

* slower execution,
* duplicated work,
* decision paralysis,
* unresolved risks,
* coordination overhead,
* and organisational frustration.

Over time, people lose confidence in processes because they observe that issues disappear into ambiguity.

This often leads to a secondary failure mode:
people creating shadow ownership structures informally just to get things done.

## Better Patterns

Avoiding diffuse accountability does not require heavy process.

Usually, it requires clearer defaults.

Examples:

* Always assign an initial owner, even if ownership may later move.
* Define explicit triage ownership.
* Create clear escalation paths for ambiguous ownership.
* Default unresolved ownership to a coordinating team.
* Ensure every important initiative has one accountable lead.

A simple principle is:

Multiple teams may contribute, but accountability should remain singular and explicit.

## The Problem with “Everyone Owns It”

When everyone owns something, nobody truly owns it.

That does not mean people are avoiding responsibility intentionally. In most cases, the opposite is true. People are trying to be helpful, respectful of boundaries, and collaborative.

But larger organisations introduce a scaling problem:

* Teams have incomplete context.
* Ownership boundaries become fuzzy.
* Communication becomes broadcast-oriented.
* Priorities compete constantly.

In that environment, broad responsibility creates uncertainty:

* Who is expected to act?
* Who decides priority?
* Who follows up?
* Who escalates if nothing happens?
* Who is accountable if the issue remains unresolved?

Without clear answers, work quietly stalls or is ignored.

## Final Thought


Collaboration is valuable. But collaboration should increase contribution, not dilute accountability.
The larger an organisation becomes, the more important this distinction is.

Because in complex systems, ambiguity does not remain neutral.

It accumulates.

And eventually, it becomes operational friction that slows the entire organisation down.


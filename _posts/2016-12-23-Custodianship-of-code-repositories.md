---
layout: post
title: Custodianship of code repositories
tags: 
category: Process
---

It’s a two way street
Sirius is contributing to Ledger Service(Bumblenauts).
Sales and Billing is contributing to Ledger Service (Bumblenauts).
Dagobah will be contributing to Contact Service (Sirius).
 
We are beginning to experience the new Custodianship model first hand, and I think we can lead the way in this to help other teams at MYOB be successful in this approach too.  Here are some ideas/thoughts I have had. ..
 
We need both sides to be empathetic.
Custodians will naturally be biased towards their way of doing things, and this may result in conflict when someone makes a pull request.  So when you are involved in this process please take a minute to put yourself in the other sides shoes, and be empathetic.
 
Custodian
·         Expects design and vision to be maintained.
·         Expects code quality to remain the same or even improve.
·         Probably busy when pull requests are made so may not be able to process them within the hour.  We may need an SLA - eg 24 or 48 hours.
·         Expects not to be surprised by big changes that have not been discussed.
 
Contributor
·         Expects some help as the may not be familiar with design, code and expectations.
·         Expects pull requests to be processed quickly, but should also acknowledge that the Custodians may be busy and can't do it immediately.
·         Does not want to be hindered by a process.
 
Guidelines
·         Every change should be managed by a pull request no matter how small.  If we allow direct pushes to occur this may be used to get changes in quickly.
·         Should have SLA around pull requests.  A week is probably good enough.  24 or 48 hours?
·         We should NOT rely on the pull to be processed to be able to run some tests.
·         We need to acknowledge that this process will incur some cost on both sides.  So we can either go for big bang costs at the end of the process (ie. A big pull request), or we can make small investments from the start that will pay off when the pull request is made.  I think the latter is the better approach. So this means:
o    Get the custodian involved early in inception phase.
o    Get designs and changes reviewed by Custodian
o    BA & QA need to collaborate as well this is not just a Dev thing.
o    Both teams need to factor this time in - I think it will pay off in the end when the pull requests are processed as there will be no suprises, and all expectations will have been met.

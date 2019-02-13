---
layout: post
title:  "Internalized Tensions of Software"
date:   2014-02-18 22:27:00 -0800
categories: software
---
Software developed in a for-profit environment is subject to two contradictory
demands:

- _Use-demand:_ On the one hand, it must be useful, maintainable, and
  effectively meet customer needs.
- _Value-demand:_ On the other hand, it must deliver value (for example,
  profits) in as timely a fashion as possible, be subject to estimation, and
  help balance opportunity cost.

It is easy to see how these tensions come into conflict.
For example, to make a piece of software maintainable may require a refactor whose exact timescale
escapes effective estimation.
Similarly, delivery so as not to incur opportunity
costs may require reducing maintainability or even incurring the cost of rework.

Within an organization the overemphasis of either pole of this tension can
produce a crisis.
If use-demand is overemphaiszed the result is perfectionism and a low rate of valuable output.
The details are constantly being reworked.
If sustained long enough the organization starves from its own inability to produce
valuable output.
If value-demand is overemphasized the result is typically low quality software mired in bugs and technical debt.
These projects eventually become trapped in firefighting, missed milestones, and inevitably have to be rewritten from scratch or heavily refactored.

The choice of software development process or methodology does not abolish these
conflicts, but rather provides the form within which they have room to move.
"This is, in general, the way in which real contradictions are resolved.
For instance, it is a contradiction to depict one body as constantly falling towards
another and at the same time flying away from it.
The ellipse is a form of motion within which this contradiction is both realized and resolved" [^1]

The above framework should allow us to illuminate some of the reasons for the failure of traditional methodologies.
Let's take, for example, the waterfall method.
This method attempts to use the kind of upfront, linear, unidirectional planning typically found in industrial manufacture.
The software is designed, built, debugged, and then shipped.
The problem, of course, is that it tries to cram use-demand into the framework required by value-demand.
This necessarily implies that the balancing required to address use-demand is always deferred until some later phase.
Slow feedback means limited responsiveness and thus success of every later phase is predestined by the quality of work and omniscience of the parties involved in the earlier phases.
The demands are here confusedly, almost nonsensically mediated.
Agile methods do better by explicitly acknowledging the need for mediation between the two demands.
The ruin of agile is typically due to partial adoption - having a morning scrum without developer involved sprint planning, a global task backlog, roadmap, and end of sprint postmortems.
The morning scrum in such a scenario then merely serves as a morning status check (bordering on micromanagement), and the feedback and mediation points have been completely removed.
These sorts of imbalances are the source of tremendous waste in the software industry.

When not viewed as mediators of internal tensions it is all too easy for processes to devolve into their ineffective alternatives.
As developers and team leaders we need to be aware of how we are striking this balance and whether or
not it is healthy for the project.
Writing the software itself is usually not the hardest part of the software lifecycle.
Instead, it is finding a company disciplined enough to perform the balancing act required consistently.

---

[^1]: Karl Marx, "Capital: Volume 1"

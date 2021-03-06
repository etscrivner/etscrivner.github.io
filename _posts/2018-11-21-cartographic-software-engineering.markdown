---
layout: post
title:  "Cartographic Software Engineering"
date:   2018-11-21 11:54:00 -0800
categories: software
---
> "The utility of geography in matters of small concern, also, is quite evident; for instance, in hunting. A hunter will be more successful in the chase if he knows the character and extent of the forest; and after, only one who knows a region can advantageously pitch camp there, or set an ambush, or direct a march. The utility of geography is more conspicuous, however, in great undertakings, in proportion as the prizes of knowledge and the disasters that result from ignorance are greater."

Strabo, _"Geographica"_

### Introduction

Imagine, for once, that we chose to treat the software we produced not as a mental representation actualized, a blueprint constructed, or a sculpture refactored to perfection.
Suppose, rather, that we chose to treat it as an [ecumene](https://en.wikipedia.org/wiki/Ecumene) - a habitable world, a territory organized atop a wilder underlying landscape.

<img src="/assets/images/cartographic-software-engineering.jpg" width="450" style="float: right; padding: 1em"/>

Our software, then, would be the small village that arose first by laboriously clearing and driving back the wild forest.
Whose buildings and fortifications were constructed - with varying levels of mastery - from the ready materials of that environment and whatever tools and techniques were brought along by its engineers, artisans, and craftsmen.
A small piece of organized space in a wild and disorganized environment.

The terrain - all those strata we build on top of: hardware, operating systems, networks, languages, libraries, cloud platforms, and web APIs - would be subject to phenomena at various time scales: weather, seasons, wars, socio-political phase changes, and plate tectonics.

The experience provided by construction itself would lead to improvements in tools and techniques as well as the creation of novel tools and techniques.
A local culture would arise: cuisine, language, style, routines.
Such local culture makes every mature codebase recognizable as [sui generis](https://en.wikipedia.org/wiki/Sui_generis).

How would our methods change if we thought of our software this way?
We would think of our services as villages, towns, cities, and countries.
We would think of our dependencies as geological strata, environments, and local ecologies.
The impact of such a change in thinking is not immediately obvious to those of us schooled in modern methods of software engineering.

I posit that this would mean for us to take seriously the idea of a software geography, and especially to take seriously that idea by which geographers most immediately master and navigate a territory - cartography.
Let us then sketch the first outlines of a *software cartography*.

# Viewpoint Construction as Primary Art

It is an underappreciated fact that software systems are incapable of singular abstract representation.
No single image or document could ever fully capture a piece of software.
Instead, every piece of software must be represented at multiple levels of abstraction and points-of-view simultaneously - machine level, programming language level, UI level, system diagram level, executive summary level, business strategy level.
For this very reason, the [IEEE 42010 standard](https://en.wikipedia.org/wiki/ISO/IEC_42010) chooses to emphasize the use of views and viewpoints over any single technique for describing a piece of software.
This recognizes that the adequate description of a single software component may require a [system diagram view](https://en.wikipedia.org/wiki/System_context_diagram), a [class diagram view](https://en.wikipedia.org/wiki/Class_diagram), a [state-machine view](https://en.wikipedia.org/wiki/Finite-state_machine), and a logic specification view (of which I could find no good Googleable examples, but you can learn more ([from this book](https://www.amazon.com/PSP-Self-Improvement-Process-Software-Engineers/dp/0321305493/ref=sr_1_2?ie=UTF8&qid=1518669892&sr=8-2) [^1]) - none of which is adequate by itself to describe the complete component.

<img src="/assets/images/ancient-skies.png" width="350" style="float:left; padding: 1em" />

Much like a map, which can be constructed at the level of a continent, a country, a province, a building, etc.
A software system view can be constructed at varying levels of abstraction, and as the level of abstraction rises, the level of detail necessarily falls.

This leads naturally to the idea that different levels of abstraction will be appropriate for different activities.
One cannot guide an entire deparatment using a class diagram and similarly one cannot build a class diagram from a mission and vision statement.
Yet both levels of detail are related and necessary for the harmonious operation of the whole and the achievement of the goal.

So far, we have discussed viewpoints as if the view was what was to be captured, but what about the viewer themselves?
So long as software has not become completely autonomous, human symbiosis and interaction is still required.
Software is made to be used and administered.
Often by several different classes of users and administrators.
Therefore, the roles of these users themselves may be worth capturing, especially insofar as these roles will need to be on-boarded or eventually automated.
People too are components of any real system.

Seen this way, viewpoint construction is, in the broadest sense, a primary art in the creation of software systems.
Therefore, any proper *software cartography* must take it as its starting point.
From this starting point we can disentangle three primary arts of viewpoint of construction.

Firstly, if we are to clear the forest and build our village, we must learn how to fashion maps.
These maps should define the area over which our campaign is to be waged - the scope and extent of the work - and aid us in finding an advantageous location upon which to carry out that work.

Secondly, if we are to organize people to do the work, we should learn to plan and to fashion roles for them.
This means learning to identify and organize related activities into coherent roles.
Each of us may play many or even all roles, but these roles should be disentangled, described, and their duties captured.

Finally, we should use this wealth of captured information to achieve our own industrial revolution through automation.
Outsized leverage can be achieved only through the automation of roles.
Once a repetitive activity or group of activities is recognized and appropriately captured, partial or full automation (where possible) is a natural next step.

We will call these three primary arts Cartography, Biography, and Automation.

# Cartography

Any intellectual activity will experience a level up when an appropriate diagrammatic representation is discovered [^2]. For example, [Feynman diagrams](https://en.wikipedia.org/wiki/Feynman_diagram) replace rather large multi-variate integrals with a more compact and convenient visual representation which is more amenable to experimentation and dissemination.

Software is no less amenable to pictographic capture. The basic building blocks are the [Flowchart](https://en.wikipedia.org/wiki/Flowchart), [Class Diagram](https://en.wikipedia.org/wiki/Class_diagram), [Sequence Diagram](https://en.wikipedia.org/wiki/Sequence_diagram), [State Diagram](https://en.wikipedia.org/wiki/UML_state_machine), and the other [UML](https://en.wikipedia.org/wiki/Unified_Modeling_Language) basics [^3]. A budding **software cartographer** should seek to master the widest array of diagramming tools possible including the more obscure variants like the [System Context Diagram](https://en.wikipedia.org/wiki/System_context_diagram), the [Data Flow Diagram](https://en.wikipedia.org/wiki/Data_flow_diagram), and [Problem Frame](https://en.wikipedia.org/wiki/Problem_frames_approach). Each of these is like a good tool and one should learn and when and what each of them is good for - a training that only experience can provide.

Armed with these diagrammatic tools a **software cartographer** is able to raise the level of abstraction at which they operate away from code and towards higher-level, more speculative, and larger scale abstractions. These are the brushes with which you will paint your works. Much like a paint brush the value of their productions largely depends on the skill, experience, and natural talents of the person wielding them.

The basic canvas upon with the **software cartographer** paints is the document. The document provides the unifying whole in which their work will hang together. It should be organized to give it a flow and a rhythm - the elements of style and grammar apply here no less than in creative writing. No small effort must be expended in learning to write documents and to write them well as these are the vehicle by which you can share and realize your higher level works.

To summarize: The two cornerstones of cartography are the diagram and the document. One should learn to master both and their applications in conveying the designs of systems.

# Biography

Geography itself is divided into sub-disciplines: [Physical geography](https://en.wikipedia.org/wiki/Physical_geography) and [Political geography](https://en.wikipedia.org/wiki/Political_geography).
What we call "cartography" above maps mostly closely to the former, meaning what we here call "biography" most closely maps to the latter.
When we set out to describe a system we must make sure not to forget the people that inhabit and operate that system.

Surprisingly few systems are designed explicitly with human-machine symbiosis as an explicit goal - yet this is implicitly how they are expected to operate. Humans can and should be considered as components in systems - analysts, investigators, administrators, and account managers are all components in the total business sytem. This symbiosis is usually santized into the user/system dualism, but could be made much richer by thinking of the human "users" as explicit components. The means by which human components convert inputs into outputs may defy simple modeling, but in many cases the inputs and outputs themselves probably do not.

This is the art of biography - learning about and modeling users as explicit components in our systems rather than as sources or sinks at the edges of our systems. We can leverage our cartographic diagramming tools for much of this. Whenever we consider adding a component we should ask if it would not function better or more simply as a person. Often we can take complex components we understand poorly and make them human components until we can gain the experience to understand them better, allowing for another iterative round of refinement.

The art of biography involves collaborating with the human components of your system (whether they are explicitly thought of this way or not) to better understand their jobs. This might involving cataloguing and categorizing various activities to better understand their structure.

To summarize: Biography is the art of thinking about humans as components rather than sources or sinks at the edge of our systems, and learning to better integrate them into the total functioning of the whole.

# Automation

Armed with mature physical and political descriptions of our system we can now begin the next phase of abstraction - launching our own industrial revolution through automation. Our system is a set of components we understand and can model cartographically, and the people operating within that system are similarly modeled and understand through biography. Combining these two we can now look for opportunities to turn repetitive work by people into software components or poorly functioning software components into humans that perhaps function better.

Automation is the pinnacle of cartographic software engineering and its aim.

While there is much still to say here the outline has been sketched. Now all that remains is its elaboration in practice.

---

[^1]: [Watts Humphrey](https://en.wikipedia.org/wiki/Watts_Humphrey) is an as yet underappreciated luminary in the field of software engineering. More important even than the particulars of his ideas is the attitude which underlies them. Namely, his relentless pursuit of self-improvement and belief that software projects are rationally manageable in ways that lend themselves to continuous improvement in all important areas - productivity, prediction accuracy, quality, reliability. Furthermore, Humphrey believes such "rational management" can lend consistency and quality to the works of even less capable individuals while giving ultra-competent individuals the ability to thrive at new peaks of performance. Humphrey views the exasperated rejection of method and over-reliance on self-organization characteristic of Scrum, Agile, TDD et al. as surrender in the face of the difficult task of organizing and planning software development - more political than pragmatic. The [data he collected](https://resources.sei.cmu.edu/library/asset-view.cfm?assetid=5259) on his Team Software Process (TSP) bears this out. Software projects can be managed with the appropriate discipline and techniques, producing astounding results. Similarly for Humphrey, waterfall methods fall victim to a lack of delegation to competent and appropriately empowered teams actually capable of organizing, planning, and performing the work. They also fail to manage risk by ignoring the iterative unfolding of any complex system. What matters is technique and the individuals operating under those techniques. Recent attempts to reconcile TSP and Agile practices have been misguided - the two are fundamentally politically opposed.

[^2]: Wikipedia contains [a large repository of diagrams](https://commons.wikimedia.org/wiki/Specific_diagram_types) but solemnly notes "there is no general accepted classification of diagrams". A fascinating research problem.

[^3]: UML itself has fallen somewhat out of fashion and even traumatized some individuals with the inflated claims and overzealous totalizing of some of its early practitioners. See ["Death By UML Fever"](https://queue.acm.org/detail.cfm?id=984495) for an idea of what happened here. It provides a cautionary tale about being overly prescriptive or enthusiastic with regards to "one method to rule them all" in software engineering.

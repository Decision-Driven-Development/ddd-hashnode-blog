---
title: "Understanding Decision-Driven Development: Key Concepts Unveiled"
seoTitle: "Key Concepts of Decision-Driven Development"
seoDescription: "Explore Decision-Driven Development concepts, focusing on control states, state transitions, and decision tables in software development"
datePublished: Fri May 03 2024 11:22:44 GMT+0000 (Coordinated Universal Time)
cuid: clvql5uyb00010bl3d9dia7xb
slug: understanding-decision-driven-development-key-concepts-unveiled
tags: finite-state-machine, decision-table

---

Before we dive into the specifics of the Decision-Driven Development methodology, it's important to understand some of its underlying concepts. These concepts were developed decades ago, but now they are not so popular in software development practices, at least in enterprise development. That's why we can call this part of the series "Software archaeology".

## Software as a set of states

First of all, let's answer a question: What's the purpose behind writing any software?

The answer is simple: we create software to empower users to solve their problems and alleviate their frustrations. In essence, we provide them with the tools to shape their world into a state that meets their needs.

Take, for instance, an application that allows user to order pizza. The end goal is to have a hot, delicious pizza delivered to the user's door - that is the final state, "pizza delivered". However, before the pizza can be delivered, several other states must be achieved:

* pizza must be prepared
    
* payment must be processed
    
* delivery address must be specified
    
* order must be placed
    

In essence, to reach our end goal, our system and its entities, which model real-world objects, must navigate through a series of predefined states. Without this progression, it would be impossible to solve the user's problem and achieve the desired state.

Well, there's a huge caveat here. The delivery address is definitely part of the program state, right? But what if there are infinite delivery addresses (and there really are)? It means that the number of possible states is infinite as well. How can we possibly account for all of them?

## States are not created equal

Let's call all the possible states of the system *computational states*. They are potentially infinite, but only differ quantitatively from each other. They don't carry significant business meaning and directly determine only the results of actions, but not the actions themselves.

In our pizza delivery scenario, the specific delivery address, while seemingly important, is actually a computational state. It's a variable that can take on an infinite number of values, but doesn't fundamentally change the business logic of the system. The system doesn't care about the specifics of the address. The courier will deliver the pizza to any valid address within the area of service. This is a classic example of a computational state - it's potentially infinite, varies quantitatively, and directly determines only the results of actions (in this case, the delivery of the pizza to point A or to point B).

The specific address doesn't carry significant business meaning in the context of state transitions in the system. It's the transition from 'address unspecified' to 'valid address specified' that truly matters. That's because those two states are *control states*. They are few, have important business meaning, and qualitatively differ from each other. They determine the set of possible actions that the entity takes.

In the context of a pizza ordering application, states such as 'pizza prepared', 'payment processed', 'delivery address specified', and 'order placed' are control states. They are the key states that determine the flow of the system and the actions that can be taken.

> Therefore, the software should focus on managing the control states, as these are the states that truly matter in the context of the business logic of the system. The computational states, while potentially infinite and varying quantitatively, do not fundamentally alter the operation of the system.

The idea of such a separation is not new. Edsger Dijkstra proposed "deriving" programs from a predefined finite number of important states back in the late 1960s.

<div data-node-type="callout">
<div data-node-type="callout-emoji">📑</div>
<div data-node-type="callout-text"><strong>Dijkstra, E. (1968). Co-operating sequential processes</strong>. Available <a target="_blank" rel="noopener noreferrer nofollow" href="https://www.semanticscholar.org/paper/Co-operating-sequential-processes-Dijkstra/2ce99201ab01b6f5404e6b6f77afcbb3332dc45f" style="pointer-events: none">here</a>.</div>
</div>

## Control states are always "conditional"

Let's consider a delivery address as a computational state in a pizza delivery application. This computational state can be transformed into a control state by applying one or several *conditions* to it. For example, the *condition* could be a check to see if the address falls within the service area. If the address is within the service area, the control state could be 'valid address specified'. If not, the control state could be 'invalid address specified'.

Thus, we have computational states that are transformed into control states through a set of *conditions*. Now we need to determine how we can transition from one control state to another.

Obviously, for such a transition, we need to somehow change some basic computational states. This change can be initiated by UI clients, external systems, timers, etc. In our example the change of the computational state could be initiated by the user inputting a different address.

It really helps to look at those computational state changes as a set of self-contained actions, like the "Command" pattern in object-oriented programming. This way we can easily manage the transitions between control states.

## State-Transition paradigm and finite state machines

The concept of control states and state transitions is a fundamental part of the State-Transition paradigm. This paradigm is used in software development to model the behavior of systems that can be in a finite number of states and transition between them based on certain conditions.

Finite state machines (FSMs) are a common implementation of the State-Transition paradigm. FSMs are a mathematical model of computation that consists of a finite number of states, transitions between those states, and actions that are performed when a transition occurs.

In a state-transition model, the system moves from one state to another based on certain conditions, which aligns perfectly with the idea of software being a set of states. FSMs, on the other hand, are a specific type of state-transition system that has a finite number of states, making them ideal for modeling software processes where the number of states is known and limited. Furthermore, FSMs provide a clear and concise way to manage the states and transitions, thus making them the perfect tool for Decision-Based Software Development paradigm.

## Decision Tables

The calculation of conditions on a given computational state is a pivotal component of *decision tables*, a well-established and refined technique. Decision tables provide a structured and compact representation of applied conditions. This technique, honed over many years, allows for the efficient management of complex logic within software, making it an invaluable tool.

Decision tables have several benefits in software development:

1. **Simplicity**: They present logic in a structured, easy-to-understand format. This can be especially helpful for communicating with non-technical stakeholders.
    
2. **Completeness**: They help ensure that all possible combinations of conditions have been considered.
    
3. **Maintainability**: They separate the business logic from the code, making the system easier to modify as business requirements change.
    

A nice work on decision tables and their practical application to software development was done by E. Humby in 1973. So, it's also a part of our software archaeology journey.

<div data-node-type="callout">
<div data-node-type="callout-emoji">📘</div>
<div data-node-type="callout-text"><strong>Humby, E. (1973). Programs from decision tables</strong>. A compact but very insightful book, consisting of decision tables primer, a section on translating decision tables to sequential condition checks and a section on optimizing the resulting programs.</div>
</div>

## Conclusion

In this blog post, we've explored the concept of software as a set of states, distinguishing between computational and control states. We've seen how control states are the key states that determine the flow of the system and the actions that can be taken, while computational states are quantitatively infinite and do not fundamentally alter the operation of the system.

We've also briefly mentioned the importance of state-transitions and Finite State Machines (FSMs) in modeling and managing software states. FSMs provide a logical and efficient way to model and manage states and transitions, making them ideal for software development.

Finally, we've introduced the concept of decision tables as a structured and efficient way to manage complex logic within software. Decision tables provide a simple, complete, and maintainable way to represent conditions and logic in software systems.

Both techniques, state-transition modeling and decision tables, have been around for decades, thus the term "software archaeology". However, they remain relevant and valuable tools in modern software development practices. We'll discover the practical application of these concepts in the next part of the series.
# Overview

The notion of **zero knowledge** was first proposed in the 1980s by MIT researchers Shafi Goldwasser, Silvio Micali and Charles Rackoff. 
That time, most work in this area focused the **soundness** of the proof system. It considered the case where a malicious **Prover** attempts to ‘trick’ a **Verifier** into believing a false statement: What happens if you don’t trust the Verifier?

> ***Soundness***: you should follow [this book](https://www.amazon.com/Logic-Computer-Science-Modelling-Reasoning/dp/052154310X) - chapter **1.4 Semantics of propositional logic** (p.45, p.49)

### The problems

How much extra information is the Verifier going to learn during the course of this proof, thus this statement is true?

Let's see an example. In most real systems (2023), when logging, the clients input their password, then the "raw passwords" were transmitted to the server. Servers will calculate (most, put them into hash function) passwords, then compare "encoded passwords" with "also encoded passwords" stored in database.

-> Why servers have privilege to know client's info, whether hackers can take advantage of this to analysis the habit of creating the clients's passwords?
### A "real world" example

Imagine the network structure is represented by the graph below.Each vertex in this graph represents a telecom tower. The connecting lines (edges) indicate tower's transmissions are likely to interfere with each other.

<img src="./assets/telecom-towers.png" alt="Telecom Tower" style="width:50%; display: block; margin-left: auto;  margin-right: auto;">

If adjacent towers use the same bandwidth, it can be conflicted
So if we use three different frequency, the network will work normally. Theory problem called the graph three-coloring problem.

<img src="./assets/telecom-towers-colored.png" alt="Telecom Tower Colored" style="width:50%; display: block; margin-left: auto;  margin-right: auto;">

If this network was very large and complex, so much so that the computing power at my disposal was not sufficient to find a solution. In this instance, I might hire my friends at Google to solve it for me on spec.

But this leads to a problem.

Suppose that Google devotes a large percentage of their computing infrastructure to searching for a valid coloring for my graph. I’m certainly not going to pay them until I know that they really have such a coloring.

At the same time, Google isn’t going to give me a copy of their solution until I’ve paid up. We’ll wind up at an impasse.
### A crazy technical solution (with hats!)

The solution includes some concepts:

1. Google cover all tower with **hats**, make sure the client not have info about the color of each tower.
2. When the client testing, Google will show randomly some towers and their colors that proved Google is not lying.
3. The loop will be ended util step **2** made enough large (~ E^2), so client can be confident to pay money for Google

> Please follow [main article](https://blog.cryptographyengineering.com/2014/11/27/zero-knowledge-proofs-illustrated-primer/) 
for more information.

### What makes it **zero knowledge**?

The first rule of modern cryptography is never to trust people who claim such things without proof.

Goldwasser, Micali and Rackoff proposed three following properties that every zero-knowledge protocol must satisfy. Stated informally, they are:

**1. Completeness**: If Google is telling the truth, then they will eventually convince me (at least with high probability).

**2. Soundness**: Google can only convince me if they’re actually telling the truth.

**3. Zero-knowledgeness**: I don’t learn anything else about Google’s solution. (hard part, we need to conduct a very strange thought experiment.)

> **Completeness** and **Soundness**: you should follow [this book](https://www.amazon.com/Logic-Computer-Science-Modelling-Reasoning/dp/052154310X) - chapter **1.4 Semantics of propositional logic** (p.45, p.49)
# AI Programmers

This post is a bit different. I was asked a fascinating question today:
> ...[H]ow visible is the code in an end product to the user? ...Artists have been complaining that their work was used to train AI. Can most programs be decompiled into something from which an AI can parse and scrape?

To answer this question, I think it will be best to address the constituent parts.

## The "end product"
Software comes in all shapes and sizes. 

1. The source code for a program may be freely distributed as the product itself. Advocates, such as the [FSF](https://www.fsf.org/), believe this offers the user freedom and protection from malicious actors through transparency and peer-review.

2. The program may also be compiled and distributed as an executable binary on the user's behalf. While the source code may be openly available to review and compile, some prefer the expediency of the ready-to-run executable, typically trusting that someone has done due diligence to review the software being distributed for safety, or that their antivirus software will catch any wrong doing.

3. In cases where the company wants to protect the intellectual property of the product code, the compiled executables may be the only software distributed to the user, such as with many modern videogames. 

4. This is in contrast with an even more restrictive form of distributing modern videogames - streaming services. Input from the user, such as keyboard or controller input, are sent to a server where the game code is running. The server determines how that input affects the state of the game, makes the changes, and streams back the resulting video. 

How much of the overall program the AI has access to restricts the ability to learn from it. Even if it had access to a server running the core services of a product, there may be external services that the program needs to request data from. Depending on the program, it may be useless without these external services.

## Decompilation, parsing, and scraping
First things first - there is no 1-to-1 relationship between source code and compiled code. Decompilation programs can skillfully generate code which will compile back the same way. This generated code may be obscure and hard to read, missing comments, missing annotations, and missing compiler directives.

That said, it would be a good enough representation for an AI to learn from. What it would learn may be highly obscure and difficult to read to a human, and it may not efficiently move or transform data, but it may come up with something that works...eventually.

Granting the benefit of the doubt, the AI could then optimize this code to solve problems in more human timescales, resulting in faster working code. 

There is a lack of [international copyright law](https://guides.library.upenn.edu/copyright/international), but there is at least regional [software license](https://en.wikipedia.org/wiki/Software_license) compliance, which will typically hold the AI creator responsible for breaches of contract. There may already be enough open source and permissively licensed public code to train an AI all about data structures, software design patterns, and common solutions to common problems, but as of yet, no program has been able to come close to the critical thinking and foresight of human software engineers. 

To elaborate, when a high-level problem or challenge lends itself the opportunity to be solved, such as moving a car from Germany to California, USA, a minimal list of requirements can be established fairly quickly. Off the top of my head, licensing and legal requirements, the costs and logistics of shipment and ground transport, and even insuring against various liabilities along the way. Maybe an AI trained on this domain of problem could predict these things, or perhaps we could just tell it these requirements and expect it to take care of the hard stuff. 

Now suppose we failed to provide the AI with anything we might consider common knowledge, such as the need to convert currencies, language compatibility considerations at different stages of the journey, minor slowdowns or major stoppages and its effect on the rest of the logistical chain. Software bugs are not uncommon, but if the code is tested for quality assurance and a bug is discovered, can the AI fix the bug? Is the language we would use to describe the bug the same as writing code itself?

To take the analogy a step further - suppose the client now wishes to move two cars, or a car every day for the next 10 years, or a tank. Can the AI modify its solution to accomodate the changes? If it is sufficiently advanced, are there drawbacks? Perhaps there are cost and time implications to changing the requirements, as there are with human developers, such as regenerating the entire solution from scratch with the new requirements.

At a more philosophical level - is code more than just a representation of requirements? Perhaps forcing a certain structure on language itself also forces deliberate human thought to translate our vague desires into concrete implementations.

## Artificial Intelligence (AI) vs. Machine Learning (ML) vs. Deep Learning
It is worth noting the following distinctions, as I have used "AI" throughout this post where "machine learning" was likely more accurate:

- AI is a blanket term to cover all software and computer systems aimed at performing tasks normally requiring human intelligence.

- ML is more specific, focusing specifically on giving computers the ability to learn without being explicitly programmed. 

- Deep learning is even more specific as a category of ML aiming to also utilize brain-like logical structures.

## tl;dr
**The code in the end product is not particularly visible.** Not all programs can be decompiled and not all programs behave in isolation, but despite this, there may be enough freely available code on the internet for an AI to minimally learn what we might call core "concepts" of programming. However, I do struggle to think how the AI would internalize these concepts without some human help to describe the problems being solved with that code and the tradeoffs of the design decisions.

Perhaps the future of programming will be to use a traditionally written language, making the next generation of programmer the linguists and poets.

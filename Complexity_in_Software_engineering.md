# Mastering complexity in Software Engineering

Mastering complexity is the most essential thing in software engineering. Avoiding it as much as we can is our task. Allow it only when it is essential and cannot be avoided because the value it creates justifies the cost of it.

Unfortunately, we often see precisely the opposite happening. Complexity is a trap. You often realize that you build something too complex when you are done with it. There should be something to prevent this. But before we dive into the solution space, let us talk about the why?

**Why is complexity such a thing?**

Software has two main values:

- Behavior
- Structure

Since behavior has no impact on the structure of a software system, for the structure it is quite the opposite.

Software was invented to be “soft”, as its name already tells us. It was intended to be a way to easily change the behavior of machines. If we’d wanted the behavior of machines to be hard to change, we would have called it hardware.

And if the code or the system is all tangled up, your changes to it will have a high probability to have an unplanned impact on the behavior of the system. Therefore, it reduces the ability to change your system. It slows down the whole development process or as a worst-case scenario, it makes further evolution impossible. As you can imagine, this can lead to a loss in revenue or even to bankruptcy.

Here are a few examples:

- Knight Capital Group lost $440 million in 2012 due to a trading algorithm error caused by a glitch in the code due to complexity.

- Lehman Brothers filed for bankruptcy in 2008 due to its reliance on complex financial models and trading algorithms.

- RadioShack filed for bankruptcy in 2015 due to its inability to keep up with technological change and its outdated inventory management system.

- Borders Group went bankrupt in 2011 due to its failure to adapt to changing consumer preferences and reliance on a complex inventory management system.

In all these cases was a need for behavior change that could not be enforced due to complex systems that were out of control. The change was needed to fulfill new customer or internal requirements. Those companies that were able to adapt their systems to the requirements quickly had huge market advantages. The above mentioned companies not.

**So what can we do?**

Avoiding complexity whenever possible. But when is it possible and when not? I guess the only right answer can be: "It depends!".

The first thing we can do is learn about the concept of essential complexity and accidental complexity. This concept was introduced by Turing Award winner Fred Brooks who is mostly known for his paper "No Silver Bullet—Essence and Accident in Software Engineering". So let us have a look at it:

## Accidental complexity

Accidental complexity refers to the complexity that arises due to the implementation details of a system rather than its essential nature. In other words, it is the complexity that is not inherent in the problem being solved, but rather a result of the particular way the solution is constructed. Or in other words: It's the stuff you don't need to solve a problem!

### Popular examples are

#### Over-engineering

Does your application need a full-blown framework like Spring Boot to deliver its value? Sure you need Kubernetes even if your application does not need to scale. Uhu, yeah the mostly static landing page has to be written in React!

Over-engineering, where a system is designed with more complexity than is necessary, can lead to accidentally complex code. This can result in unnecessary features or functionality that increase the codebase's complexity without providing any real benefit to the user.

#### Dependencies

Many software systems rely on a large number of external libraries and dependencies. Managing these dependencies can become accidentally complex if they have many interdependencies or require specific versions, making it difficult to keep track of which dependencies are needed and which are not. Often is a result of over-engineering.

#### Configurations

The process of configuring a system can become accidentally complex if it requires a long list of settings to be adjusted, many of which are not well-documented or understood by the user and most of them may not be necessary. This can make it difficult to set up, test and maintain the system, and can also increase the risk of errors and inconsistencies.

#### Features

Complexity is not only a "technical" problem. Feature complexity is when you don't know the value the feature has to a user. An untested (not gathering feedback from users) feature is always accidentally complex because you don't know yet if it's needed from the user's perspective.

## Essential complexity

When accidental complexity is the stuff you don't need, essential complexity is what you cannot avoid.

It refers to the inherent complexity of a problem or task that cannot be eliminated through simplification or abstraction. It is the complexity that is inherent in the problem domain itself, rather than in the implementation of a solution.

It is the place where the actual value of the product gets manifested into code. Removing it will decrease the value. Some call it business logic or domain logic.

A good example of essential complexity is cryptography. It involves the secure transmission of information and is inherently complex due to the mathematical principles and algorithms involved in encryption and decryption. While some aspects of cryptography can be simplified or abstracted, the fundamental complexity of secure information transmission cannot be eliminated.

## But what is complexity in a more general context?

There are a lot of different types of complexity out there [Wikipedia](https://en.wikipedia.org/wiki/Complexity). In software engineering, we are especially interested in behavioral complexity.

This type of complexity arises from the interactions between different parts of the system, as well as between the system and its users.
The nature of behavioral complexity is the lack of predictability of how the system reacts to interaction or change.

**Examples**:

- Large and highly coupled code is unable to change easily without a high risk of introducing bugs for example.

- Concurrent or parallel running systems can be another excellent example of behavioral complexity because if you don't be careful they quickly become non-deterministic.

- And there is a system that is tremendously complex that we all know well, even though it has nothing to do with computers, the human body. It is a complex system because it consists of many different parts, each of which has its unique structure, function, and behavior. These parts include organs, muscles, nerves, glands, hormones, etc. which work together in intricate ways to sustain life and maintain homeostasis. The interactions between different parts of the body are often nonlinear, meaning that small changes in one component can have significant effects on the behavior of the entire system.

## Tackling accidental complexity

As we defined accidental complexity as the stuff you don't need, the solution to the problem is pretty simple. Remove the unnecessary stuff. You're welcome.

Well, sadly the hard part is recognizing what is essential and what is not. Most times we need to explore this incrementally because we do not know what we or the product needs right from the beginning. So instead of going all in at first, start as simple as possible and work iteratively and incrementally our way and add complexity when we discover that there is an actual need.

Work systematically. Start only with what is needed. Do a bit of an upfront design. Be smart and stop fooling yourself. Do not make decisions on what is good for your cv, so-called cv driven development. Yes, developers have a bucket list with technologies they haven't yet worked with. Don't do this. Be a professional, not a (paid) amateur.

Ask yourself questions like: Do we need a dependency injection framework to fulfill the pattern? Do we need a cache right from the beginning, because we might need it later? Do we need to depend on this huge library even though we only use a tiny bit of functionality of it, that we could easily implement on our own? Do you need 8 layers of abstraction in your code because you blindly followed some methodology? And do you have to use all the fancy new language features that only bloat your code and deliver no real value rather than make only you happy? Mostly the answer is no. I say: "The best code is boring code".

Structure your system in a way that you can delegate decisions to the future when you explored more terrain. When these questions are easier to answer. Have an architecture that is open for extension but closed for modification. Before you can no longer resist the urge to shout "YAGNI" (You Aren’t Going to Need It.) out loud, let me illustrate my point with an example.

Let's say your system needs some kind of persistence mechanism to do its job. Maybe another to-do list app. Don't start with the decision on what kind of database you should implement. In most cases, the type of db does not matter at the beginning. Start with what is essential to your system, the business rules or higher-order policies. Define an interface for the persistence logic. Introduce what Uncle Bob referred to as an architectural boundary in his book "Clean Architecture". This makes the implementation a plugin. A detail that can be changed later. Start with the easiest and simplest implementation that fulfills your early needs. In most cases, this would be an in-memory db to use as a fake in your unit tests. Later on, you can add an implementation (plugin) for an SQL or NO-SQL db or whatever type of DB you need. Maybe a simple file storage system is sufficient enough. This prevents you from introducing accidental complexity from the beginning.

This architectural pattern is mostly known as [Hexagonal Architecture (also known as Ports and Adapters)](https://en.wikipedia.org/wiki/Hexagonal_architecture_(software)). But there is also [DCI](https://en.wikipedia.org/wiki/Data,_context_and_interaction) or [BCE](https://en.wikipedia.org/wiki/Entity-control-boundary) and of course [Clean Architecture](https://blog.cleancoder.com/uncle-bob/2012/08/13/the-clean-architecture.html) as an attempt at integrating all these architectures into a single actionable idea. They all tackle the same problem and more.

Each of these architectures produces systems that have the following characteristics:

- **Independent of frameworks**:
The architecture does not depend on the existence of some library of feature-laden software. This allows you to use such frameworks as tools, rather than forcing you to cram your system into their limited constraints.
- **Testable**:
The business rules can be tested without the UI, database, web server, or any other external element.
- **Independent of the UI**:
The UI can change easily, without changing the rest of the system. A web UI could be replaced with a console UI, for example, without changing the business rules.
- **Independent of the database**:
You can swap out Oracle or SQL Server for Mongo, BigTable, CouchDB, or something else. Your business rules are not bound to the database.
- **Independent of any external agency**:
Your business rules don’t know anything at all about the interfaces to the outside world.

I highly recommend getting yourself familiar with at least one of their concepts. But be aware that in some cases even implementing those boundaries can be accidentally complex.

Moving on. Let's go one step further and apply this "lean" approach also to our features, because:

 The best code is the code that does not need to be written.

So do we need to write new code to give users the capability to solve a problem? Or even worse, set up a whole new microservice before we even know what the problem is or in other words what kind of capabilities the user needs to solve his problems. We might use an existing API to at least give some capabilities to the users and then measure if our assumptions meet reality. Don't build the stakeholder's fancy tool to manage the new feature right from the beginning, before you even know if the feature will be successful. Use tools you already have, even if it does not fit perfectly. After you gained some more insights, re-evaluate the decision and move on which might mean writing new code.

In other words: **Maximize the amount of work not done!**

### Lean Experimentation

Does the user want this feature? What is the value we expect from this feature? How can we measure success?

Business people tend to create unnecessary complexity by requiring features that have little to no value to the majority of customers. Because the idea may be based upon a single person's opinion and does not represent any need from the majority of users. Mostly this one person just thinks it is a good idea and has the power to "force" it into the development teams.

By treating the product development process not as an experiment, with a clear hypothesis and feedback mechanism to evaluate the hypothesis, we can increase the risk of introducing unnecessary features and therefore, create overly complex systems.

**If we do not test (gathering feedback from users) our features, they are always accidentally complex** because you don't know if you need them. Don't rely on assumptions and guesses. Start with your best guess and quickly gather data to evaluate the value by releasing it to real customers as soon as possible. Falsify your hypothesis. You might not be able to find causation but at least the data in combination with user feedback will give you signals, hints, and stuff to further investigate on.

**Simply, do lean experimentation**:

"Lean Experiments are based on the Lean Startup approach to creating new products and services under conditions of extreme uncertainty. Lean Experiments are designed to quickly and cheaply gather evidence to validate or invalidate risky assumptions about your product."

Nice, we don't need to reinvent the wheel. Some people already came across this problem and created a small, lightweight process how to make lean experiments:

1. **Hypothesis**: Clearly state the hypothesis you want to test. For example: "If we add a feature that allows users to easily save their progress, then more users will complete the sign-up process."

2. **Metrics**: Define the metrics you will use to measure the success of the experiment. These should be tied to your hypothesis. The metrics should be a part of your hypothesis. For example: If we add a feature that allows users to easily save their progress, then 20% more users will complete the sign-up process." Without a metric, your hypothesis is just an assumption. It is useless because it can not be tested and therefore not validated.

3. **Methodology**: Describe how you will run the experiment. This should include details such as the sample size, the time frame for the experiment, and any control groups you will use. For example: "We will randomly assign half of our users to the experimental group, which will have the new feature. The other half will be in the control group, which will not have the new feature. We will run the experiment for one week and measure the success metrics."

4. **Prototyping**: Develop a prototype of the feature or change you want to test. This should be quick and inexpensive, focusing on the core functionality that you want to test. So instead of a Minimal Valuable Product define an even smaller Minimal Testable Product. But bear in mind that your results heavily depend on what you test. If you test for revenue, you need to have the whole behavior of the feature implemented. Most of the time you'll end up implementing the MVP feature. But if you want to test if the majority of users would use the feature, a UI-only implementation with no real functionality might be just enough to gain first insides.

5. **Testing**: Run the experiment according to your methodology, collecting data on your success metrics. Be sure to track any unexpected results or issues that arise during the experiment.

6. **Analysis**: Analyze the data from the experiment, comparing the success metrics for the experimental group and the control group. Determine whether the hypothesis was supported or not.

7. **Next steps**: Based on the results of the experiment, decide on the next steps. If the hypothesis was supported, consider implementing the feature or change more broadly. If the hypothesis was not supported, consider iterating on the prototype and running the experiment again, or pivoting to a different approach altogether.

Remember that the lean experiment approach is all about rapid prototyping and iteration. Don't be afraid to adjust your approach based on what you learn during the experiment.

### Protect your system

In good organizations, the Teams that build the product are self-organized and own their product. This also means that the team has the responsibility to protect the system from any extrinsic- or intrinsic-driven complexity which can be any kind of ideas, feature requests, and changes, especially if they inherently introduce a lot of new (behavioral) complexity to the project. Have in mind that, only a simple solution is a good solution when working on such. Suggest simpler alternatives. Balance customer value with complexity. Let simplicity be your mantra.

That's the best we can do.

## Tackling Essential complexity

Ok, let us assume you fought the battle with yourself and everybody outside the team to avoid accidental complexity as much as possible. What is left is the stuff you need to live with. It is essential to solving the problem. It still is your enemy but you cannot run away from it. The good news is, there is plenty of stuff you can do to manage it. Let us see what we can do.

### Modularity

If complexity is the lack of knowledge of how a system behaves, especially when changes are made to it, we should find a coherent structure to separate the parts of our system that should not be interdependent. When we reduce the coupling between stuff that is not coherent, we only need to "load" the stuff in our brains that has the same concern, when applying changes to it and therefore reduce the possibility that changes affect too many other parts of the system that we are not able to track at once. It's divide and conquer. The concern of a thing plays an important role here. But not only one.
Make sure that the parts of your system are responsible only for one thing. But responsibility should be interpreted differently here. It´s about the actor or driver of change. This can be a group of users or stakeholder, but not only. Keep this also in mind when deciding which behavior should be grouped into one coherent module.

In summary, the following are the properties that systems should have that help us master essential complexity.
Therefore, systems should be:

- modular
- separated by concerns
- high cohesive
- low coupled
- hides information and has a good abstraction

#### Cost of Change-Driven Development

The effort that is needed to make changes to your system is called the `Cost of Change`. When the product development cycles are short, the learnings come in quickly and the need for change also. Therefore, your system needs to be agile too. The cost of change must be as low as possible. We need to adapt the changes to the system quickly, because if you learn that you did something wrong, the faster you can make changes to your system and re-run the experiment, the faster you will make progress.

At this point, I deliberately refrain from giving extensive examples and elaborations on the individual aspects mentioned. There is plenty of them out there in the form of books and articles on the web. The ones I like to mention here are Modern Software Engineering by Dave Farley and Clean Architecture by Uncle Bob.

### Experimentation, again

Modularity helps us to tackle complexity in code. But how do we even get there? How do we know what parts the systems should have? What are the concerns that need to be separated? What should be coupled and what not? 

To answer the questions, we need to see software engineering as an exercise in discovery and learning. It is always hard to understand something as a whole. Therefore, we need to explore it by developing the system. We cannot learn by just guessing. We need to make our hands dirty and build the software piece by piece (incrementally) to better understand it.

Do lean experimentation from a technical perspective. Make each iterative step an experiment. Follow the lightweight process described above if it fits. Or make it even smaller. Do it and learn not only if your system behaves as it should but also if the structure (architecture) supports the fact that it might have to change rapidly (low cost of change).

You get the point.

## Conclusion

Developing digital products is hard and challenging. It is easy to screw things up quickly because not only our systems and their behavior are complex, the process of development itself is complex too.

To master it every individual as well as the whole organization needs to become an expert in learning. The organization and every part of it need to become an environment that supports learning, knowledge sharing, and embracing change.

We as individuals tend to fool ourselves, because we are humans. We like simple answers to complex questions and do not care if the answer is right or wrong if it sounds good. This can be mitigated through a lightweight process of lean experiments that leads us to a road of evidence.

We finally do the stuff that we know works to build better products faster

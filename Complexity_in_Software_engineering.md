Mastering complexity is the most essential thing in software engineering. Avoiding it is our task. Allow it only when it is essential and cannot be avoided because the value it creates justifies the cost of complexity.

Unfortunately, we often see precisely the opposite happening. Especially with supposedly "senior" colleagues who are attracted to complexity like moths to a flame. Often with the same result.

They are only fuelling their ego by wanting to show how well they can master complexity. Often they overestimate their abilities. Even if they don't, they don't consider that software engineering is a highly collaborative discipline. It is not enough for 1 engineer to understand a complex system. The whole team has to understand it—even or especially the junior engineers.

**So what can we do?**

Avoiding it whenever possible. But when is it possible and when not? I guess the answer only can be "It depends!". 

But the first thing we can do is learn about the concept of essential complexity and accidental complexity. The concept was introduced by Turing Award winner Fred Brooks who is mostly known for his paper "No Silver Bullet—Essence and Accident in Software Engineering". 

## Accidental complexity
Accidental complexity refers to the complexity that arises due to the implementation details of a system rather than its essential nature. In other words, it is the complexity that is not inherent in the problem being solved, but rather a result of the particular way the solution is constructed. Therefore, it's the stuff you don´t need!

### Popular examples are:

#### Over-engineering
Does your application need a full-blown framework like Spring Boot to deliver its value? Sure you need Kubernetes even if your application does not need to scale. Uhu, yeah the mostly static landing page has to be written in React!

Over-engineering, where a system is designed with more complexity than is necessary, can lead to accidentally complex code. This can result in unnecessary features or functionality that increase the codebase's complexity without providing any real benefit to the user.

#### Dependencies
Many software systems rely on a large number of external libraries and dependencies. Managing these dependencies can become accidentally complex if they have many interdependencies or require specific versions, making it difficult to keep track of which dependencies are needed and which are not. Often is a result of over-engineering.

#### Configurations:
The process of configuring a system can become accidentally complex if it requires a long list of settings to be adjusted, many of which are not well-documented or understood by the user and most of them may not be necessary. This can make it difficult to set up, test and maintain the system, and can also increase the risk of errors and inconsistencies.

#### Features:
But complexity is not only a "technical" problem. Feature complexity refers to the complexity that arises from the features and functionality that a system provides. Business people love to create unnecessary complexity by requiring features that have little to no value to the majority of customers. Because the idea is mostly based upon a single person's opinion and does not represent any need from the majority of users. Mostly this one person just thinks it is a good idea and has the power to "force" it into the development teams. 

By treating the product development process **not** as an experiment, with a clear hypothesis and feedback mechanism to evaluate the hypothesis, we can increase the risk of introducing unnecessary or overly complex features. 

 **If we do not test (gathering feedback from users) our features, they are always accidentally complex**.

## Essential complexity
When accidental complexity is the stuff you don´t need, essential complexity is what you need. 

It refers to the inherent complexity of a problem or task that cannot be eliminated through simplification or abstraction. It is the complexity that is inherent in the problem domain itself, rather than in the implementation of a solution.

Probably the best example of essential complexity is our business logic. It is the place where the actual value of the product gets manifested into code. Removing it will decrease the value.

A good example of essential complexity is cryptography. Cryptography involves the secure transmission of information and is inherently complex due to the mathematical principles and algorithms involved in encryption and decryption. While some aspects of cryptography can be simplified or abstracted, the fundamental complexity of secure information transmission cannot be eliminated.

## But what is complexity in a more general context?
There are a lot of different types of complexity out there (Wikipedia)[https://en.wikipedia.org/wiki/Complexity]. But we want to classify complexity in software engineering like this:

### Behavior driven
When you don´t know how the system behaves. When you don´t know how the system reacts as you add more code or change existing. It is what happens when everything depends on each other and shares every piece of information with each other.

### Quantity driven
Here complexity gets created just by the sheer size of a system. It has lots of components. And even when the logic of every component is easy to understand or already well-known, it is hard to understand the system as a whole. It is when the system is too big to fit into one person's head. 

### In general
So, in general, complexity means not knowing stuff about a system. But complexity is not binary. It is not that a system is complex or not. We instead understand complexity as the degree of complexity the system has. Therefore, our goal is to 

## Tackling Accidental complexity
As I defined accidental complexity as the stuff you don´t need, the solution to the problem is pretty simple. Remove the stuff that is unnecessary. You're welcome.

Well, sadly the hard part is recognizing what is essential and what is not. Most times we need to explore this. But instead of going all in at first, we should start as simple as possible and work iteratively and incrementally our way and add complexity when we discover that there is a need and make the accidental complexity essential.

I would even go one step further and say:

**The best code is the code that does not need to be written.**

Do we really need to write a new (micro)service to give users the capability to solve a problem? We might use an existing API to at least give some capabilities to the users and then measure if our assumptions meet reality. After we gained some more insights, we re-evaluate our decision and move on.

That´s the best we can do.

## Tackling Essential complexity
...

# The value of Test-Driven-Development

There are a lot of misconceptions about TDD out there. And I will not go into detail here. Instead, I want to show you what I think TDD is but more importantly what I think where TDD can help you.

## The method

### Write executable specifications

The classic test-driven approach is to start your implementation of some behavior you want to achieve by writing your test first. Yes even before starting the implementation. In my experience though, it does not matter if you write the test first or if you write it in parallel with your implementation. The point is to write it immediately and as the same process of implementing the logic. Not after you finished everything. 

Run your tests and make sure they **fail**.

### Implement the logic and structure for testability

Now comes the fun part. Implement the logic. But focus on behavior, not on the structure. Evolve your test in parallel with your code. Run little experiments by running the test(s) to discover the behavior of your design through learning. The structure you give your code is only driven by testability. Keep in mind that you should not test the implementation rather than the behavior of your code. Your code should never have extra logic that only serves testability needs. This is a red flag. Take a step back and try to find a way to create the testability you need to achieve by separation that reduces coupling.

Do this iteratively till you achieved the desired outcome and prove it by running the test successfully. Now your code is ready for production since it has already the assumed value from the customer's perspective.
Even though we made no big moves to create a high-quality structure. It is ok to already deliver it to your customers.

Run your tests and make sure they **succeed**.

### Refactor toward a better structure

After you are done implementing the logic, we need to start thinking about the future. Our fresh code works fine, but what about his ability to be adaptable to changes? Software was invented to be a way to easily change the behavior of machines. This ability is needed because the requirements of users, internal stakeholders, or our (technical) environment change pretty quickly.

The effort that is needed to make changes to your system is called the Cost of Change. When the product development cycles are short, the learnings come in quickly and the need for change also. Therefore, your system needs to be agile. The cost of change must be as low as possible.

We achieve this by reducing the complexity of our code. In software engineering, we are especially interested in behavioral complexity.
This type of complexity arises from the interactions between different parts of the system, as well as between the system and its users. The nature of behavioral complexity is the lack of predictability of how the system reacts to interaction or change.

To reduce complexity we need to structure our parts in a way that encapsulates behavior. We mainly strive for independence between the moving parts by separation and clear interfaces. If you want to learn more about mastering complexity, I recommend reading my other article on this topic.

Run your tests again and make sure they still **succeed**.

#### Red, Green, Refactor 
Just to be mentioned. This process is also known as red, green, and refactor. Because first, you start with failing tests which are mostly visually indicated by our toolings with a red color. Then you work till all tests pass which is shown by a green color and then you start the refactoring.

## Summerized

Let´s recap what we just did:

First, we created executable specifications in the form of tests and confirm that they fail by not implementing any behavior yet.

Then we focused on behavior and did only just enough structural work to make our code testable. 

At last, we invested in the future and made our code sustainable by lowering the cost of change.

## The true value of TDD

We, humans, tend to interpret working efficiently as doing multiple things at a time. So-called human multitasking. Wikipedia says:

Human multitasking is the concept that one can split their attention on more than one task or activity at the same time, such as speaking on the phone while driving a car. Multitasking can result in time wasted due to human context switching and becoming prone to errors due to insufficient attention.

According to research https://en.wikipedia.org/wiki/Human_multitasking#Research, multitasking significantly increases the risk of making mistakes.

Therefore, avoiding multitasking is the goal. TDD helps you by separating the process of implementing behavior and working on structure.
# The value of Test-Driven-Development

There are a lot of misconceptions about TDD out there. And I will not go into detail here. Instead, I want to show you what I think TDD is but more importantly what I think where TDD can help you.

## The method

### Write executable specifications

The classic test-driven approach is to start your implementation of some behavior you want to achieve by writing your test first. Yes even before starting the implementation. In my experience though, it does not matter if you write the test first or if you write it in parallel with your implementation. The point is to write it immediately and as the same process of implementing the logic. Not after you finished everything. 

Run your tests and make sure they fail.

### Implement the logic and structure for testability

Now comes the fun part. Implement the logic. But focus on behavior, not on the structure. Evolve your test in parallel with your code. Run little experiments by running the test(s) to discover the behavior of your design through learning. The structure you give your code is only driven by testability. Keep in mind that you should not test the implementation rather than the behavior of your code. Your code should never have extra logic that only serves testability needs. This is a red flag. Take a step back and try to find a way to create the testability you need to achieve by separation that reduces coupling.

Do this iteratively till you achieved the desired outcome and prove it by running the test successfully. Now your code is ready for production since it has already the assumed value from the customer's perspective.
Even though we made no big moves to create a high-quality structure. It is ok to already deliver it to your customers.

Run your tests and make sure they succeed.

### Refactor toward a better structure

After you are done implementing the logic, we need to start thinking about the future. Our fresh code works fine, but what about his ability to be adaptable to changes? Software was invented to be a way to easily change the behavior of machines. This ability is needed because the requirements of users or internal stakeholders change pretty quickly. 

The effort that is needed to make changes to your system is called the Cost of Change. When the product development cycles are short, the learnings come in quickly and the need for change also. Therefore, your system needs to be agile. The cost of change must be as low as possible.


## Summerized

First...

Then...

At last...

## The value is efficiency 
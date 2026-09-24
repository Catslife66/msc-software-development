# Software Engineering Case Analysis

1. What is the situation?

Only use the facts the case gives you.

2. What is uncertain or constrained?

Look especially for things like unclear requirements, changing requirements, fixed deadlines/budgets, limited resources, unfamiliar technology, dependencies, legacy systems, or missing knowledge.

> “Requirements are incomplete and the deadline is fixed.”

3. What could go wrong?

Turn those uncertainties/constraints into risks.

> Unclear requirements → build the wrong functionality.
> No tests → changes may introduce unnoticed regressions.
> Hardware dependency → changing hardware may require substantial rework.

4. What would the impact be?

Keep this at project/software level:

delay, increased cost, defects, rework, poor maintainability, failure to meet requirements.

You usually don't need to descend into detailed technical implementation unless the case specifically asks for it.

5. What engineering action could reduce that risk?

Now bring in concepts from the module:

requirements clarification, prototyping, incremental development, testing, documentation, modular design, customer feedback, change anticipation/tolerance, etc.

6. Why does that action help?

Don't say:

> “Use Agile.”

Say:

> “Develop incrementally so that the client can review early functionality. This could expose misunderstood requirements before substantial development effort has been committed.”

So your basic thinking loop is:

**FACT → UNCERTAINTY/CONSTRAINT → RISK → IMPACT → ACTION → WHY**

For a Software Engineering case, first ask:

> “Does knowing this missing detail change the software-engineering risk I'm identifying?”

If no, ignore it.

If yes, then it's perfectly legitimate to say:

> “We don't have enough information to decide this yet, so clarifying X should be one of our first actions.”

# Clean Code: A Handbook of Agile Software Craftsmanship

## Unit Tests

**Laws of TDD**
  1. You may not write production code until you have written a failing unit test.
  2. You may not write more of a unit test than is sufficient to fail.
  3. You may not write more production code than is sufficient to pass the currently failing test.

The tests and the production code must be ***written at the same time***.

Test code is just as important as production code.
You don't have the same concerns about perfomance as in a production environment, so tests should be ***as readable as possible***.
Sometimes it's better to create functions and utilities designed to be used by the tests, rather than using APIs that programmers use to manipulate the system.

It is unit tests that ***allow changes*** and keep our code flexible, maintainable, and reusable.
If you have tests, you do not fear making changes to the code!

**BUILD-OPERATE-CHECK** - A test-structuring method in which tests should be splitted in three parts:
1. Build up the test data.
2. Operate on that test data.
3. Check that the operation yielded the expected results.

A good rule for writing unit tests is test just one concept per test function and minimize the number of asserts.

**GIVEN-WHEN-THEN** - A method that helps to create the tests. See the examples:
```
Given the last day of a month with 31 days (like May):

1. When you add one month, such that the last day of that month is the 30th
(like June), then the date should be the 30th of that month, not the 31st.

2. When you add two months to that date, such that the final month has 31 days,
then the date should be the 31st.


Given the last day of a month with 30 days in it (like June):

1. When you add one month such that the last day of that month has 31 days, then the
date should be the 30th, not the 31st.
```

**F.I.R.S.T.** - Five rules for writting clean tests:
1. Fast: Tests should be fast so that you don't bother yourself to run them frequently.
2. Independent: Tests should not depend on each other so that you are able to run them independently and in any order.
3. Repeatable: Tests should be repeatable in any environment (PROD, QA, offline environments...) so that you don't have any excuse for why they failed.
4. Self-Validating: Tests should have a boolean output (pass or fail) so that you don't have to manuallly evaluate an output, for example.
5. Timely: Tests need to be written just before the production code so that you design the production code to be easily testable.

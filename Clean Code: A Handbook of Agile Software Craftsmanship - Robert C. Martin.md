# Clean Code: A Handbook of Agile Software Craftsmanship

## Clean Code

Bad code can significantly cause impediment so that you end up ***wading*** through
that bad code.

Many times we create shit code and we choose to go back and clean it up later because it
was working. However, ***later equals never*** as says LeBlanc’s law.

It's important to ***leave the campground cleaner than you found it***. Always that you make
changes to functionality, even if it's not yours, improve it.

Below, there's good description of how productivity goes down in a project with bad code.
It's important to note that adding new staff is even worse.

> As the mess builds, the productivity of the team continues to decrease, asymptotically
approaching zero. As productivity decreases, management does the only thing they can;
they add more staff to the project in hopes of increasing productivity. But that new staff is
not versed in the design of the system. They don’t know the difference between a change
that matches the design intent and a change that thwarts the design intent. Furthermore,
they, and everyone else on the team, are under horrific pressure to increase productivity. So
they all make more and more messes, driving the productivity ever further toward zero.

The snippet below describes what's the sequence of an odious code base.

> Eventually the team rebels. They inform management that they cannot continue to develop
in this odious code base. They demand a redesign. Management does not want to expend
the resources on a whole new redesign of the project, but they cannot deny that productivity
is terrible. Eventually they bend to the demands of the developers and authorize the
grand redesign in the sky.

> A new tiger team is selected. Everyone wants to be on this team because it’s a green-field
project. They get to start over and create something truly beautiful. But only the best
and brightest are chosen for the tiger team. Everyone else must continue to maintain the
current system.

> Now the two teams are in a race. The tiger team must build a new system that does
everything that the old system does. Not only that, they have to keep up with the changes
that are continuously being made to the old system. Management will not replace the old
system until the new system can do everything that the old system does.

> This race can go on for a very long time. I’ve seen it take 10 years. And by the time it’s
done, the original members of the tiger team are long gone, and the current members are
demanding that the new system be redesigned because it’s such a mess.

> If you have experienced even one small part of the story I just told, then you already
know that spending time keeping your code clean is not just cost effective; it’s a matter of
professional survival.

Managers don't know everything, so they need you to say what's important. They won't
fire you if you defend the code quality, no matter the schedule. The snippet below
describes it better.

> “But wait!” you say. “If I don’t do what my manager says, I’ll be fired.” Probably not.
Most managers want the truth, even when they don’t act like it. Most managers want good
code, even when they are obsessing about the schedule. They may defend the schedule and
requirements with passion; but that’s their job. It’s your job to defend the code with equal
passion.

> To drive this point home, what if you were a doctor and had a patient who demanded
that you stop all the silly hand-washing in preparation for surgery because it was taking
too much time? Clearly the patient is the boss; and yet the doctor should absolutely refuse
to comply. Why? Because the doctor knows more than the patient about the risks of disease
and infection. It would be unprofessional (never mind criminal) for the doctor to
comply with the patient.

> So too it is unprofessional for programmers to bend to the will of managers who don’t
understand the risks of making messes.

The snippet below is a curious example of why quality and care is more important than speed.

> When hand-washing was first recommended to physicians by Ignaz Semmelweis in 1847, it was
rejected on the basis that doctors were too busy and wouldn’t have time to wash their hands
between patient visits.

The metaphor of broken windows is good example of why the the code base should be well written
from the very start.

> [...] They used the metaphor of broken windows. A building with broken windows looks like
nobody cares about it. So other people stop caring. They allow more windows to become
broken. Eventually they actively break them. They despoil the facade with graffiti and
allow garbage to collect. One broken window starts the process toward decay.

Interesting definition of clean code, described by Michael Feathers.

> I could list all of the qualities that I notice in
clean code, but there is one overarching quality
that leads to all of them. ***Clean code always
looks like it was written by someone who cares***.
There is nothing obvious that you can do to
make it better. All of those things were thought
about by the code’s author, and if you try to
imagine improvements, you’re led back to
where you are, sitting in appreciation of the
code someone left for you - code left by someone
who cares deeply about the craft.

We read much more code than we write it, so making it easy to read actually makes it
easier to write. See the snippet below.

> [...] Indeed, the ratio of time spent reading vs. writing is well over 10:1.
We are constantly reading old code as part of the effort to write new code.
Because this ratio is so high, we want the reading of code to be easy, even if it makes
the writing harder. Of course there’s no way to write code without reading it, so making
it easy to read actually makes it easier to write.

## Unit Tests

**Laws of TDD**
  1. You may not write production code until you have written a failing unit test.
  2. You may not write more of a unit test than is sufficient to fail.
  3. You may not write more production code than is sufficient to pass the currently failing test.

The tests and the production code must be ***written at the same time***.

Test code is just as important as production code. You don't have the same concerns about
perfomance as in a production environment, so tests should be ***as readable as possible***.
Sometimes it's better to create functions and utilities designed to be used by the tests,
rather than using APIs that programmers use to manipulate the system.

It is unit tests that ***allow changes*** and keep our code flexible, maintainable, and reusable.
If you have tests, you do not fear making changes to the code!

**BUILD-OPERATE-CHECK** - A test-structuring method in which tests should be splitted in three parts:
1. Build up the test data.
2. Operate on that test data.
3. Check that the operation yielded the expected results.

A good rule for writing unit tests is test just one concept per test function and
minimize the number of asserts.

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

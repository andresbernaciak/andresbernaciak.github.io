# Building a Family AI Chief of Staff: Starting with the Inbox

Household coordination is a surprisingly messy operating problem.

School communications, sports schedules, permission slips, activity reminders, deadlines, and PTO requests arrive through different channels (email/apps), at different times, and sometimes more than once (multiple kids anyone?). The challenge is making sure nothing falls through the cracks—especially when two parents receive the same notifications—and consistently turning all of that information into a reliable answer to a few basic questions:

* What is happening?
* When is it happening?
* What needs to be done?
* By when?
* Who needs to do it?
* Is anything unclear?

I'm building a small AI-enabled workflow to explore whether an LLM can help turn that fragmented information into a more useful household operating system.

## Starting deliberately small

The long-term idea could include email ingestion, calendars, recurring briefs, ownership, proposed actions, and eventually more agentic behavior. It could also be run locally with an open-weight model at no cost (excluding the hardware and electricity required to operate it).

But that is not V0.

The first question is much simpler:

> Can an LLM reliably convert an unstructured school or activity email into structured events, deadlines, and actions?

The initial architecture is intentionally basic:

```text
Synthetic email
      ↓
Python
      ↓
OpenAI API
      ↓
Structured extraction
      ↓
Events | Deadlines | Actions
```

There is no Gmail integration yet. There is no database. Nothing writes to a calendar, sends a message, or takes an autonomous action.

The goal is first to determine whether the core interpretation step works.

## Defining the output before building the workflow

Before making the first API call, I defined three basic objects.

An **event** is something that will happen, such as a field trip or hockey practice.

A **deadline** represents when something must happen, such as returning a permission slip.

An **action** represents work somebody actually needs to perform, such as completing the permission slip or preparing a lunch.

This creates an interesting distinction. The same communication might generate both:

```text
Deadline
Permission slip due September 10

Action
Complete and return permission slip by September 10
```

That looks redundant from an information-extraction perspective, but it is not redundant operationally. One represents time. The other represents work.

## Designing for uncertainty

I also chose not to ask the model for a numeric confidence score.

Instead, every extracted item can be flagged as requiring human review, along with the reason.

For example, a message sent to all Grade 6 families may clearly describe a field trip without identifying which child in a household it applies to.

The system should not guess.

That distinction will become more important as the workflow eventually moves from simply extracting information toward proposing or taking actions.

## Making the output testable

The first inputs are synthetic emails rather than messages from a real inbox.

For each email, I am also manually defining the expected events, deadlines, and actions before running the model.

That creates a simple evaluation set.

Instead of asking whether the AI output "looks right," I can begin asking more useful questions:

* Did it miss an action?
* Did it invent one?
* Did it resolve the date correctly?
* Did it identify conditional actions correctly?
* Did it flag genuine ambiguity?
* Does a smaller, less expensive model perform well enough?

That evaluation layer will become increasingly important as the workflow gets more capable.

## Next

The first implementation uses the OpenAI API with structured outputs and a typed schema so that the output can feed directly into software rather than remaining free-form text.

The immediate next step is to run the first set of synthetic communications through the extraction layer, compare the results with the expected outputs, and start documenting where the system succeeds and fails.

From there, the architecture can start getting more complex as I continue to build.

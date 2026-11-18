<!--
Template for one architecture decision record, adr-<slug>.md. Delete every
comment block before committing.

The slug names the decision and is unique in the tree; it carries no date and
no sequence number. The record states the current decision and is revised in
place when that decision changes: rewrite it, retitle it, rename the file,
then recheck every document that cites it.

Revising leaves no trace in the record -- no revision note, no date, no
"originally". A displaced decision survives only as a rejected option in
Options Considered. There is no status field: the tree holds only decisions in
force. One decision per record. Write it impersonally -- "Adopt X", never "We
decided to adopt X".
-->

# <Decision title>

## Context

<The forces that made a decision necessary: the constraints in play, what was
blocked, what had to be true. Facts, not narrative -- do not recount how the
problem came to attention.>

## Options Considered

<!--
Every option that lost carries a verdict and its reason. An option listed
with no reason is decoration: it makes the record look thorough while
carrying nothing a future reader can use.

The verdict is Rejected or Not adopted (Chinese: 否决, 未采纳), and the two
differ in whether the option was judged wrong. Rejected: adopting it would
break a constraint, or it cannot coexist with the option adopted. Not
adopted: it is compatible with the option adopted and was left out because
the decision does not need it at its present scope. A not-adopted option
states the constraint that kept it out and may say it can be added without
displacing the decision; it names no stage and promises nothing. When it
should be taken up goes in Invalidation Conditions, as an observable
condition.

This is the only place a displaced decision may appear: as an alternative that
lost, with its rejection reason. No revision narrative.

An option that adopts a public external component or follows a published
design cites it (REF-<slug>) at its first mention, so a reader can tell a
candidate taken from outside from one designed in-house.
-->

### <Option A>

<What adopting it would have meant.>

**Rejected**: <why>

### <Option B>

<What adopting it would have meant.>

**Not adopted**: <the constraint that kept it out>. <It is compatible with
the option adopted and can be added without displacing this decision.>

### <Option C>

<What adopting it means.>

**Adopted** — see Decision.

## Decision

Adopt <X>.

## Consequences

<What the project is now committed to.>

<!--
Costs are mandatory. Every architectural decision buys something at a price,
and the price is the part a future reader needs in order to judge whether the
trade still holds. A record listing only benefits is unusable for that.
-->

**Costs accepted:**

- <what this gives up, and who will encounter it>

<!--
Optional. Delete this section when the decision rests on no assumption that
can be checked later.
-->
## Invalidation Conditions

<What would show this decision to have been wrong: the measurement that would
contradict it, the scale at which it stops holding, the assumption whose
failure undoes it.>

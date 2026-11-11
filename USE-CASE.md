# One subscriber wins $1 million. How can anyone check?

In this fictional MrBeast-style giveaway, eight subscribers each hold one numbered ticket. An entrant who sees only an announcement has to take the organizer's word for who won. Proof of Draw lets an entrant, a journalist, or the organizer replay exactly how the published number selects a ticket. It has no affiliation with MrBeast and offers no prize.

## What a real organizer would publish

1. Close entries and post an ordered list of opaque ticket IDs. Give each subscriber their own ID privately and time to check that it appears once.
2. Before the random value exists, publish a timestamped, independently preserved copy of that list, the selection rule, the beacon name, and the exact future round. For example, choose in advance to cancel the draw if that round has no usable output. Choosing another round after seeing the result would let the organizer influence the outcome.
3. After the round, publish the record and announced ticket. Anyone can repeat the same calculation. An organizer should also keep separate evidence of eligibility and prize delivery.

## The eight-ticket demonstration

Three binary digits encode eight possibilities, from 000 to 111. Each has one ticket. Read the first three bits of the published output, interpret them as a number from zero to seven, then add one. In CURBy-Q round 28297, the first byte is 61 in hexadecimal, or 01100001 in binary. Its first three bits, 011, select ticket #4. Switch the announcement to #7 to see the discrepancy.

The demo uses an archived round so two judges can reproduce the same result. The ticket list and rules were created after the archive existed. A real drawing needs the earlier public commitment described above.

## What quantum contributes

Ordinary software can implement the verifier. A classical public beacon could supply a replayable number too. CURBy-Q adds physical evidence about unpredictability through measurements on entangled photons, statistical analysis, and randomness extraction. Our local two-qubit Qiskit simulation illustrates the physics and its sensitivity to errors. The public archive supplies the actual draw value.

## What it would take to use this at scale

The demo covers a fixed list of eight. For other list sizes, publish a rule that gives each ticket the same chance. For ten tickets, for example, read four bits at a time, accept 0 through 9 and skip 10 through 15. Specify ahead of time how to continue if the record runs out. A production system would also need verifiable list publication, private eligibility checks, a way to dispute omissions, and independent checks of the beacon's provenance.

Sources: [Archived round 28297](https://random.colorado.edu/api/curbyq/round/28297) · [NIST's account of the physical beacon](https://www.nist.gov/news-events/news/2025/06/nist-and-partners-use-quantum-mechanics-make-factory-random-numbers).

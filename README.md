# Proof of Draw

A creator announces the winner of a fictional $1 million subscriber giveaway. Can any of the eight ticket holders check the announcement? The verifier replays a fixed ticket list, a public selection rule and an archived randomness pulse.

[Try the live verifier](https://ikr0me.github.io/proof-of-draw/) · [Watch the 1 min 42 sec demo](https://ikr0me.github.io/proof-of-draw/demo.mp4)

## Try the verifier

Download [index.html](index.html) and open it in a browser. Select **#4** and click **Verify winner**. Repeat with **#7**. CU Boulder’s archived round 28297 starts with the byte `01100001`. The first three bits, `011`, select position 3 in a list counted from zero, which holds ticket **#4**. The checker accepts #4 and rejects #7 against the same receipt. [Original beacon record](https://random.colorado.edu/api/curbyq/round/28297)

For the entrant's perspective and the rules a real organizer would need, read the [use case](USE-CASE.md). The [one-page judge Q&A](Judge-QA.pdf) covers the classical alternative, the quantum contribution and the limits of this receipt.

## Reproduce the evidence

1. Keep [ProofOfDraw.ipynb](ProofOfDraw.ipynb) and [curbyq-round-28297.json](curbyq-round-28297.json) in the same folder. The notebook includes the results from the verified run.
2. In a Python environment for Jupyter or VS Code, run `python -m pip install -r requirements.txt` from that folder. Select the same environment as the notebook kernel and **Run All**. The recorded run used CPython 3.9.6, Qiskit 1.4.5 and NumPy 2.0.2. The browser verifier and notebook receipt use the bundled archive and work offline.
3. In the notebook, change `announced_ticket` and rerun the claim cell. The full test covers all 256 first bytes. Each of the eight tickets is selected by 32 bytes. All seven incorrect claims fail for the archived round.

## Where quantum enters

CU Boulder and NIST collect physical Bell-test data and extract randomness from those measurements. The app consumes a published pulse. The Qiskit notebook illustrates the underlying idea with the two-player CHSH game. Both players receive a private bit and answer without communicating. [Beacon experiment](https://doi.org/10.1038/s41586-025-09054-3) · [IBM’s CHSH lesson](https://quantum.cloud.ibm.com/learning/en/courses/basics-of-quantum-information/entanglement-in-action/chsh-game)

The best of all 16 classical plans wins **75%**. The seeded, ideal Qiskit simulation won **6,845/8,000 trials (85.56%)**, with a 95% Wilson interval of **84.78%–86.32%** for sampling uncertainty. The circuit’s exact win probability is **85.36%**. In the model where each player’s answer independently flips, the expected win rate reaches 75% at **7.96%** error per answer.

## Limits and credit

A classical public beacon could also support replay. A real organizer would need to publish the eligibility policy, ordered list, selection rule, exact future round and fallback policy before the draw. This retrospective example checks the announced winner against the supplied inputs. Audience eligibility, advance publication and prize delivery require separate evidence. The rule handles exactly eight distinct tickets. The source of the archived pulse is CU Boulder. The seeded Qiskit run took place on a classical computer and provides an illustration of Bell correlations. Independent verification of the original physical experiment and its certification falls outside this demo. [NIST guidance on public draws](https://csrc.nist.gov/projects/interoperable-randomness-beacons/apps) · [CU Boulder beacon](https://random.colorado.edu/)

The CHSH strategy follows IBM Quantum Learning. The project adds the giveaway verifier, archived receipt, exhaustive ticket checks and a simulated error experiment. OpenAI Codex assisted with implementation, documentation, video production and verification. The narration uses the ElevenLabs stock voice Ainsley via Higgsfield. [IBM circuit example](https://quantum.cloud.ibm.com/learning/en/courses/basics-of-quantum-information/entanglement-in-action/qiskit-implementation)

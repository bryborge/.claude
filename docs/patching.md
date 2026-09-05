# Patching in Tests

**Monkeypatching is a smell. It's a signal about the code, not a routine test tool.**

Reaching for `monkeypatch`, `mock.patch`, or any runtime rebinding says the code has a
hard-wired dependency the test can't reach from the outside. Sometimes that's true. Work
down this list and stop at the first thing that works:

- Can real input values drive the code down the branch you want? Use them.
- Can you pass a stub *in* — an argument, a fake collaborator, a fixture object — rather
  than reaching in and rewriting a global? Do that.
- Is the thing genuinely uncontrollable from outside — wall-clock time, randomness,
  network, filesystem, hardware? Patch it. That's what the technique is for.

Add a patch only once you've watched it fail without one. Before keeping any patch, prove
it's load-bearing: replace it with something that fails loudly
(`lambda *_: pytest.fail("called")`) and run the suite. If the suite still passes, the
patch was never on the path — delete it.

When a patch is genuinely required, name in your response what design forced it. "I had to
patch X" is a finding about the code worth surfacing, not a test detail to bury.

# ProofGuard · Live Demo (AI-FEST 2026)

A single-file front-end demo. No install, no build step.

## Run
- Double-click `index.html`, or
- `python -m http.server 8000` in this folder, then open http://localhost:8000

## What is inside `index.html`
- `C` array: the 5 scripted cases (algebra, calculus, linear algebra, clean control, abstention).
  Each step has a status: ok, bad, unv (UNVERIFIED) or inh (inherits an earlier error).
- Pipeline animation: Parse (Gemini) -> Verify (SymPy) -> Locate first error -> Explain.
- Live equivalence checker (section 2): real JavaScript, samples random and special points.

## Connect it to your real FastAPI backend
Replace the scripted case with a call, for example:

    const r = await fetch("http://localhost:8000/verify", {
      method: "POST", headers: {"Content-Type": "application/json"},
      body: JSON.stringify({ problem: q, solution: text })
    });
    const data = await r.json(); // expect: steps[{text,status,evidence}], first_error, explanation, fix

Keep the same status names (ok / bad / unv / inh) and the UI renders it unchanged.
Verdicts must come from SymPy; Gemini only parses and explains.

## Before you present
The 5 cases are scripted illustrations. Report real accuracy from your own labelled test set.

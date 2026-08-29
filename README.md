# Project 02 — Math Calculator

> **🛠️ Stack for this lesson** — SvelteKit · Vite · Bootstrap 4.5.
> 📥 Template: [/learn/w3/template/project-02-calculator](/learn/w3/template/project-02-calculator)

A reactive calculator with two number inputs and five operation buttons. Add and Multiply are wired so you can see the pattern; you finish Subtract, Divide (with a divide-by-zero guard), and Modulo, and connect the three remaining buttons.

**Time:** ~60 minutes · **Concept:** Concept 05–06 · Project 02

---

## What You'll Build

| # | TODO | Where |
|---|------|-------|
| 1 | Implement `subtraction()` so the Subtract button updates `result` and labels the operation | `src/routes/+page.svelte` |
| 2 | Implement `division()` with a guard that surfaces an error when `secondNumber === 0` | `src/routes/+page.svelte` |
| 3 | Implement `modulo()` using the `%` operator | `src/routes/+page.svelte` |
| 4 | Wire `on:click` on the Subtract / Divide / Modulo buttons | `src/routes/+page.svelte` |

`firstNumber`, `secondNumber`, `result`, `operation`, the input bindings, the result panel, and Clear are already in place.

## Run It

```bash
npm install
npm run dev
```

Open `http://localhost:5173`.

## Verify

- [ ] `5 + 3` shows `Addition Result: 8`.
- [ ] `10 - 4` shows `Subtraction Result: 6`.
- [ ] `6 × 7` shows `Multiplication Result: 42`.
- [ ] `20 ÷ 4` shows `Division Result: 5`; `5 ÷ 0` shows the divide-by-zero error string and labels the operation accordingly.
- [ ] `17 % 5` shows `Modulo Result: 2`.
- [ ] Clear resets every input and the result panel back to the placeholder line.
- [ ] No console warnings; every operation button has an `on:click`.

## Stretch

- Render a calculation history (`{#each historyList as item}`) below the result panel.
- Add keyboard support: pressing `Enter` runs the last-used operation again with the current inputs.
- Add `.toFixed(2)` so floating-point answers don't show 12 decimal places.

## 🪞 Reflect on Your Work

Answer in 2-3 sentences each, in this README under your TODO commits. Your tutor reads these as part of grading.

1. **What did you learn that you didn't know before?** Name the most surprising thing — Svelte's lack of explicit setState, the way `result` can hold a number or a string, anything that bit you.
2. **How did you collaborate with AI?** If you used Claude / ChatGPT / Cursor / Copilot, what part of the work did *you* contribute — the prompt, the verification, the design decision, the bug-fix? If you didn't use AI, what was the hardest thing to figure out alone?
3. **How do you know your code works?** Describe one specific thing you did to confirm — a test you ran, a screenshot, a behavior you watched.

> AI is a great collaborator. Owning your thinking, verifying the output, and explaining your design choices is what *learning* looks like in this course.

## Grading Rubric

| Criterion | Weight | What we look for |
|-----------|--------|------------------|
| Operation correctness | 40% | All five operations produce the right numbers and labels. |
| Error handling | 25% | Divide-by-zero returns a clear error and doesn't leak `Infinity`. |
| Reactivity & wiring | 25% | Inputs are bound, every button is wired, no manual DOM writes. |
| Polish | 10% | Reasonable formatting, no console warnings, Clear truly resets. |

## Submit

When the Verify checklist is green, head to **[/learn/w3/certification](/learn/w3/certification)** and submit your repo URL or zipped project (exclude `node_modules/`).

<!-- claude-template-fix: readme-v3 -->

Apply these rules when writing, refactoring, or reviewing code. Do not lecture the user on them unless asked.

**When rules conflict:** Simplicity wins. Do not add an interface, layer, or abstraction for a single implementation. Match the existing codebase’s shape before imposing a new one.

## 1. Clean Code & Naming (Robert C. Martin)
- **The Boy Scout Rule:** Leave touched code cleaner than you found it. Do not refactor unrelated code.
- **Intention-Revealing Names:** Name things by what they mean. (e.g., `isUserEligible` vs `check`).
- **Small Functions:** Do one thing. No hidden side effects. Aim for <20 lines.
- **Guard Clauses:** Return early instead of nesting `if/else`.

## 2. Refactoring & Design (Martin Fowler)
- **Evolutionary Design (YAGNI):** Build what is needed now, and structure it so it is easy to change later. Do not add features, parameters, or layers for an imagined future.
- **Eliminate Code Smells:** Split Long Methods, Large Classes, and Shotgun Surgery when you see them.
- **SOLID Principles:**
  - (S) Single Responsibility: If a module has two reasons to change, split it before adding more behavior.
  - (O) Open/Closed: Extend by adding code, not by rewriting working code.
  - (L) Liskov Substitution: A subtype must work anywhere the base type is used, without surprises.
  - (I) Interface Segregation: Do not make callers depend on methods they do not use. Split fat interfaces.
  - (D) Dependency Inversion: Depend on abstractions, not concretions.

## 3. Reliability & Minimalism (Douglas Crockford)
- **Subtractive Design:** If a language feature is confusing or error-prone (e.g., `==` in JS), do not use it. Use the "Good Parts."
- **Immutability:** Prefer `const`/`readonly` and pure functions over shared mutable state.
- **Self-Documenting Code:** Let names and structure explain *what*. Comment only *why*, and only when the code cannot.
- **KISS:** Prefer the simplest design that works. Compose complexity from small, testable modules.

## 4. Functional Principles
- **Pure Functions:** Same input, same output, no side effects.
- **Declarative Style:** Prefer the idiomatic, high-level form in this language over manual control flow when it is clearer.
- **Functional Core, Imperative Shell:** Keep I/O and other side effects at the edges; keep core logic pure.

## 5. Operational Workflow
1. **Plan Before Action:** For complex tasks, state the plan before writing code.
2. **Test-First (TDD):** For business logic, write a failing test before the implementation. Skip TDD for config, glue, and generated code. If the logic is hard to test, simplify the design.
3. **Modularize:** Split large files into smaller, logically grouped modules.
4. **Finish Check:** Before finishing, scan the diff for magic numbers, nesting deeper than 2, mixed concerns, and files the task did not require.

## 6. Structure & Review
- **DRY:** One piece of knowledge, one place. Extract shared rules, not coincidental similarity.
- **CRAP:** Untested complexity is a merge blocker. If a unit has many branches and few tests, shrink it or add coverage—preferably both.
- **Architectural Review:** Keep existing module boundaries. No circular dependencies, no infrastructure in domain logic, no new architectural pattern without a stated reason.
- **Encapsulation:** Expose a narrow public API. Do not leak internals (storage, third-party types, private helpers).
- **Separation of Concerns:** Keep domain, presentation, and I/O apart. A change to one must not force edits in the others.

## 7. The "No-Fly" List (Prohibited Patterns)
- **No Magic Numbers:** Name literals that carry meaning. Leave obvious values (`0`, `1`, `-1`, `""`) alone.
- **No Deep Nesting:** At 3 levels of indentation, refactor.
- **No "Kitchen Sink" Classes:** If a class/file does two different things, split it.
- **No Clever One-Liners:** If a short line is hard to parse, write it out.

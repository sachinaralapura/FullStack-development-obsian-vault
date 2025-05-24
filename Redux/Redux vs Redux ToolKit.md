### Redux (Core Library)

Redux, at its heart, is a **predictable state container for JavaScript applications**. It provides a minimal API and a set of principles

- **Single Source of Truth:** Your entire application's state is stored in a single, plain JavaScript object tree within a single store.
- **State is Read-Only:** The only way to change the state is by emitting an `action`, a plain JavaScript object describing what happened.
- **Changes are Made with Pure Functions (Reducers):** Reducers are pure functions that take the current state and an action, and return a _new_ state. They must not mutate the original state.
# State Management with NgRx in Angular

NgRx is a state management library for Angular applications inspired by Redux. It provides a predictable state container for managing application state in a way that makes debugging and testing easier. NgRx follows the principles of reactive programming with the use of RxJS and is highly useful in large-scale Angular applications that require centralized state management.

---

## 🧠 Mind Map

**NgRx State Management**:

- **Store**: A central container of application state.
- **Actions**: Describes an event or change in the application state.
- **Reducers**: Pure functions that specify how the state should change in response to actions.
- **Selectors**: Functions that help retrieve slices of the state.
- **Effects**: Side-effects such as HTTP calls, data fetching, or other async operations.
- **Entity State**: Pattern for managing collections of data entities in the store.

---

## 🧑‍💻 Key Technical Words & Definitions

1. **Store**: A container for all the application state. It is the single source of truth in an NgRx application. The store is updated via dispatched actions and updated by reducers.

2. **Actions**: Events that describe changes to the application state. Actions are dispatched to trigger a state change. Actions contain a `type` property and an optional `payload`.

3. **Reducers**: Functions that specify how the state is updated in response to an action. Reducers are pure functions that take the current state and an action, returning a new state.

4. **Selectors**: Functions that provide a way to select specific slices of the state from the store. Selectors can be composed and combined for efficient state selection.

5. **Effects**: Used to handle side-effects like HTTP requests, interacting with external APIs, or other asynchronous operations that affect the state. Effects listen for actions and dispatch new actions based on async events.

6. **Entity State**: A way to handle collections of data entities (e.g., users, products) in the state by storing them in a normalized format to improve performance and make updates easier.

7. **NgRx DevTools**: A set of browser extensions to inspect and debug the NgRx store in an Angular application. It provides powerful insights into dispatched actions, state changes, and timing.

8. **Action Creators**: Functions that help create action objects in a concise and readable way, improving code maintainability.

9. **Store Modules**: NgRx modules that are used to organize the state into feature-based modules, allowing for more modular and scalable state management.

---

## 🎯 Common Interview Questions

1. **What is NgRx, and why should you use it in Angular?**
   - NgRx is a state management library for Angular that uses RxJS and Redux principles to manage and update state in a predictable and scalable way. It is useful in large-scale applications that require centralized state management.

2. **How does NgRx store the application state?**
   - NgRx stores the application state in a single immutable state object, which is managed through actions, reducers, and selectors. This ensures a predictable flow of state changes.

3. **What is the purpose of `Actions` in NgRx?**
   - Actions describe events that trigger state changes. They are dispatched to the store, and reducers handle them to modify the state accordingly.

4. **Explain the concept of reducers in NgRx.**
   - Reducers are pure functions that receive the current state and an action, and return a new state. They specify how the state should change in response to an action.

5. **What are selectors in NgRx?**
   - Selectors are functions that allow components to retrieve slices of state from the store. They help improve performance and reusability by avoiding the need for direct access to the state object.

6. **How do Effects work in NgRx?**
   - Effects are used to handle side-effects, such as API calls or other asynchronous operations, and to dispatch additional actions. They are typically used for actions that don't directly modify the state but trigger external changes.

7. **What is `Entity State` in NgRx, and why is it useful?**
   - `Entity State` is a pattern that stores collections of data entities in a normalized format in the store. It is useful for managing large datasets efficiently and allows easy additions, deletions, and updates.

---

## 💻 Code Snippet

### Defining Actions in NgRx

```typescript
import { createAction, props } from '@ngrx/store';

export const loadUsers = createAction('[User API] Load Users');
export const loadUsersSuccess = createAction(
  '[User API] Load Users Success',
  props<{ users: User[] }>()
);
export const loadUsersFailure = createAction(
  '[User API] Load Users Failure',
  props<{ error: string }>()
);
```

### Creating Reducers in NgRx

```typescript
import { createReducer, on } from '@ngrx/store';
import { loadUsers, loadUsersSuccess, loadUsersFailure } from './user.actions';

export interface UserState {
  users: User[];
  error: string | null;
}

export const initialState: UserState = {
  users: [],
  error: null,
};

export const userReducer = createReducer(
  initialState,
  on(loadUsers, state => ({ ...state })),
  on(loadUsersSuccess, (state, { users }) => ({ ...state, users })),
  on(loadUsersFailure, (state, { error }) => ({ ...state, error }))
);
```

### Defining Selectors in NgRx

```typescript
import { createFeatureSelector, createSelector } from '@ngrx/store';
import { UserState } from './user.reducer';

export const selectUserState = createFeatureSelector<UserState>('users');

export const selectAllUsers = createSelector(
  selectUserState,
  (state: UserState) => state.users
);

export const selectUserError = createSelector(
  selectUserState,
  (state: UserState) => state.error
);
```

---

## 📝 Best Practices Summary

1. **Use `Action Creators`**: Always use `createAction()` and `createReducer()` for creating actions and reducers. This makes the code more readable and maintainable.

2. **Avoid Direct Mutation**: Never directly mutate the state. Always return a new state object in the reducers. This ensures immutability and avoids unexpected bugs.

3. **Use Selectors for State Access**: Use selectors to access the state in your components rather than directly accessing the store. This improves performance and reusability.

4. **Organize State by Feature**: Use feature-based store modules for scalability. Organize your state, actions, and reducers by the features of your application.

5. **Use NgRx DevTools**: Leverage NgRx DevTools to inspect the state and dispatched actions during development. This helps debug issues faster.

6. **Avoid Complex Effects**: Keep your effects simple and focused on handling side-effects like API calls or event-driven actions. Avoid putting too much logic inside effects.

---

## 📋 Cheat Sheet Summary

- **Store**: Central container of application state.
- **Actions**: Events describing changes to state.
- **Reducers**: Pure functions that update state based on actions.
- **Selectors**: Functions to select slices of the state.
- **Effects**: Handle side-effects like HTTP requests and asynchronous operations.
- **Entity State**: Pattern to manage collections of data entities efficiently.

---

## ⚡ Common Mistakes

1. **Not Using Immutable State**: Always avoid direct mutation of the state in reducers. Always return a new state object.

2. **Overcomplicating Reducers**: Keep reducers simple and focused on updating state. Avoid putting business logic inside reducers.

3. **Not Using Selectors**: Accessing state directly in components without selectors can lead to inefficient rendering and tight coupling. Use selectors for state access.

4. **Ignoring NgRx DevTools**: Not using NgRx DevTools can make debugging and inspecting state changes more difficult, especially in large applications.

---

## 🔍 Further Reading

- [NgRx Documentation](https://ngrx.io/docs)
- [Angular State Management with NgRx](https://angular.io/guide/ngrx)
- [NgRx Store Example](https://github.com/ngrx/platform)
- [NgRx DevTools](https://github.com/ngrx/platform/tree/master/projects/store-devtools)

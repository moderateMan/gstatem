React GStatem is a small, simple and fast state-management tool.

[![Build](https://github.com/gstatem/gstatem/actions/workflows/build.yml/badge.svg)](https://github.com/gstatem/gstatem/actions/workflows/build.yml)

## Installation
### npm
```shell
npm i react-gstatem
```

### yarn
```shell
yarn add react-gstatem
```

### [Demos](https://gstatem.netlify.app/)

## Basic usage of function component
### Create a store
```typescript jsx
// Store.js
import { create } from "react-gstatem";

const { useSelect, dispatch } = create({
  /* initial state */
  state: { count: 0 }
});

/* the count hook for function component */
export const useCount = () => useSelect<number>(state => state.count);

/* update the store with callback */
export const increaseCount = () => dispatch(state => ({ count: state.count + 1 }));
```

### <a name="useincomponent" />Use the store in component
```typescript jsx
import React from "react";
import Counter from "./Counter";
import { increaseCount, resetCount, useCount } from "./Store";

const BasicUsage = () => {
  const count = useCount();
  return (
    <Counter value={count} onIncrement={increaseCount} />
  );
};

export default BasicUsage;
```
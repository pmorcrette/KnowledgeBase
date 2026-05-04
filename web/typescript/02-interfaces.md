# Interfaces

Interfaces define object shapes and contracts. Related: [Types](01-types.md), [Classes](03-classes.md).

## Basic Interface

```typescript
interface User {
    name: string;
    age: number;
    email?: string;    // Optional property
    readonly id: number;  // Readonly
}

const user: User = {
    name: "Alice",
    age: 30,
    id: 1
};
```

## Interface Methods

```typescript
interface Calculator {
    add(a: number, b: number): number;
    subtract(a: number, b: number): number;
}

const calc: Calculator = {
    add(a, b) { return a + b; },
    subtract(a, b) { return a - b; }
};
```

## Extending Interfaces

```typescript
interface Animal {
    name: string;
}

interface Dog extends Animal {
    breed: string;
}
```

## Declaration Merging

```typescript
interface User {
    name: string;
}

interface User {
    age: number;
}

// Combined: { name: string; age: number }
```

## Function Interfaces

```typescript
interface SearchFn {
    (source: string, sub: string): boolean;
}

const contains: SearchFn = (src, sub) => 
    src.indexOf(sub) >= 0;
```
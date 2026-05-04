# Functions

Function types and patterns in TypeScript. Related: [Types](01-types.md), [Generics](05-generics.md).

## Function Types

```typescript
// Named function
function add(a: number, b: number): number {
    return a + b;
}

// Arrow function
const add = (a: number, b: number): number => a + b;

// Function type
let add: (a: number, b: number) => number;
add = (a, b) => a + b;
```

## Optional Parameters

```typescript
function greet(name: string, greeting?: string): string {
    return `${greeting ?? "Hello"}, ${name}`;
}
greet("Alice");
greet("Alice", "Hi");
```

## Default Parameters

```typescript
function greet(name: string, greeting: string = "Hello"): string {
    return `${greeting}, ${name}`;
}
```

## Rest Parameters

```typescript
function sum(...nums: number[]): number {
    return nums.reduce((a, b) => a + b, 0);
}
```

## Overloads

```typescript
function getItem(id: string): { id: string };
function getItem(id: number): { id: number };
function getItem(id: string | number): { id: string | number } {
    return { id };
}
```

## This Parameter

```typescript
function log(this: void): void {
    console.log(this);
}
```

## Generic Functions

```typescript
function first<T>(arr: T[]): T {
    return arr[0];
}
first([1, 2, 3]);  // number
first(["a", "b"]);  // string
```
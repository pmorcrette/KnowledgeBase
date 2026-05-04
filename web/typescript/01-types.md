# Types

TypeScript's basic and composite types. Related: [Interfaces](02-interfaces), [Functions](04-functions).

## Basic Types

```typescript
// Primitive types
let str: string = "hello";
let num: number = 42;
let bool: boolean = true;

// Null and undefined
let n: null = null;
let u: undefined = undefined;
```

## Arrays

```typescript
// Two syntaxes
let arr: string[] = ["a", "b", "c"];
let arr2: Array<number> = [1, 2, 3];
```

## Objects

```typescript
// Object type
let obj: { name: string; age: number } = {
    name: "Alice",
    age: 30
};
```

## Any and Unknown

```typescript
// Any - opt out of type checking
let anything: any = "hello";
anything = 42;

// Unknown - type-safe any
let something: unknown = "hello";
if (typeof something === "string") {
    something.toUpperCase(); // OK
}
```

## Void and Never

```typescript
// Void - no return value
function log(msg: string): void {
    console.log(msg);
}

// Never - never returns
function error(msg: string): never {
    throw new Error(msg);
}
```

## Type Aliases

```typescript
type Point = { x: number; y: number };
type ID = string | number;

let p: Point = { x: 1, y: 2 };
let id: ID = 123;
```
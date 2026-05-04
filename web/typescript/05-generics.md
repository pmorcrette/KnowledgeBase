# Generics

Reusable components with TypeScript generics. Related: [Functions](04-functions.md), [Advanced](10-advanced.md).

## Generic Functions

```typescript
function identity<T>(value: T): T {
    return value;
}

identity<string>("hello");  // explicit
identity("hello");       // inferred
```

## Generic Interfaces

```typescript
interface Container<T> {
    value: T;
    get(): T;
}

class Box<T> {
    constructor(public value: T) {}
    get(): T {
        return this.value;
    }
}
```

## Generic Constraints

```typescript
interface HasLength {
    length: number;
}

function logLength<T extends HasLength>(item: T): void {
    console.log(item.length);
}

logLength("hello");
logLength([1, 2, 3]);
```

## Multiple Type Parameters

```typescript
function pair<K, V>(key: K, value: V): { key: K; value: V } {
    return { key, value };
}
```

## Default Types

```typescript
interface Result<T = string> {
    data: T;
    status: number;
}
```

## Utility Types

```typescript
interface User {
    id: number;
    name: string;
}

// Partial - all optional
type PartialUser = Partial<User>;

// Required - all required
type RequiredUser = Required<User>;

// Pick - select properties
type UserPreview = Pick<User, "id" | "name">;

// Omit - exclude properties
type WithoutId = Omit<User, "id">;

// Record
type UserMap = Record<string, User>;
```
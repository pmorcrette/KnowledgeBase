# Advanced Types

Advanced TypeScript patterns.

## Intersection Types

```typescript
interface A {
    a(): void;
}

interface B {
    b(): void;
}

type AB = A & B;

const obj: AB = {
    a() { },
    b() { }
};
```

## Conditional Types

```typescript
type IsString<T> = T extends string ? true : false;
type Test = IsString<string>;  // true
type Test2 = IsString<number>; // false
```

## Mapped Types

```typescript
type Readonly<T> = {
    readonly [P in keyof T]: T[P];
};

type Optional<T> = {
    [P in keyof T]?: T[P];
};
```

## Template Literals

```typescript
type EventName = `on${Capitalize<string>}`;
type Handler = `handle${Capitalize<string>}`;
```

## Type Inference

```typescript
type ReturnType<T> = T extends (...args: any[]) => infer R ? R : never;

type Fn = () => number;
type R = ReturnType<Fn>;  // number
```

## Non-null Assertion

```typescript
function getElement(id: string): HTMLElement | null {
    return document.getElementById(id);
}

const el = getElement("app")!;  // Non-null assertion
```

## Type Assertions

```typescript
const el = document.getElementById("app") as HTMLElement;
const el2 = <HTMLElement>document.getElementById("app");
```
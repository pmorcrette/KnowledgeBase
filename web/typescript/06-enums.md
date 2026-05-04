# Enums and Type Guards

Constants and discriminated unions. Related: [Types](01-types.md), [Advanced](10-advanced.md).

## Numeric Enums

```typescript
enum Color {
    Red,    // 0
    Green,   // 1
    Blue    // 2
}

enum Color {
    Red = 1,
    Green = 2,
    Blue = 4
}
```

## String Enums

```typescript
enum Direction {
    Up = "UP",
    Down = "DOWN",
    Left = "LEFT",
    Right = "RIGHT"
}
```

## Const Enums

```typescript
const enum Status {
    Active = "ACTIVE",
    Inactive = "INACTIVE"
}

Status.Active;  // inlined at compile
```

## Type Guards

```typescript
function isString(val: unknown): val is string {
    return typeof val === "string";
}

function process(val: string | number) {
    if (isString(val)) {
        val.toUpperCase();  // TypeScript knows it's string
    }
}
```

## Narrowing

```typescript
function process(val: string | null) {
    if (val !== null) {
        val.toUpperCase();  // string
    }
    
    if (val && typeof val === "string") {
        val.toUpperCase();
    }
}
```

## Discriminated Unions

```typescript
interface Square {
    kind: "square";
    size: number;
}

interface Circle {
    kind: "circle";
    radius: number;
}

type Shape = Square | Circle;

function area(shape: Shape): number {
    switch (shape.kind) {
        case "square":
            return shape.size ** 2;
        case "circle":
            return Math.PI * shape.radius ** 2;
    }
}
```
# Namespaces

Organizing code with namespaces. Related: [Modules](07-modules.md), [Errors](09-errors.md).

## Declaration

```typescript
namespace Utils {
    export function formatDate(date: Date): string {
        return date.toLocaleDateString();
    }
    
    export function formatCurrency(amount: number): string {
        return new Intl.NumberFormat("en-US", {
            style: "currency",
            currency: "USD"
        }).format(amount);
    }
}
```

## Usage

```typescript
Utils.formatDate(new Date());
Utils.formatCurrency(100);
```

## Nested Namespaces

```typescript
namespace Utils.Date {
    export namespace Format {
        export function iso(date: Date): string {
            return date.toISOString();
        }
    }
}
Utils.Date.Format.iso(new Date());
```

## Global Merge

```typescript
// shapes.ts
namespace Shapes {
    export class Square { }
}

// shapes2.ts (merged)
namespace Shapes {
    export class Circle { }
}
```

## File-based Namespaces

```typescript
// Validation.ts
/// <reference path="./types.ts" />
```
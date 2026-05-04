# TypeScript Overview

TypeScript is JavaScript with static typing. It compiles to plain JavaScript.

## Basic Syntax

```typescript
// Variable with type
let name: string = "Hello";
let count: number = 42;
let active: boolean = true;

// Function with types
function greet(name: string): string {
    return `Hello, ${name}`;
}
```

## TypeScript Features

- **Static typing**: Type checking at compile time
- **Interfaces**: Define object shapes
- **Generics**: Reusable components
- **Modules**: Code organization
- **IDE support**: IntelliSense, refactoring

## Running TypeScript

```bash
# Install
npm install -g typescript

# Compile
tsc file.ts

# Watch mode
tsc --watch file.ts

# Compile to ES5
tsc --target ES5 file.ts
```

## tsconfig.json

```json
{
    "compilerOptions": {
        "target": "ES2020",
        "module": "commonjs",
        "strict": true,
        "outDir": "./dist"
    }
}
```
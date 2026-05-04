# Error Handling and Definitions

Working with errors and type definitions.

## Error Handling

```typescript
try {
    riskyOperation();
} catch (error) {
    if (error instanceof Error) {
        console.log(error.message);
    }
}
```

## Custom Errors

```typescript
class AppError extends Error {
    constructor(
        message: string,
        public code: string
    ) {
        super(message);
        this.name = "AppError";
    }
}

throw new AppError("Failed", "ERR_001");
```

## Type Definitions

```typescript
// .d.ts files
interface Window {
    myPlugin: MyPlugin;
}

declare const myPlugin: MyPlugin;
```

## Declaration Files

```typescript
// globals.d.ts
declare var MY_VAR: string;
declare function greet(name: string): string;
declare class User { }

declare namespace MyLib {
    function init(): void;
}
```

## Ambient Modules

```typescript
// node.d.ts
declare module "*.json" {
    const value: any;
    export default value;
}
```

## Triple-slash Directives

```typescript
/// <reference types="node" />
/// <reference path="./types.ts" />
```
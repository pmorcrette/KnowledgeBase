# Modules

Importing and exporting code. Related: [Namespaces](08-namespaces), [Overview](00-overview).

## Export

```typescript
// Named export
export const API_URL = "https://api.example.com";
export function greet(name: string): string {
    return `Hello, ${name}`;
}

// Default export
export default class App {
    run() { }
}
```

## Import

```typescript
// Named import
import { greet, API_URL } from "./utils";

// Rename
import { greet as sayHi } from "./utils";

// All as namespace
import * as utils from "./utils";

// Default import
import App from "./App";
```

## Import Types

```typescript
import type { User } from "./types";
import { type User, type Order } from "./types";
```

## Re-exports

```typescript
export { User } from "./user";
export type { Order } from "./order";
export * from "./utils";
```

## CommonJS (Related: [Overview](00-overview))

```typescript
// node.d.ts
module.exports = { foo };
const node = require("./node");
```
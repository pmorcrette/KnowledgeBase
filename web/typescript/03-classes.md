# Classes

Object-oriented programming in TypeScript. Related: [Interfaces](02-interfaces), [Advanced](10-advanced).

## Class Definition

```typescript
class Person {
    name: string;
    age: number;
    
    constructor(name: string, age: number) {
        this.name = name;
        this.age = age;
    }
    
    greet(): string {
        return `Hi, I'm ${this.name}`;
    }
}
```

## Access Modifiers

```typescript
class Person {
    private secret: string;    // Class only
    protected id: number;   // Class + subclasses
    public name: string;    // Anywhere
    
    constructor(name: string, id: number) {
        this.name = name;
        this.id = id;
    }
}
```

## Readonly

```typescript
class Config {
    readonly apiUrl: string;
    
    constructor() {
        this.apiUrl = "https://api.example.com";
    }
}
```

## Getters/Setters

```typescript
class Rectangle {
    private _width: number = 0;
    
    get width(): number {
        return this._width;
    }
    
    set width(value: number) {
        if (value > 0) this._width = value;
    }
}
```

## Inheritance

```typescript
class Animal {
    constructor(public name: string) {}
    move(): void {
        console.log(`${this.name} moves`);
    }
}

class Dog extends Animal {
    bark(): void {
        console.log("Woof!");
    }
}
```

## Abstract Classes

```typescript
abstract class Shape {
    abstract area(): number;
    
    logArea(): void {
        console.log(this.area());
    }
}

class Square extends Shape {
    constructor(public side: number) { super(); }
    
    area(): number {
        return this.side * this.side;
    }
}
```
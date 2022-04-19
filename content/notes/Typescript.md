```typescript
// Implicit Types
let helloWorld = "Hello World";

// Explicit Types
let helloWorld2: string = "Hello World";
let age: number = 20;

// Arrays
let list: number[] = [1, 2, 3];

// Tuple
type stringAndNumber = [string, number];
let x: stringAndNumber = ["hello", 10];

// Enums
enum Continents {
    Asia,
    Europe,
    Africa,
    Australia,
    Antarctica,
    NorthAmerica,
    SouthAmerica,
}
var region = Continents.Africa;

// Interface
interface Person {
    name: string;
    id: number;
}

const user: Person = {
    name: "John",
    id: 1,
}
// Composing types -> Union
type WindowStates = "maximized" | "minimized" | "normal" | string;
const WindowState: WindowStates = "woo";

type LockStates = "locked" | "unlocked" | string;
type OddNumbers = 1 | 3 | 5 | 7 | 9;
var num: OddNumbers = 1;

const getLength = (s: string | string[]) => {
    return s.length;
}
```
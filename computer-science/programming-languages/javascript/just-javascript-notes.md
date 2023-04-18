# Just Javascript notes

Javascript does not pass variables, it passes values.

undefined: unintentionally missing values\
null: intentionally missing values

Javascript implements floating-point math (numbers with limited precision)

Any **whole** numbers between `Number.MIN_SAFE_INTEGER` and `Number.MAX_SAFE_INTEGER` are exact.

Special numbers: `NaN`, `Infinity`, `-Infinity`, and `-0`.

BigInt: n at the end. Eg. 9007199254740991n (precision if needed)

Strings are not objects but have built-in properties. String properties are special and don’t behave the way object properties do. Strings are primitives, and all primitives are immutable.

Symbols serve a similar purpose to door keys: they let you hide away some information inside an object and control which parts of the code can access it.

Objects are _not_ primitive values. They’re mutable (we can change them)

Javascript is a garbage-collected language, we can't destroy an object but it might eventually disappear.

Technically, functions _are_ objects in JavaScript, but are also values.

myFunction() it's a call expression.

`Object.is()` behaves the same as `===`. But **`NaN === NaN` is `false`** and **`-0 === 0` and `0 === -0` are `true`**

To check NaN you can use **`size !== size`**, if this is true then is NaN.

```
console.log([[]] == ''); // true
console.log(true == [1]); // true
console.log(false == [0]); // true
```

```
x == null is strictly equal to x === null || x === undefined
```

Object properties don't contain values, they point to them. Property names are also case-sensitive.

`const` prevents variable reassignment—not object mutation.

`__proto__` prototype

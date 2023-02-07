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

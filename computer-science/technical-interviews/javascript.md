# Javascript

## Variables and primitives

* **What is the output of the following code?**

```javascript
(function(){ 
    var a = b = 3;
})();
console.log(a);
console.log(b);
```

* **What is the difference between let, var and const?**
  * _var_ declarations are globally scoped or function scoped while _let_ and _const_ are block scoped.
  * var variables can be updated and re-declared within its scope; let variables can be updated but not re-declared; const variables can neither be updated nor re-declared.
  *
* **What is the output of the following code?**

```javascript
console.log(NaN === NaN ? 'true' : 'false');
```

* **What is the output of the following code?**

```javascript
console.log([] ? 'true' : 'false');
console.log([] == false ? 'true' : 'false');
```

* **Which ones from the following array are falsy values?**

```javascript
[-1, '', 'false', 0, null, {}, '0', undefined, NaN, false, []]
```

* **What is the output from the following code?**

```javascript
let a = 0.1 + 0.2;
console.log(a === 0.3 ? 'true' : 'false');
```

* **What is the output from the following code?**

```javascript
let a = { x: 10, y: 20 };
let b = a; b.x = 20;
console.log(a.x);
```

* **What ways do we have to clone objects on Javascript?**

```javascript
{...a}
Object.assign({}, a)
```

*   **What does the Promise.all function take as argument and what does it return?**

    _Promise.all_ takes an iterable of promises as input and returns a single Promise. This returned promise fulfills when all of the input's promises fulfill with an array of the fulfillment values. It rejects when any of the input's promises rejects, with this first rejection reason.
*   **Which module would you use to open and read a file in Node.js?**

    _fs_ or the filesystem module.
* **What are the different types of streams in Node.js**
  * **Readable streams:** The readable stream is responsible for reading data from a source file
  * **Writable streams:** The writable stream is responsible for writing data in specific formats to files
  * **Duplex streams:** Duplex streams are streams that implement both readable and writable stream interfaces
  * **Transform streams:** The transform stream is a type of duplex stream that reads data, transforms the data, and then writes the transformed data in a specified format
*   **When to use Node.js streams?**

    Streams come in handy when working with files too large to read into memory and process as a whole.
*   **What does the 'await' keyword do in JS?**

    The _await_ operator is used to wait for a Promise and get its fulfillment value. It can only be used inside an async function or at the top level of a module.
* **What are the differences between Map, WeakMap, and Object data types?**
  * **Objects:** Simple key-value storage with string and symbol keys.
  * **Map:** Versatile key-value storage with any type of key and maintained insertion order. More performant than objects for frequent additions and removals.
  * **WeakMap:** Specialized key-value storage for objects where you don't want the map to prevent garbage collection of its keys. You cannot iterate over WeakMaps
*   **What is Garbage Collection and how does NodeJS apply it?**

    Garbage collection is a form of automatic memory management used by many programming languages. Its primary function is to reclaim memory occupied by objects that are no longer in use.&#x20;

    * Stack: Stores local variables and pointers.
    * Heap: Store reference-type objects, like strings or objects. Has two main segments, New Space (Young generation) and Old Space (Old generation).

    An object is a candidate for garbage collection when it is unreachable from the root node, so not referenced by the root object or any other active objects.\
    V8 Javascript engine employs a stop-the-world garbage collector mechanism. it means that the program stops execution while garbage collection is in progress. That's why it's expensive.\
    V8 engine uses:

    * Scavenge collection: fast, for the Young generation.
    * Mark-sweep collection: slower for the Old generation.

## Event loop

* **What is the difference between null and undefined?**

## Event loop

* **What is the output from the following code?**

```javascript
(function() {
    console.log(1);
    setTimeout(function() { console.log(2) }, 1000);
    Promise.resolve(3).then(i => console.log(i));
    setTimeout(function() { console.log(4) }, 0);
    console.log(5);
    Promise.resolve(6).then(i => console.log(i));
})();
```

* **What are the differences between a promise syntax and the async await syntax?**

```javascript
Promise.then(...)
// vs
const a = await Promise()
```

* **What is going to happen when we run these snippets?**

```javascript
function foo() { setTimeout(foo, 0); }
// and
function foo() { Promise.resolve().then(foo); }

//
foo()
```

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

# Proxy

---

A `Proxy` object can resemble another object but have custom
interceptions by modifying the getters, setters, etc.

---

## Description

Proxies will essentially create a "chain link" from the target object.
Allowing the proxy to use the prototype chain to modify special circumstance
when getting or setting. These are called `traps`.

```js
const target = {
    message1: "hello",
    message2: "everyone",
};

const handler3 = {
    get(target, prop, receiver) {
        if (prop === "message2") {
            return "world";
        }
        return Reflect.get(...arguments);
    },
};

const proxy3 = new Proxy(target, handler3);

console.log(proxy3.message1); // hello
console.log(proxy3.message2); // world
```

Trying to access anything will activate the getter in the handler, but with the 
if statement it will return "world."
Else it will return `Reflect.get(...arguments)`,

---

### Reflect

`Reflect` object is used to get the corresponding object internal methods.
In the case above, we'd want the normal behavior if the prop does not equal "message2."

### Exotic Objects

`Proxy` enables us to create our own exotic objects. 
An example of an exotic object would be an array.
Arrays differ from normal objects, because they have a magic length property that, 
when modified, automatically allocates empty slots or removes elements from the array. 
Similarly, adding array elements automatically changes the length property. 
This is because arrays have a `[[DefineOwnProperty]]` internal method that knows 
to update length when an integer index is written to, or update the array contents 
when length is written to. Such objects whose internal methods have different 
implementations from ordinary objects are called exotic objects.

---
Read more at [MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Proxy)
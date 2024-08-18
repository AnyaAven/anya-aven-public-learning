# Basics of Vue

---

This will be written with from a developer with the understanding of React.

---
### Tutorial

This will follow Vue.js's official [Tutorial](https://vuejs.org/tutorial/#step-1).

---

### Template and Script tags
Use the `<template>` tag for your dynamic HTML. 
To add dynamic logic, add it inside your script.

Setup your component example:
```vue
<script setup>
  import { ref } from 'vue'

  import { reactive } from 'vue'

  const counter = reactive({
    count: 0
  })

  console.log(counter.count) // 0
  counter.count++
  
  const message = ref('Hello World!')

  console.log(message.value) // "Hello World!"
  message.value = 'Changed'
</script>

<template>
  <h1>Make me dynamic! {{counter}} {{message}}</h1>
</template>
```

---

### `reactive()` and `ref()`
Objects created from `reactive()` are JavaScript Proxies that work just like normal objects.
`reactive()` only works on objects (including arrays and built-in types like `Map` and `Set`).
`ref()`, on the other hand, can take any value type and create an object that
exposes the inner value under a `.value` property.

To access refs in a component's template, declare and return them from a component's setup() function:
```vue
import { ref } from 'vue'

export default {
  // `setup` is a special hook dedicated for the Composition API.
  setup() {
    const count = ref(0)

    function increment() {
    // .value is needed in JavaScript
    count.value++
    }

// expose the ref to the template and function
    return { 
      count,
      increment
    }
  }
}
<!---->
<template>
  <h1>{{count}}</h1>
</template>
```

[docs](https://vuejs.org/guide/essentials/reactivity-fundamentals.html)

---
### Differences in `<script setup>` and `setup()`

The tutorial and the docs linked above conflict with the syntax of how 
setup should be defined. One uses a script tag and the other uses ES modules to export.

Will need to research more about the above code example. The one below does work.
```vue
<script setup>
import { ref } from 'vue'

const count = ref(0);

function increment() {
  // .value is necessary in JavaScript
  count.value++
}
</script>

<template>
  <button @click="increment">
    {{ count }}
  </button>
</template>

```



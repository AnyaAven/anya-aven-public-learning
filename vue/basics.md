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

---

### Attribute Bindings
To bind an attribute to a dynamic value we use the `v-bind` directive.

>A directive is a special attribute that starts with the `v-` prefix. 
> They are part of Vue's template syntax

Pass in arguments after the colon to sync with the component's property.
```vue
<script setup>
import { ref } from 'vue'

const titleClass = ref('title')
</script>

<template>
  <h1 v-bind:class="titleClass" >Make me red</h1> <!-- adds dynamic class binding here -->
</template>

<style>
.title {
  color: red;
}
</style>
```
Shorthand (no need to write `v-bind`): 
```vue
<h1 :class="titleClass" >Make me red</h1>
```

---

### Event Listeners
To add event listeners use `@click="callbackFunction`.

Remember to access the variable's value property! `count.value++`

```vue
<script setup>
import { ref } from 'vue'

const count = ref(0)
const increment = function (){
  count.value++
}
console.log(count)
</script>

<template>
  <!-- make this button work -->
  <button @click="increment">Count is: {{ count }}</button>
</template>
```

---

### Form Bindings
Combine both `v-bind` and `v-on` with `v-model`, eliminating the callback function.

Before:
```vue
<script setup>
import { ref } from 'vue'

const text = ref('')

function onInput(e) {
  text.value = e.target.value
}
</script>

<template>
  <input :value="text" @input="onInput" placeholder="Type here">
  <p>{{ text }}</p>
</template>
```

After:
```vue
<script setup>
import { ref } from 'vue'

const text = ref('')

</script>

<template>
  <input v-model="text" placeholder="Type here">
  <p>{{ text }}</p>
</template>
```

v-model works not only on text inputs, but also on other input types such 
as checkboxes, radio buttons, and select dropdowns.

---

### If and Else

Set up a component property (reference) `const awesome = ref(true`
```vue
<h1 v-if="awesome">Vue is awesome!</h1>
<h1 v-else>Oh no 😢</h1>
```
### Lists / For Loops
Similar to React, you need a unique key on each item in a list.
```vue
<ul>
  <li v-for="todo in todos" :key="todo.id">
    {{ todo.text }}
  </li>
</ul>
```

---
### Todo List Example

```vue
<script setup>
import { ref } from 'vue'

// give each todo a unique id
let id = 0

const newTodo = ref('')
const todos = ref([
  { id: id++, text: 'Learn HTML' },
  { id: id++, text: 'Learn JavaScript' },
  { id: id++, text: 'Learn Vue' }
])

function addTodo() {
  todos.value.push({id: id++, text: newTodo.value });
  newTodo.value = ''
}

function removeTodo(todo) {
  const removeId = todo.id;
  todos.value = todos.value.filter(t => t !== todo)
}
</script>

<template>
  <form @submit.prevent="addTodo">
    <input v-model="newTodo" required placeholder="new todo">
    <button>Add Todo</button>
  </form>
  <ul>
    <li v-for="todo in todos" :key="todo.id">
      {{ todo.text }}
      <button @click="removeTodo(todo)">X</button>
    </li>
  </ul>
</template>
```

---
### `Computed()`
Introducing computed(). We can create a computed ref that computes 
its .value based on other reactive data sources:
```js
const filteredTodos = computed(() => {
  return hideCompleted.value
    ? todos.value.filter((t) => !t.done)
    : todos.value
})
```

```vue
<script setup>
import { ref, computed } from 'vue'

let id = 0

const newTodo = ref('')
const hideCompleted = ref(false)
const todos = ref([
  { id: id++, text: 'Learn HTML', done: true },
  { id: id++, text: 'Learn JavaScript', done: true },
  { id: id++, text: 'Learn Vue', done: false }
])

const filteredTodos = computed(() => {
  return hideCompleted.value
    ? todos.value.filter((t) => !t.done)
    : todos.value
})

function addTodo() {
  todos.value.push({ id: id++, text: newTodo.value, done: false })
  newTodo.value = ''
}

function removeTodo(todo) {
  todos.value = todos.value.filter((t) => t !== todo)
}
</script>

<template>
  <form @submit.prevent="addTodo">
    <input v-model="newTodo" required placeholder="new todo">
    <button>Add Todo</button>
  </form>
  <ul>
    <li v-for="todo in filteredTodos" :key="todo.id">
      <input type="checkbox" v-model="todo.done">
      <span :class="{ done: todo.done }">{{ todo.text }}</span> <!-- Notice how to apply classes-->
      <button @click="removeTodo(todo)">X</button>
    </li>
  </ul>
  <button @click="hideCompleted = !hideCompleted">
    {{ hideCompleted ? 'Show all' : 'Hide completed' }}
  </button>
</template>

<style>
.done {
  text-decoration: line-through;
}
</style>
```

Notice how to apply classes `:class="{done: todo.done}"`

Quick toggle, add functionality without a function: `@click="hideCompleted = !hideCompleted"`

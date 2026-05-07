## Houxit.js
#### The Transparent Web Framework for Perfectionists 

Welcome to Houxit, the modern sleek and robust web framework that empowers creative and productive development while Building web apps.

### Overview
**Houxit** (Pronounced: `HOW-zit`), is a next-generation JavaScript framework, partly inspired by the elegance and success of Vue.js, designed to streamline the creation of dynamic, reactive, and component-based web applications with unparalleled ease.

With its intuitive API and clean architecture, Houxit empowers developers to craft interactive and complex UIs with simplicity, making it the framework of choice for modern web development.

### **Why Houxit?**

In a world dominated by familiar giants like React, Vue, Angular, and Svelte, a new idea was born — not to mimic, but to break free. Developers were getting locked into patterns, conventions, and rigid lifecycles that often slowed innovation.

From the ashes of repetition and fatigue, emerged a vision:
A framework that combines clarity, speed, and freedom, without compromising modern standards.

Thus came the Houxit — a symbolic “exit” from old boundaries, led by a new philosophy rooted in simplicity, power, and developer-first design.
**Houxit** isn’t just another framework—it's a revolution, a movement --- an exit from the expected, and an entry into innovation. Combining the best practices of modern web development with innovative features, Houxit redefines how we build web applications, delivering high performance, modularity, and an unmatched developer experience.

<hr>

**Some Key Features and Capabilities at a glance:**

- 🧊 **Component-driven architecture**: Craft reusable, modular components with ease through **Houxit Widgets**.
- 🕋 **Declarative templating**: Write clean and concise templates with Houxit intuitive templating syntax.
- 🛣️ **Two-way data binding**: Keep your data in sync with automatic updates.
- 📶 **Powerful state management system**: Manage your application's state with ease with a lightweight built-in statefull API.
- 🌐 **Extensive ecosystem**: Leverage a growing community of developers and a wealth of plugins and tools.
- 📝 **Gentle learning curve**: Easy to learn, making it perfect for developers of all skill levels, from novices to experts.
- ⚡ **Optimized-performance**: Houxit is optimized for speed and efficiency, ensuring fast and seamless user experiences.
- 🚀 **Flexible and adaptable**: Designed to fit your needs. You can Seamlessly integrate with other libraries , frameworks and existing projects, or use it standalone for new projects..
- 📲 **Virtual DOM**: Optimize performance with a virtual DOM that minimizes DOM mutations and ensures accuracy during DOM reconciliation transform.
- 🎯 **Smart Updates**: Update components only when necessary, reducing unnecessary re-renders.
- 🤽 **Context API**: Share data and functionality between widgets with a simple and efficient API.
- 🧩 **Community-driven**: Join a growing community of developers and contributors.
- 🔖 **Directives**: Extend HTML with custom behaviorial attributes.
- 🪐 **Lifecycle Hooks**: Execute code at precise and specific points in a component's and element's lifecycle.

**Building web applications has never been easier**

 Houxit focuses on maintainability, modularity, and reusability without sacrificing performance. Its strong foundation allows you to build complex web applications that are easy to maintain and extend.


🌐 **Rich Ecosystem**

Houxit offers a rich ecosystem of tools and libraries to support every phase of your application’s lifecycle. From a powerful templating engine to a robust routing system, Houxit provides everything you need to build fast, efficient, and scalable web applications.

🚇 **Convention over Configuration**

Houxit adheres to the principle of **convention over configuration**, letting you focus on what truly matters—building your application—while the framework handles the underlying details and plumbing.


🎗️ **Just the UI**

Houxit is designed to be focused on the view layer, making it easy to integrate with other backend logic or state management libraries, such as Redux or GraphQL, without any fuss.

📲 **Virtual DOM**

Houxit is optimized for performance and scalability, with a virtual DOM that minimizes DOM mutations and smart updates that only update components when necessary. This means your application will be fast and responsive, even with complex and dynamic user interfaces.

⚛️ **JSX**
 
 Enjoy the freedom of JSX support, allowing you to choose the rendering style that best suits your project's needs and your personal coding preferences.

💫 **TypeScript Support**

Out-of-the-box TypeScript support optimizes the development process and enhances debugging, making Houxit the ideal choice for modern, large-scale projects.

✨  **Extensible**

Extensive with the developer's host machine project Capabilities. Meaning that it can be used as a CDN linked to an HTML file as no build steps or CLI installations are required, or can follow the guide to install the Houxit-Kit for the full-fledged experience of what Houxit can offer.

<hr>

##### Here is an example Houxit App

> `./App.houxit`

```html
<script build>
  import { token } from "houxit";
  import AppHeader from "./AppHeader.houxit";
  
  const count = token(0);
  const message = token("Hello Houxit");
  function increment(){
    count.data++
  }
</script>
<template>
  <AppHeader/>
  <h1>{{ message }}</h1>
  <button @click=increment> The count is <strong>{{ count }}</strong> </button>
  
</template>
<style $$scoped>
  button{
    font-size: 2em;
  }
</style>
```

Considering the size, scope or frame of your web frontend target and goals, raging from a full-stack project to standalone widgets, Houxit was built to provides you with most neccessary tools and abilities matching your ambitions and development skills.

Its a Perfectionists web framework that drives innovation.

<hr>

Whether you're starting fresh or integrating into an existing project, Houxit makes it easy to get up and running. For a full-fledged experience, we recommend using the official scaffolding tool, **Houxit-Kit**.


## Introduction

At the heart of Houxit is the concept of a **widget**. A widget is a self-contained, reusable piece of your UI — it manages its own state, reacts to inputs, and renders output. Widgets communicate with each other through clearly defined channels: `$params` (defined inputs), `$signals` (defined emitted events), `$events` (native DOM events), and `$attrs` (passthrough attributes).

Houxit does not rely on a virtual DOM in the traditional sense. Instead, it tracks reactive dependencies granularly, so only the precise parts of the DOM that depend on changed state are updated.

A Houxit application is a tree of widgets, mounted into the real DOM via `initBuild`.

---

## Widgets — The Core Unit

A widget in Houxit can be expressed in three ways:

**1. A plain function** — treated as a `build` function directly and returns a render function.

```javascript
function Greeting({ params }) {
  return ()=>(<h1>Hello, { params.name }</h1>)
}
```

**2. An options object** — a structured object with named options.

```javascript
const Counter = {
  model: {
    count: 0
  },
  handlers: {
    increment() {
      this.count++
    }
  },
  template: `<button $$on:click="increment">Clicked {{ count }} times</button>`
}
```

**3. A class** — extending `Houxit.Widget`.

```javascript
class MyWidget extends Houxit.Widget {
  constructor(){
    super();
    this.model = {
      value: 'hello'
    }
  }
  
  template = `<p>{{ value }}</p>`
}
```

All three forms are valid wherever a widget is expected — as a root widget in `initBuild`, as a child widget, or registered globally.

---

## Getting Started

### CDN Usage

Drop Houxit into any HTML page without a build step:

```html
<!-- Development build -->
<script src="https://cdn.jsdelivr.net/npm/houxit/dist/houxit.global.javascript"></script>

<!-- Production build (minified) -->
<script src="https://cdn.jsdelivr.net/npm/houxit/dist/houxit.global.min.javascript"></script>
```

With the CDN build, Houxit is available as the global `Houxit`:

```html
<script src="https://cdn.jsdelivr.net/npm/houxit/dist/houxit.global.javascript"></script>
<body>
  <div id="app"></div>

<script>
  const { initBuild, useModel } = Houxit

  initBuild({
    model: {
      message: 'Hello from Houxit!'
    },
    template: `<h1>{{ message }}</h1>`
  }).mount('#app')
</script>
</body>
```

You can also use the ES module build with `unplugin` or directly via import maps:

```html
<script type="importmap">
  {
    "imports": {
      "houxit": "https://cdn.jsdelivr.net/npm/houxit/dist/houxit.esm.javascript"
    }
  }
</script>

<script type="module">
  import { initBuild } from 'houxit'

  initBuild({ template: `<p>Hello!</p>` }).render('#app')
</script>
```

---

### Installation via npm

```bash
npm install houxit
```

Import the framework in your entry file:

```javascript
import { initBuild } from 'houxit'
```

---

### Scaffolding a Project

For full-featured projects with `.houxit` Widget Unit Files, use the official scaffolding tool:

```bash
npm create houxit@latest
```

Follow the prompts to name your project and choose a preset (minimal, standard, or full). The scaffolded project includes a configured build pipeline, a sample app structure, and development tooling.

```
my-app/
├── src/
│   ├── widgets/
│   │   └── App.houxit
│   └── main.javascript
├── index.html
└── package.json
```

Then start the dev server:

```bash
cd my-app
npm install
npm run dev
```

---

## Your First App — `initBuild`

`initBuild` is the entry point for a Houxit application. It accepts a root widget (function, options object, or class) and returns an application instance with a `render` method and many more.

```javascript
import { initBuild } from 'houxit'

const app = initBuild({
  model: {
    count: 0
  },
  handlers: {
    increment() {
      this.count++
    }
  },
  template: `
    <div>
      <p>Count: {{ count }}</p>
      <button $$on:click="increment">+</button>
    </div>
  `
})

app.mount('#app')
```

`initBuild` differs from a regular widget instantiation in one key way: when Houxit encounters the root widget via `initBuild`, it treats that widget as the **application root** (`initBuild` context). In this context, if no explicit `render` function, `template`, or `markdown` option is present, Houxit will use the `innerHTML` of the mount target as the template. This allows progressive enhancement of server-rendered HTML.

**Resolution order for the root widget's output:**

1. `render` function (explicit hyperscript)
2. `template` option (string template)
3. `markdown` option (markdown string)
4. `innerHTML` of the mount element (only in `initBuild` context)

---

## Widget Unit Files (WUF)

A **Widget Unit File** (`.houxit`) is the single-file format for authoring widgets when working within a build-tool project. It encapsulates the widget's script, template, and styles in one file — keeping related concerns co-located without coupling them.

```html
<!-- src/widgets/Counter.houxit -->

<script build>
import { stream } from 'houxit'

const count = stream(0)

function increment() {
  count.value++
}
</script>

<template>
  <div class="counter">
    <p>Count: {{ count }}</p>
    <button $$on:click="increment">Increment</button>
  </div>
</template>

<style>
.counter {
  font-family: sans-serif;
  padding: 1rem;
}
</style>
```

The `<script build>` block is the Adapter API authoring mode — it runs in a build context where reactive primitives, lifecycle hooks, and widget metadata are implicitly scoped to the widget being defined. Variables declared at the top level of `<script build>` are automatically available in the template.

You can also use the Options API with a `<script>` block:

```html
<script>
export default {
  model: {
    count: 0
  },
  handlers: {
    increment() {
      this.count++
    }
  }
}
</script>

<template>
  <button $$on:click="increment">{{ count }}</button>
</template>
```

---

## Options API

The Options API lets you define a widget as a plain object with named options. Each option plays a specific role in the widget's lifecycle and behavior.

### model

`model` is where you declare the widget's **reactive state**. Unlike a function that returns state, you define properties directly on the `model` object. Houxit reads this object at instantiation time, makes every property reactive, and merges it into the widget instance.

```javascript
export default {
  model(){
    this.count= 0;
    this.user= { name: 'Chukwuemeka', role: 'admin' };
    this.items= [];
  }
}
```

In the template and in handlers, state properties are accessed directly by name — `count`, `user.name`, etc. In handlers, use `this.count` to mutate state.

### params

`params` declares the widget's accepted inputs. Params are passed by the parent and are read-only within the widget. They are available in templates as `$params.propName`.

```javascript
export default {
  params: {
    title: String,
    count: {
      type: Number,
      default: 0
    },
    onSave: Function
  }
}
```

### handlers

`handlers` replaces what other frameworks call "methods". These are functions that operate on the widget's state and are callable from the template.

```javascript
export default {
  handlers: {
    increment() {
      this.count++
    },
    async fetchData() {
      this.items = await api.getItems()
    }
  }
}
```

### observers

`observers` replaces watchers. Define observers as an object whose keys are reactive state paths (or functions returning a value) and whose values are callback functions called when the observed value changes.

```javascript
export default {
  observers: {
    count(newVal, oldVal) {
      console.log(`count changed from ${oldVal} to ${newVal}`)
    },
    'user.name'(newName) {
      document.title = newName
    }
  }
}
```

### Lifecycle Hooks

Houxit provides a set of lifecycle hooks that map to key moments in a widget's life. All hooks are defined as functions in the options object.

| Hook | When it runs |
|---|---|
| `preBuild` | Before the widget is built/initialized |
| `postBuild` | After the widget is built |
| `init` | When the widget instance is first created |
| `preMount` | Just before the widget is inserted into the DOM |
| `postMount` | After the widget is mounted in the DOM |
| `preUpdate` | Before a reactive update causes a re-render |
| `postUpdate` | After a reactive update has re-rendered |

```javascript
export default {
  model(){ 
    this.count= 0 
  },
  postMount() {
    console.log('Widget is in the DOM')
  },
  postUpdate() {
    console.log('DOM updated')
  }
}
```

### template

A string template for the widget's HTML output. Supports all Houxit template syntax including directives, blocks, and interpolation/filters.

```javascript
export default {
  template: `
    <div>
      <h1>{{ title }}</h1>
      <p $$if="show">Visible</p>
    </div>
  `
}
```

### render

An explicit render function using Houxit's `h` hyperscript helper. When `render` is present, `template` and `markdown` are ignored.

```javascript
import { h } from 'houxit'

export default {
  render() {
    return h('div', null,
      h('h1', null, this.title),
      h('p', null, `Count: ${this.count}`)
    )
  }
}
```

---

## Adapter API

The Adapter API is the composition-oriented authoring style, used within `<script build>` blocks in WUF files or called inside the `build` function option of the Options API. It mirrors and extends the Options API's capabilities with function-based primitives that can be freely composed across modules.

> **Note:** Adapter API functions must be called during widget initialization (synchronously, at the top level of `<script build>` or inside `build`). They rely on the active widget instance context to register themselves correctly.

### token — Reactive State

`token` creates a reactive value. Reading `.data` tracks the dependency; writing `.value` triggers updates.

```javascript
import { token } from 'houxit'

const count = token(0)

count.data        // read: 0
count.data = 5    // write: triggers updates
```

In templates within `<script build>`, access the token by its variable name directly — Houxit unwraps `.data` automatically: however, some caveats apply. Check docs.

```html
<p>{{ count }}</p>
```

To create a stream of objects or arrays:

```javascript
const user = stream({ name: 'Chukwuemeka' })
const items = stream([])
```

### token — Reactive Refs

`token` creates a ref to a DOM element or widget instance.

```javascript
import { token } from 'houxit'

const inputEl = token(null)
```

```html
<input $$bind:ref="inputEl" />
```

After mount, `inputEl.data` points to the actual DOM element.

### createAgent — Signals

`createAgent` creates a reactive signal — a getter/setter pair ideal for sharing state across widgets without a full reactive object.

```javascript
import { createAgent } from 'houxit'

const [getCount, setCount] = createAgent(0)

getCount()       // read
setCount(5)      // write
setCount(( value }) => n + 1)  // update from previous value
```

Signals work well with `Provider`  for cross-widget state sharing without prop-drilling.

### observe — Watching State

`observe` watches a reactive source and calls a callback when it changes.

```javascript
import { token, observe } from 'houxit'

const count = token(0)

observe(count, (newVal, oldVal) => {
  console.log(`changed: ${oldVal} → ${newVal}`)
})

// Watch a computed expression:
observe(() => count.data * 2, (doubled) => {
  console.log('doubled:', doubled)
})
```

Options:

```javascript
observe(source, callback, {
  initial: true,   // run immediately with current value
  deep: true         // deeply observe objects/arrays
})
```

### effectHook — Side Effects

`effectHook` runs a callback immediately and re-runs it whenever any reactive state it reads changes. It's the right tool for effects that should auto-track their dependencies.

```javascript
import { token, effectHook } from 'houxit'

const count = token(0)

effectHook(() => {
  document.title = `Count is ${count.data}`
  // Houxit tracks that this effect reads count.value
  // and re-runs whenever count changes
})
```

Return a cleanup function to run before the next effect execution or when the widget unmounts:

```javascript
effectHook(() => {
  const timer = setInterval(() => count.value++, 1000)
  return () => clearInterval(timer)
})
```

### Readonly & Shallow Variants

```javascript
import { stream, readonly, shallow, readonlyStream, shallowStream } from 'houxit'

// Prevent mutation of a stream from outside a widget:
const count = token(0)
const readCount = readonly(count)

// Shallow streams only react to top-level property changes:
const state = shallowStream({ nested: { value: 1 } })

// Readonly shallow:
const locked = readonlyStream(state)
```

### Lifecycle Hooks in Adapter API

All Options API lifecycle hooks have Adapter API equivalents as importable functions:

```javascript
import {
  preBuild,
  postBuild,
  init,
  preMount,
  postMount,
  preUpdate,
  postUpdate
} from 'houxit'

postMount(() => {
  console.log('mounted!')
})

postUpdate(() => {
  console.log('updated')
})
```

---

## Templates

Houxit templates are valid HTML supersets. They are compiled to efficient render code at build time (or at runtime for CDN usage). Any valid HTML is valid in a Houxit template.

### Interpolation

Use double curly braces to interpolate reactive expressions:

```html
<p>Hello, {{ name }}!</p>
<p>2 + 2 = {{ 2 + 2 }}</p>
<p>{{ isLoggedIn ? 'Welcome back' : 'Please sign in' }}</p>
```

Interpolations are text-only by default (HTML is escaped for security). Use the `$$html` directive or the `@html` block to render raw HTML.

---

### Directives

Directives are special attributes prefixed with `$$`. They give Houxit instructions on how to treat a DOM element reactively.

#### `$$if` / `$$else` / `$$else-if`

Conditionally render an element. The element and its children are fully created or destroyed based on the condition's truthiness.

```html
<p $$if="isLoggedIn">Welcome back!</p>
<p $$else-if="isPending">Loading...</p>
<p $$else>Please log in.</p>
```

#### `$$for`

Render a list of elements from an array. Use the `of` syntax with a key for efficient reconciliation:

```html
<ul>
  <li $$for="item of items" :key="item.id">
    {{ item.name }}
  </li>
</ul>
```

With index:

```html
<li $$for="(item, index) of items" :key="index">{{ index }}: {{ item }}</li>
```

#### `$$bind`

`$$bind:attr="expression"` binds a DOM attribute or property to a reactive expression. Use the `*` shortcut syntax:

```html
<!-- Full syntax -->
<img $$bind:src="user.avatarUrl" $$bind:alt="user.name" />

<!-- Shortcut (* prefix) -->
<img *src="user.avatarUrl" *alt="user.name" />

<!-- Boolean attributes -->
<button *disabled="isLoading">Submit</button>

<!-- Two-way binding for inputs -->
<input $$model="message" />
```

#### `$$on`

`$$on:event="handler"` attaches an event listener. Use the `@` shortcut:

```html
<!-- Full syntax -->
<button $$on:click="increment">+</button>

<!-- Shortcut (@ prefix) -->
<button @click="increment">+</button>

<!-- Inline expression -->
<button @click="count++">+</button>

<!-- Event modifiers -->
<form @submit|prevent="handleSubmit">...</form>
<!--Multi event attachment -->
<div @click.hover|stop="select">...</div>
```

#### `$$slot`

`$$slot` declares a slot outlet inside a widget's template. Use the `#` shortcut for slot usage on the parent side:

```html
<!-- Inside a Card widget's template -->
<div class="card">
  <div class="card__header">
    <slot name="header" />
  </div>
  <div class="card__body">
    <slot /> <!-- default slot -->
  </div>
</div>

<!-- Using the Card widget -->
<Card>
  <h3 $$slot:default/>
  <!--shortcut (# prefix)-->
  <h2 #header>My Title</h2>
  <p>Card body content.</p>
</Card>
```

Scoped slots pass data from child to parent:

```html
<!-- Widget template exposes data to the slot through the context prop -->
<slot name=default context="{ item }" />

<!-- Parent consumes it -->
<MyList #default="{ item }">
  <span>{{ item.name }}</span>
</MyList>
```

#### `$$animate` & `$$transite`

`$$animate` and `$$transite` handle enter/leave animations and CSS transitions declaratively.

`$$transite` applies CSS transitions when an element enters or leaves the DOM (often paired with `$$if` or `$$for`):

```html
<p $$if="show" $$transite:fade="{ delay:300 }">Hello</p>
```

```javascript
// Define the transition in your widget or globally
export default {
  transitions: {
    fade(node, params){
      
      return {
        enter: { opacity: [0, 1], duration: 300 },
        leave: { opacity: [1, 0], duration: 200 }
      }
    }
  }
}
```

`$$animate` applies keyframe-style animations with full control:

```html
<div $$animate:spin >Loading...</div>
```

```javascript
export default {
  animations: {
    spin(node, { to, from }, params){
      
      return {
        keyframes: [
          { transform: 'rotate(0deg)' },
          { transform: 'rotate(360deg)' }
        ],
        duration: 1000,
        iterations: Infinity
      }
    }
  }
}
```

Custom animation functions give you complete programmatic control:

```javascript
export default {
  animations: {
    bounce(el, { to, from }, params) {
        // Animate el however you like, call done() when finished
      return { duration: 400, easing: 'ease-out' }
    }
  }
}
```
when declared in Adapter mode or in mode context:you will have to call the js compiler in template.
```html
<div $$animate:[spin] >Loading...</div>
```

In render functions or jsx, use the `motion` prop and call the `transite` & `animate` methods. They receive the animations and transition functiins as first argument then parameters.

```javascript
<div motion={animate(whixx, {})}/>//jsx
h('input', { motion:transite(fade, {})})//render functions
//Or you can use the attach prop...
<div attach={({ animate, transite, use })=>{//transite and animate exposed in the context object
        transite(fly, {});
        animate(whosh);
}} />
```
to resolve a registered animation or transition function up the ancestor scope, use the `Houxit.resolve()` callback;
```html
<script build>
import { resolve } from 'houxit';

const fade=resolve.animation('fade');
function whizzz(node, params){
  //a Custom transition function, does not require registration
}
</script>
<template>
  <div $$animate:[fade] >Loading...</div>
  <div $$transite:[whizzz]='{ duration:400 }' >Loading...</div>
</template>
```
---

### Template Blocks

Blocks are multi-line template constructs that provide control flow and utility beyond what single-attribute directives can express. Blocks use a `{{@keyword}}` / `{{/keyword}}` delimiter syntax.

#### `@if` Block

```html
{{@if count > 10}}
  <p>Count is large!</p>
{{@else:if count > 5}}
  <p>Count is medium.</p>
{{@else}}
  <p>Count is small.</p>
{{/if}}
```

#### `@for` Block

```html
{{@for item of items}}
  <div class="item">
    <h3>{{ item.title }}</h3>
    <p>{{ item.body }}</p>
  </div>
{{/for}}
```

With index and key:

```html
{{@for (item, i) of items key=item.id}}
  <li>{{ i + 1 }}. {{ item.name }}</li>
{{/for}}
```

#### `@const`

Declare a local template variable for use within the template scope:

```html
{{@const total = items.reduce((s, i) => s + i.price, 0)}}
<p>Total: {{ total }}</p>

{{@const greeting = `Hello, ${user.name}!`}}
<h1>{{ greeting }}</h1>
```

`@const` declarations are scoped to the nearest enclosing block (or the template root).

#### `@html`

Render a raw HTML string. Only use with trusted content — this bypasses Houxit's automatic HTML escaping.

```html
{{@html article.bodyHtml}}
```

#### `@await` Block

Render async content inline. Best used inside a `Suspense` widget for graceful loading states.

```html
{{@await fetchUser(userId)}}
```

The `Suspense` widget handles the pending state globally for a subtree:

```html
<Suspense>
  <p #fallback>Loading...</p>

  {{@await fetchData()}}
</Suspense>
```

#### `@class` / `@new`

`@class` opens a class-based scoping block. `@new` instantiates within that block. These are advanced blocks for scenarios where class-based constructs serve the rendering logic.

```html
{{@class Formatter}}
  {{@const fmt = @new Formatter(locale)}}
  <p>{{ fmt.format(value) }}</p>
{{/class}}
```

---

## Class & Style Bindings

Houxit extends standard class and style binding with an expressive dot-notation shorthand.

### Class Binding

**Standard object syntax:**

```html
<div $$bind:class="{ active: isActive, disabled: isDisabled }"></div>
```

**Array syntax:**

```html
<div $$bind:class="[baseClass, isActive ? 'active' : '']"></div>
```

**Dot-notation shorthand** — map class names directly onto the element using a condition:

```html
<div class.name.header></div>
```

Binding it (with `*`) makes the right-hand side evaluated as a JS expression:

```html
<!-- Applies both 'name' and 'header' classes when isHeader is truthy -->
<div *class.name.header="isHeader"></div>
```

### Style Binding

**Standard object syntax:**

```html
<p $$bind:style="{ color: textColor, fontSize: size + 'px' }"></p>
```

**Dot-notation shorthand** — set a CSS property directly:

```html
<!-- Sets color to the literal string 'red' -->
<p style.color="red"></p>

<!-- Binding: the value is parsed as a JS expression -->
<p *style.color="primaryColor"></p>

<!-- Multiple properties -->
<p style.color.background="red"></p>
```

Combined:

```html
<p *style.color.background="isDark ? 'white' : 'black'"></p>
```

---

## Reactivity In-Depth

Houxit's reactivity system is based on automatic dependency tracking. When a reactive value (a `token`, a `stream`, a `createAgent` getter, or a `model` property) is read during rendering or inside an `effectHook`, Houxit records that dependency. When the value changes, Houxit knows exactly which parts of the DOM or which effects to re-run.

**Reactive objects** — streams containing objects are deeply reactive by default. Accessing a nested property inside a template or effect establishes a dependency on that specific property.

```javascript
const user = stream({ name: 'Chukwuemeka', age: 30 })

effectHook(() => {
  // This effect only re-runs when user.value.name changes
  // Not when user.value.age changes
  console.log(user.value.name)
})
```

**Computed values** — derive reactive values from other reactive values using `computed`:

```javascript
import { token, computed } from 'houxit'

const count = token(2)
const doubled = computed(() => count.data * 2)

// doubled.data === 4
// Updates automatically when count changes
```

Computed values are lazy (only evaluated when read) and cached (the function only re-runs when a dependency changes).

**Arrays** — mutations like `.push()`, `.pop()`, `.splice()` on a reactive stream's value are tracked automatically:

```javascript
const list = stream([1, 2, 3])
list.value.push(4)  // reactive update triggered
```

---

## Props, Events & Attrs

### `$params`

`$params` is the in-template and in-model accessor for declared params (defined in the `params` option or declared with `defineParams` in `<script build>`).

```html
<p>Hello, {{ $params.name }}!</p>
```

In the `build` function or Adapter API context, `params` is available as part of the first argument object:

```javascript
build({ params, signals, events, attrs }) {
  // ...
}
```
In `<script build>`, you can get params from the return value of `defineParams`

### `$events` & `$signals`

**`$signals`** are **declared** events — events the widget explicitly defines as part of its public API (equivalent to declared emits). Signal usage is intentional and documented.

```javascript
// Options API
{
  signals: ['update:count', 'save'],
  handlers: {
    save() {
      this.$signals.save(this.formData)//pass arguments
    }
  }
}
```

**`$events`** are **undeclared** events — native DOM events that fall through to the widget's root element without explicit declaration. They behave like native event listeners attached from outside.

### `$attrs`

`$attrs` contains all attributes passed to a widget that are not declared as `params` or `signals`. This includes class, style, and event listeners that weren't explicitly declared.

```html
<!-- Parent -->
<MyInput class="large" placeholder="Type here..." />

<!-- MyInput template — $attrs contains class and placeholder -->
<input $$bind="$attrs" />
```

### Fallthrough Props & Slots

By default, attributes in `$attrs` fall through to the widget's root element. To disable this:

```javascript
{
  buildConfig:{
    forwardAttrs: false
  }
}
// Adapter API use the Houxit.defineConfig() adapter instead.
```

Then manually apply `$attrs` wherever appropriate using `$$bind="$attrs"`.

Slots fall through automatically when a widget passes `<slot>` content to a child widget.
To disable set the `forwardSlot` config to false;

---

## Slots

Slots let parent widgets inject content into a child widget's template.

**Default slot:**

```html
<!-- Button widget template -->
<button class="btn">
  <slot />
</button>

<!-- Usage -->
<Button>Click me</Button>
```

**Named slots:**

```html
<!-- Modal widget template -->
<div class="modal">
  <header><slot name="header" /></header>
  <main><slot /></main>
  <footer><slot name="footer" /></footer>
</div>

<!-- Usage -->
<Modal>
  <h2 #header>Confirm</h2>
  <p>Are you sure?</p>
  <button #footer @click="confirm">Yes</button>
</Modal>
```

**Scoped slots** pass data up from child to parent: but to expose data to the who consumer scope, use the context option method. it return value is exposed to the consumer. `useContext` for Adapter API;

```javascript
{
  context(){
    return {
      item:{
        label:'houxit'
      },
      index:0
    }
  }
}
```
```html
<!-- List widget exposes item to the children using the $$provide directive -->
<List $$provide="{ item, index }">
  <strong>{{ index }}: {{ item.label }}</strong>
</List>
```

---

## Built-in Widgets

Houxit ships a set of built-in widgets that handle common structural patterns.

### Build

`Build` is the dynamic widget component. Its `self` prop accepts any valid widget — a widget definition object, a function, a class, or a string name of a registered widget or a valid tagname.

```html
<!-- Equivalent to Vue's <component :is="..."> -->
<Build *self="currentWidget" *name="userName" />
```

The `self` prop serves as the `is` selector — whatever you pass, Houxit renders it as a widget.

### Suspense

`Suspense` wraps async subtrees and displays a fallback while they resolve.

```html
<Suspense>
  <Spinner #fallback />
  <AsyncDashboard />
</Suspense>
```

`Suspense` integrates with `@await` blocks and with any widget that has an async `build` function.

### Portal

`Portal` renders its children into a different DOM node — useful for modals, tooltips, and overlays that need to escape their parent's stacking context.

```html
<Portal target="#modals">
  <div class="modal-overlay">
    <p>I'm rendered in #modals, not in-place.</p>
  </div>
</Portal>
```

### Memo

`Memo` is the widget equivalent of a memoized component. It prevents re-renders of its children unless the specified dependencies change. Analogous to a keep-alive cache for static or expensive subtrees.

```html
<Memo *key="userId">
  <ExpensiveProfile *id="userId" />
</Memo>
```

### Provider

`Provider` establishes a reactive value in the widget tree that descendant widgets can inject without prop-drilling. Works well with `createAgent`.

```html
<!-- Provide a value -->
<Provider name="theme" *value="currentTheme">
  <App />
</Provider>
```

```javascript
// Inject in a descendant
import { inject } from 'houxit'
const theme = inject('theme')
```

### Self

`Self` renders the current widget recursively. Use it to build tree views, nested menus, or any fractal structure.

```html
<!-- TreeNode widget -->
<div class="node">
  <span>{{ node.label }}</span>
  <div $$if="node.children.length" class="children">
    <Self $$for="child of node.children" *node="child" />
  </div>
</div>
```

### Motion

`Motion` wraps one or more elements and applies enter/leave transitions and animations. It's the declarative animation wrapper — an alternative to placing `$$transite` and `$$animate` on individual elements when you want to manage a group's transitions in one place.

```html
<Motion name="slide" mode="out-in">
  <div $$if="view === 'home'" key="home">
    <Home />
  </div>
  <div $$if="view === 'about'" key="about">
    <About />
  </div>
</Motion>
```

Define the transition in your widget options or globally:

```javascript
{
  transitions: {
    slide: {
      enter: { transform: ['translateX(100%)', 'translateX(0)'], duration: 300 },
      leave: { transform: ['translateX(0)', 'translateX(-100%)'], duration: 300 }
    }
  }
}
```

### Fragment

`Fragment` renders multiple root elements without a wrapping DOM node — useful when a widget needs to return more than one sibling element.

```html
<Fragment>
  <dt>Term</dt>
  <dd>Definition</dd>
</Fragment>
```

---

## Render Functions & Hyperscript

When templates aren't flexible enough — or when you want to construct UI programmatically — use Houxit's `h` function to write render functions.

```javascript
import { h } from 'houxit'
```

`h` signature:

```javascript
h(type, props, ...children)
```

- **`type`**: A string tag name (`'div'`, `'p'`), a widget definition, or a built-in widget.
- **`props`**: An object of attributes, event handlers, and directives. `null` if none.
- **`children`**: Child nodes — strings, numbers, or more `h()` calls.

```javascript
{
  render() {
    return h('ul', { class: 'list' },
      ...this.items.map(item =>
        h('li', { key: item.id }, item.name)
      )
    )
  }
}
```

Render functions have the same expressive power as templates — all reactive state reads are tracked, all events can be attached, all built-in widgets can be used.

**Using built-in widgets in render functions:**

```javascript
import { h, Suspense, Fragment } from 'houxit'

render() {
  return h(Fragment, null,
    h('h1', null, 'Title'),
    h(Suspense, { fallback: h('p', null, 'Loading...') },
      h(AsyncWidget, { id: this.id })
    )
  )
}
```

---

## The `<script render>` Tag

Inside a `.houxit` Widget Unit File, you can use a dedicated `<script render>` block instead of a `<template>` or `render` option. This block exports a render function that receives the widget context.

```html
<!-- UserCard.houxit -->

<script>
export default {
  params: {
    user: Object
  }
}
</script>

<script render>
import { h } from 'houxit'

export default function render({ $params }) {
  return h('div', { class: 'card' },
    h('img', { src: $params.user.avatar }),
    h('h2', null, $params.user.name),
    h('p', null, $params.user.bio)
  )
}
</script>
```

The `<script render>` tag takes precedence over `<template>` if both are present. It is the recommended approach when your widget's output is highly dynamic or computed.

---

## Composing with the `build` Method

The `build` option in the Options API is Houxit's bridge between the structured Options API and the composition-oriented Adapter API. When you define a `build` function, it runs in the Adapter API context — you can call `stream`, `observe`, `effectHook`, lifecycle hooks, and all other Adapter API functions inside it.

`build` receives the widget's context object as its first argument and **must return a render function**.

```javascript
import { stream, effectHook, postMount, h } from 'houxit'

export default {
  params: {
    initialCount: Number
  },

  build({ $params }) {
    const count = stream($params.initialCount ?? 0)

    postMount(() => {
      console.log('Counter mounted with', count.value)
    })

    effectHook(() => {
      document.title = `Count: ${count.value}`
    })

    function increment() {
      count.value++
    }

    // build MUST return a render function
    return () => h('div', null,
      h('p', null, `Count: ${count.value}`),
      h('button', { 'on:click': increment }, '+')
    )
  }
}
```

> **Important:** `this` is `undefined` inside `build`. All state is local to the function closure. This is by design — it encourages clean, explicit data flow.

A **function widget** is treated as a `build` function directly:

```javascript
function Counter({ $params }) {
  const count = stream($params.initial ?? 0)

  return () => h('div', null,
    h('p', null, `${count.value}`),
    h('button', { 'on:click': () => count.value++ }, '+')
  )
}
```

When Houxit detects a function used as a widget, it calls it once (during initialization) and uses the returned render function for all subsequent renders.

---

## TypeScript Support

Houxit ships with full TypeScript types. Params, signals, model properties, and build function arguments are all typed.

```javascript
import { defineWidget, token } from 'houxit'

interface User {
  name: string
  email: string
}

export default defineWidget({
  params: {
    user: Object as () => User
  },

  build({ params }: { params: { user: User } }) {
    const editedName = token(params.user.data.name)

    return () => h('input', {
      value: editedName.data,
      'on:input': (e: Event) => {
        editedName.data = (e.target as HTMLInputElement).value
      }
    })
  }
})
```

In `<script build>` blocks within `.houxit` files, use `defineParams` and `defineSignals` for typed declarations:

```html
<script build lang="ts">
import { stream, defineParams, defineSignals } from 'houxit'

const $params = defineParams<{
  label: string
  disabled?: boolean
}>()

const emit = defineSignals<{
  click: [MouseEvent]
}>()

function handleClick(e: MouseEvent) {
  if (!$params.disabled) emit('click', e)
}
</script>

<template>
  <button *disabled="$params.disabled" @click="handleClick">
    {{ $params.label }}
  </button>
</template>
```

---

## License

Houxit.javascript is released under the [MIT License](LICENSE).

---

<p align="center">
  Built with intention. Designed for humans.
</p>

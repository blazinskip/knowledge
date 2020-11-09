# vue.js

**Q1. What is Vue.js? What are the advantages of it?**

Vue is a **progressive framework** used to building user interfaces.The core library is focused on the view layer only, and is easy to pick up and integrate with other libraries or existing projects.

Following are the advantages of using Vue.js.

* Small in size — The size of this framework is 18 to 21KB and it takes no time for the user to download and use it.
* Easy to Understand — One of the reasons for the popularity of this framework is that it is quite easy to understand. The user can easily add Vue.js to his web project because of its simple structure.
* Simple Integration — Vue.js can be integrated with the existing applications easily.
* Flexibility — This flexibility also makes it easy to understand for the developers of React.js, Angular.js, and any other new JavaScript framework.
* Virtual DOM — It uses virtual DOM similar to other existing frameworks such as ReactJS, Ember etc. Virtual DOM is a light-weight in-memory tree representation of the original HTML DOM and updated without affecting the original DOM.
* Components — Used to create reusable custom elements in VueJS applications.
* Two-Way Communication — Vue.js also facilitates two way communications because of its MVVM architecture which makes it quite easy to handle HTML blocks.

Q5. What is the virtual DOM and how is it beneficial?Hide answer

The virtual DOM is a tree-like data structure \(or a collection\) of JavaScript objects representing DOM nodes that are managed by Vue.js and that should be rendered on the page. These objects are called “virtual nodes” or `VNode`s for short.

The main purpose of the virtual DOM is faster and more efficient DOM manipulation. When there are lots of nodes in the DOM, updating them can be expensive in terms of processing power and resources required.

Working with the virtual DOM JavaScript object is significantly faster. Subsequently, Vue.js organizes DOM updates in batches for more efficiency.

**Q2. What are all the life cycle hooks in Vue instance?**

Each Vue instance goes through series of steps when they are created, mounted and destroyed. Along the way, it will also runs functions called life cycle hooks, giving us the opportunity to add our own code at specific stage. Below are the events, a Vue instance goes through.

* **beforeCreate** — The first hook in the creation hooks. They allow us to perform actions before our component has even been added to the DOM. We do not have access to the DOM inside of this.
* **created** — This hook can be used to run code after an instance is created. We can access the reactive `data`. But templates and Virtual DOM have not yet been mounted or rendered.
* **beforeMount** — The beforeMount hook runs right before the initial render happens and after the template or render functions have been compiled. Most likely we’ll never need to use this hook.
* **mounted** — We will have full access to the reactive component, templates, and rendered DOM. This is the most frequently used hook.
* **beforeUpdate** — This hook runs after data changes on our component and the update cycle begins. But runs right before the DOM is patched and re-rendered.
* **updated** — This hook runs after data changes on our component and the DOM re-renders. If we need to access the DOM after a property change, here is probably the safest place to do it.
* **beforeDestroy** — This hook will run right before tearing down the instance. If we need to clean up events or reactive subscriptions, this is the right place to do it.
* **destroyed** — This hook will be used to do any last minute clean up.

**Q3. What is the difference between `v-show` and `v-if` directives?**

Below are some of the main differences between between `v-show` and `v-if`directives:

* `v-if` only renders the element to the DOM if the expression passes whereas `v-show` renders all elements to the DOM and then uses the CSS display property to show/hide elements based on expression.
* `v-if` supports `v-else` and `v-else-if` directives whereas `v-show` doesn't support else directives.
* `v-if` has higher toggle costs since it add or remove the DOM every time while `v-show` has higher initial render costs. i.e, `v-show` has a performance advantage if the elements are switched on and off frequently, while the `v-if` has the advantage when it comes to initial render time.
* `v-if` supports tab but `v-show` doesn't support.

**Q4. What is `key` in Vue.js?**

In order to render DOM elements more efficiently, Vue.js reuses the elements instead of creating them from scratch every time. This default mode is efficient, but in some cases it may causes problems. For example, if you try to render the same input element in both `v-if` and `v-else` blocks then it holds the previous value as below:

**Q5. Why should not use if and for directives together on the same element?**

It is recommended not to use `v-if` on the same element as `v-for`. Because `v-for` directive has a higher priority than `v-if`. There are two common cases where this can be tempting:

* To filter items in a list \(e.g. `v-for="user in users" v-if="user.isActive"`\). In these cases, replace `users` with a new computed property that returns your filtered list \(e.g. `activeUsers`\).
* To avoid rendering a list if it should be hidden \(e.g. `v-for="user in users" v-if="shouldShowUsers"`\). In these cases, move the `v-if` to a container element \(e.g. `ul`, `ol`\).

**Q6. What is the difference between comptuted properties and methods?**

Computed properties are getter function in Vue instance rather than actual methods. we can define the same function as a method instead. However, the difference is that computed properties are cached based on their dependencies. A computed property will only re-evaluate when some of its dependencies have changed. In comparison, a method invocation will always run the function whenever a re-render happens.

When we have to compute something by doing lot of computations like looping through a large array, it is best to use computed properties instead of a method. Without caching, we would spend more time than necessary. When we do not want cache, we can use a method instead.

**Q7. What is `$parent` in Vue?**

Similar to `$root`, the `$parent` property can be used to access the parent instance from a child.

Although it provides direct access, it makes the application hard to test and debug. And we can not easily find out the where the mutation come from.

Vue also provides `$child` just like `$parent`, but it can be used to access the child instance.

**Q8. What is the role of `ref` in Vue.js?**

Despite the existence of props and events, sometimes if we still need to directly access a child component, we can assign a reference ID to the child component using the ref attribute. For example:![](https://miro.medium.com/max/60/1*Vv1PFMqH1MOhUBkxbKGn1Q.png?q=20)![](https://miro.medium.com/max/455/1*Vv1PFMqH1MOhUBkxbKGn1Q.png)

Now in the component where we have defined this `ref`, we can use:![](https://miro.medium.com/max/60/1*N2CwmbcWPRMeslXpSDUFfw.png?q=20)![](https://miro.medium.com/max/273/1*N2CwmbcWPRMeslXpSDUFfw.png)

`$refs` are only populated after the component has been rendered, and they are not reactive. Hence we should avoid accessing `$refs` from within templates or computed properties.

**Q9. Why do we need local registration?**

Global registration often isn’t ideal. For example, if we are using a build system like Webpack, globally registering all components means that even if we stop using a component, it could still be included in our final build. This unnecessarily increases the amount of JavaScript your users have to download. In these cases, you can define your components as plain JavaScript objects:![](https://miro.medium.com/max/60/1*oVE7ZKNezskxLzQgTgcINw.png?q=20)![](https://miro.medium.com/max/748/1*oVE7ZKNezskxLzQgTgcINw.png)

Then define the components you’d like to use in a `components` option:![](https://miro.medium.com/max/60/1*5c9PbZby3bdaxS651l8Szg.png?q=20)![](https://miro.medium.com/max/813/1*5c9PbZby3bdaxS651l8Szg.png)

**Q10. What is Mixins?**

Mixins are a flexible way to distribute reusable functionalities for Vue components. A mixin object can contain any component options. When a component uses a mixin, all options in the mixin will be “mixed” into the component’s own options. Example:![](https://miro.medium.com/max/60/1*JGZHKV72_YabxlHj8DMOIQ.png?q=20)![](https://miro.medium.com/max/765/1*JGZHKV72_YabxlHj8DMOIQ.png)

**Q11. How Vue.js track changes?**

When you pass a plain JavaScript object to a Vue instance as its data option, Vue will walk through all of its properties and convert them to getter/setters using `Object.defineProperty`.

The getter/setters are invisible to the user, but under the hood they enable Vue to perform dependency-tracking and change-notification when properties are accessed or modified.

Every component instance has a corresponding watcher instance, which records any properties “touched” during the component’s render as dependencies. Later on when a dependency’s setter is triggered, it notifies the watcher, which in turn causes the component to re-render.

**Q12. What are Async Components?**

In large applications, we may need to divide the app into smaller chunks and only load a component from the server when it’s needed. To make that easier, Vue allows you to define our component as a factory function that asynchronously resolves your component definition. Vue will only trigger the factory function when the component needs to be rendered and will cache the result for future re-renders. For example:![](https://miro.medium.com/max/60/1*bwLaKhHzNIIzxoRdC6mz8Q.png?q=20)![](https://miro.medium.com/max/776/1*bwLaKhHzNIIzxoRdC6mz8Q.png)

As we can see, the factory function receives a resolve callback, which should be called when we have retrieved your component definition from the server. We can also call `reject(reason)` to indicate the load has failed.

**Q13. What are filters in Vue.js?**

Vue.js allows us to define filters that can be used to apply common text formatting. Filters are usable in two places: mustache interpolations and `v-bind`expressions. Filters should be appended to the end of the JavaScript expression, denoted by the "pipe" symbol:![](https://miro.medium.com/max/60/1*iox06xHDwqBJZcDrhKYTlQ.png?q=20)![](https://miro.medium.com/max/1125/1*iox06xHDwqBJZcDrhKYTlQ.png)

**Q14. What is Vue Router?**

Vue Router is the official router for Vue.js. It deeply integrates with Vue.js core to make building Single Page Applications with Vue.js easy to implement. Its features include:

* Nested route/view mapping
* Modular, component-based router configuration
* Route params, query, wildcards
* View transition effects powered by Vue.js’ transition system
* Fine-grained navigation control
* Links with automatic active CSS classes
* Customizable Scroll Behavior
* HTML5 history mode or hash mode, with auto-fallback in IE9

## _Q3_: Explain the differences between one-way data flow and two-way data binding? <a id="q3-explain-the-differences-between-one-way-data-flow-and-two-way-data-binding-"></a>

In one-way data flow the view\(UI\) part of application does not updates automatically when data Model is change we need to write some custom code to make it updated every time a data model is changed. In Vue js **v-bind** is used for one-way data flow or binding.

In two-way data binding the view\(UI\) part of application automatically updates when data Model is changed. In Vue.js **v-model** directive is used for two way data binding.

## _Q4_: How to create Two-Way Bindings in Vue.js? <a id="q4-how-to-create-two-way-bindings-in-vue-js-"></a>

`v-model` directive is used to create Two-Way Bindings in Vue js.In Two-Way Bindings data or model is bind with DOM and Dom is binded back to model.

In below example you can see how Two-Way Bindings is implemented.

```text
<div id="app">
  {{message}}
  <input v-model="message">
</div>
<script type="text/javascript">
  var message = 'Vue.js is rad';
  new Vue({ el: '#app', data: { message } });
</script>
```

Q5. Czy vue component jest vue instance?

Tak

## _Q13_: What is the difference v-bind and v-model? Provide some code example. <a id="q13-what-is-the-difference-v-bind-and-v-model-provide-some-code-example-"></a>

`v-model` is a **two-way binding for form inputs**. It combines `v-bind`, which _**brings a js value**_ **\*\*into the markup, and `v-on:input` to \_**update the js value\*\*\_.

Consider:

```text
<input v-model="something">
```

and it's just syntactic sugar for:

```text
<input
   v-bind:value="something"
   v-on:input="something = $event.target.value"
>
```

`v-model` works with all the basic HTML input types \(text, textarea, number, radio, checkbox, select\). You can use `v-model` with `input type=date` if your model stores dates as ISO strings \(`yyyy-mm-dd`\).

### Q14: What is vue instance?

Every Vue application works by creating a new Vue instance with the Vue function. Generally the variable vm \(short for ViewModel\) is used to refer Vue instance. You can create vue instance as below,

```text
var vm = new Vue({
  // options
})
```

As mentioned in the above code snippets, you need to pass options object. You can find the full list of options in the API reference.

### Q15. Why do you need to use key attribute on for directive?

In order to track each node’s identity, and thus reuse and reorder existing elements, you need to provide a unique `key`attribute for each item with in `v-for` iteration. An ideal value for key would be the unique id of each item. Let us take an example usage,

```text
<div v-for="item in items" :key="item.id">
  {{item.name}}
</div>
```

Hence, It is always recommended to provide a key with v-for whenever possible, unless the iterated DOM content is simple. **Note:** You shouldn’t use non-primitive values like objects and arrays as v-for keys. Use string or numeric values instead.

### Q16. What are the caveats of array changes detection?

Vue cannot detect changes for the array in the below two cases,

1. When you directly set an item with the index,For example,

   ```text
   vm.todos[indexOfTodo] = newTodo
   ```

2. When you modify the length of the array, For example,

```text
vm.todos.length = todosLength
```

You can overcome both the caveats using `set` and `splice` methods, Let's see the solutions with an examples,

**First use case solution**

```text
// Vue.set
Vue.set(vm.todos, indexOfTodo, newTodoValue)
(or)
// Array.prototype.splice
vm.todos.splice(indexOfTodo, 1, newTodoValue)
```

**Second use case solution**

```text
vm.todos.splice(todosLength)
```

### Q17. What are the event modifiers provided by vue?

Normally, javascript provides event.preventDefault\(\) or event.stopPropagation\(\) inside event handlers. You can use methods provided by vue, but these methods are meant for data logic instead of dealing with DOM events. Vue provides below event modifiers for v-on and these modifiers are directive postfixes denoted by a dot.

1. .stop
2. .prevent
3. .capture
4. .self
5. .once
6. .passive

Let's take an example of stop modifier,

```text
<!-- the click event's propagation will be stopped -->
<a v-on:click.stop="methodCall"></a>
```

You can also chain modifiers as below,

```text
<!-- modifiers can be chained -->
<a v-on:click.stop.prevent="doThat"></a>
```

### Q18: What are slots?

Vue implements a content distribution API using the element to serve as distribution outlets for content created after after the current Web Components spec draft. Let's create an alert component with slots for content insertion,

```text
Vue.component('alert', {
  template: `
    <div class="alert-box">
      <strong>Error!</strong>
      <slot></slot>
    </div>
  `
})
```

Now you can insert dynamic content as below,

```text
<alert>
  There is an issue with in application.
</alert>
```

### Q19. What is vue router and their features?

Vue Router is a official routing library for single-page applications designed for use with the Vue.js framework. Below are their features,

1. Nested route/view mapping
2. Modular, component-based router configuration
3. Route params, query, wildcards
4. View transition effects powered by Vue.js' transition system
5. Fine-grained navigation control
6. Links with automatic active CSS classes
7. HTML5 history mode or hash mode, with auto-fallback in IE9
8. Restore scroll position when going back in history mode

**Q20. How to make router param changes as reactive?**

When you navigate from one URL to other\(mapped with a single component\) using routes with params then the same component instance will be reused. Even though it is more efficient than destroying the old instance and then creating a new one, the lifecycle hooks of the component will not be called. This problem can be solved using either of the below approaches,

1. Watch the $route object:

```text
const User = {
  template: '<div>User {{ $route.params.name }} </div>',
  watch: {
    '$route' (to, from) {
      // react to route changes...
    }
  }
}
```

1. Use beforeRouteUpdate navigation guard: This is only available since 2.2 version.

```text
const User = {
  template: '<div>User {{ $route.params.name }} </div>',
  beforeRouteUpdate (to, from, next) {
    // react to route changes and then call next()
  }
}
```

Note that the beforeRouteEnter guard does NOT have access to `this`. Instead you can pass a callback to `next` to access the vm instance.

### Q21. How to create a plugin?

The Plugin is created by exposing an `install` method which takes Vue constructor as a first argument along with options. The structure of VueJS plugin with possible functionality would be as follows,

```text
MyPlugin.install = function (Vue, options) {
  // 1. add global method or property
  Vue.myGlobalMethod = function () {
    // some logic ...
  }

  // 2. add a global asset
  Vue.directive('my-directive', {
    bind (el, binding, vnode, oldVnode) {
      // some logic ...
    }
    ...
  })

  // 3. inject some component options
  Vue.mixin({
    created: function () {
      // some logic ...
    }
    ...
  })

  // 4. add an instance method
  Vue.prototype.$myMethod = function (methodOptions) {
    // some logic ...
  }
}
```

1. **What are functional components?**

   The functional components are just simple functions to create simple components just by passing a context. Every functional component follows two rules,

   1. **Stateless:** It doesn’t keep any state by itself
   2. **Instanceless:** It has no instance, thus no this

   You need to define `functional: true` to make it functional. Let's take an example of functional components,

   ```text
   Vue.component('my-component', {
     functional: true,
     // Props are optional
     props: {
       // ...
     },
     // To compensate for the lack of an instance,
     // we are now provided a 2nd context argument.
     render: function (createElement, context) {
       // ...
     }
   })
   ```

   **Note:** The functional components are quite popular in React community too.

2. **What are the similarities between VueJS and ReactJS?**

   Even though ReactJS and VueJS are two different frameworks there are few similarities\(apart from the common goal of utilized in interface design\) between them.

   1. Both frameworks are based on the **Virtual DOM** model
   2. They provide features such Component-based structure and reactivity
   3. They are intended for working with the root library, while all the additional tasks are transferred to other libraries\(routing, state management etc\).

3. **What is vuex?**

   Vuex is a state management pattern + library \(Flux-inspired Application Architecture\) for Vue.js applications. It serves as a centralized store for all the components in an application, with rules ensuring that the state can only be mutated in a predictable fashion.

4. **What are the major components of State Management Pattern?**

   The state management has state, view and actions as major components. The pattern followed by these components in a application is known as State Management Pattern. Below are the components in a detail,

   1. The **state**, which is the source of truth that drives our app
   2. The **view**, which is just a declarative mapping of the state
   3. The **actions**, which are the possible ways the state could change in reaction to user inputs from the view. Let us take a counter example which follows state management pattern with the above 3 components,

   ```text
   new Vue({
     // state
     data () {
       return {
         count: 0
       }
     },
     // view
     template: `
       <div>{{ count }}</div>
     `,
     // actions
     methods: {
       increment () {
         this.count++
       }
     }
   })
   ```

   **5. What are the principles for vuex application structure?**

   Vuex enforces below rules to structure any application.

   1. Application-level state is centralized in the store.
   2. The only way to mutate the state is by committing mutations, which are synchronous transactions.
   3. Asynchronous logic should be encapsulated in, and can be composed with actions. The project structure for any non-trivial application would be as below,

   [![](https://github.com/sudheerj/vuejs-interview-questions/raw/master/images/vuex-app-structure.png)](https://github.com/sudheerj/vuejs-interview-questions/blob/master/images/vuex-app-structure.png)

5. **What is vue-loader?**

   Vue-loader is a loader module for webpack that allows us to write single file components using the .vue file format. A single file component file has three sections namely template, script and style. The vue-loader module allows webpack to extract and process each section using separate loader modules such as the SASS or SCSS loaders. The setup thus allows us to seamlessly author apps using .vue files.

   The vue-loader module also allows static assets to be treated as module dependencies and enables processing using webpack loaders. And it also allows hot reloading during development.

**What are render functions? Cite an example.**

Vue allows us to build templates in a multitude of ways, the most common of which is to just use HTML with special directives and mustache tags for reactive features. You can, however, also build templates using JavaScript using a special class of functions, known as render functions. These functions are close to the compiler which means they’re more efficient and faster than other template types. Since you’re using JavaScript for writing render functions, you can use the language freely to add custom functionality directly wherever needed.

This is extremely useful for advanced scenarios where standard HTML templates may not be the best option.

**Here’s a Vue app that uses HTML as a template**

```text
new Vue({
  el: '#app',
  data: {
    fruits: ['Apples', 'Oranges', 'Kiwi']
  },
  template:
      `<div>
         <h1>Fruit Basket</h1>
         <ol>
           <li v-for="fruit in fruits">{{ fruit }}</li>
         </ol>
      </div>`
});
```

**Here’s the same app made using render functions:**

```text
new Vue({
  el: '#app',
  data: {
    fruits: ['Apples', 'Oranges', 'Kiwi']
  },
  render: function(createElement) {
    return createElement('div', [
      createElement('h1', 'Fruit Basket'),
      createElement('ol', this.fruits.map(function(fruit) { 
        return createElement('li', fruit); 
      }))
    ]);
  }
});
```

**Outputs:**

Fruit Basket

1. Apples
2. Oranges
3. Kiwi

In the above example, we’re using a function that returns a series of createElement\(\) invocations, each of which is responsible for generating an element. While the v-for directive does the job in the case of HTML based templates, when using render functions we can simply use the standard .map\(\) function to loop over the fruits data Array.


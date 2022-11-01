# Svelte Interview Questions & Answers

> Click :star:if you like the project. Pull Requests are highly appreciated!

### Table of Contents

| No. | Question                                                                                                                                                                            |
| --- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 1   | [What is Svelte.js](#what-is-svelte.js)                                                                                                                                             |
| 2   | [What is the difference between Svelte and the most popular frameworks like Vue or React](#what-is-the-difference-between-svelte-and-the-most-popular-frameworks-like-vue-or-react) |
| 3   | [Does Svelte support SSR and mobile app development](#does-svelte-support-ssr-and-mobile-app-development)                                                                           |
| 4   | [What is Svelte used for](#what-is-svelte-used-for)                                                                                                                                 |
| 5   | [What is Reactivity in app development in Svelte](#what-is-reactivity-in-app-development-in-svelte)                                                                                 |
| 6   | [What are the main advantages of Svelte compared to other front-end frameworks](#what-are-the-main-advantages-of-svelte-compared-to-other-front-end-frameworks)                     |
| 7   | [What is Data binding](#what-is-data-binding)                                                                                                                                       |
| 9   | [What are Event Modifiers](#what-are-event-modifiers)                                                                                                                               |
| 10  | [What are Components events](#what-are-components-events)                                                                                                                           |
| 11  | [What is Event Forwarding](#what-is-event-forwarding)                                                                                                                               |
| 12  | [What is class directive](#what-is-class-directive)                                                                                                                                 |
| 13  | [What is class directive](#what-is-class-directive)                                                                                                                                 |
| 14  | [What is store binding](#what-is-store-binding)                                                                                                                                     |
| 15  | [What is Context API](#what-is-context-api)                                                                                                                                         |
| 16  | [Contexts vs stores](#contexts-vs-stores)                                                                                                                                           |
| 17  | [Explain what are slots](#explain-what-are-slots)                                                                                                                                   |
| 18  | [What are named slots](#what-are-named-slots)                                                                                                                                       |
| 19  | [What are slot props](#what-are-slot-props)                                                                                                                                         |

1.  ### **What is Svelte.js**

    Svelte is a free and open-source front end compiler. It is used to solve the same problems for which React or Vue are used, but Svelte.js facilitates users to build applications in a declarative, component-driven way rather than to create an imperative DOM manipulation.

    **[⬆ Back to Top](#table-of-contents)**

2.  ### **What is the difference between Svelte and the most popular frameworks like Vue or React**

    Svelte converts your app into ideal JavaScript at build time, rather than interpreting your application code at run time. This means you don't pay the performance cost of the framework's abstractions, and you don't incur a penalty when your app first loads.

    Traditional frameworks like ReactJS and VueJS do the bulk of their work in the browser i.e on the run time while Svelte shifts that work into build step i.e during compile time. So, instead of updating the DOM using Virtual DOM diffing, Svelte writes code that surgically updates the DOM when the state of your app changes.

    Using other frameworks, after being built there is still a framework. Svelte compiles code to pure, ideal JavaScript. That’s why it calls itself the “disappearing framework” – by the time the app’s code appears in the browser, there is really no framework anymore.

    **[⬆ Back to Top](#table-of-contents)**

3.  ### **Does Svelte support SSR and mobile app development**

    Yes. Svelte has SvelteKit, similar to Next.js of React and Nuxt.js of Vue for SSR. SSR can speed up the first render of your app and improve its SEO. For mobile app development, there’s Svelte-Native. It works on top of NativeScript.

    **[⬆ Back to Top](#table-of-contents)**

4.  ### **What is Svelte used for**

    1. Highly reactivity apps
    2. Fast performance, small bundle
    3. Low-energy app

    **[⬆ Back to Top](#table-of-contents)**

5.  ### **What is Reactivity in app development in Svelte**

    Reactivity is a term that describes a behavior when input change is automatically and immediately reflected in the Document Object Model (DOM). For example, when an app is reactive, it means that any change of values (the result of user input) will be automatically reflected in the DOM.

    **[⬆ Back to Top](#table-of-contents)**

6.  ### **What are the main advantages of Svelte compared to other front-end frameworks**

    1. facilitates developers to write less code. It mainly aims to build boilerplate-free components using the already known languages such as HTML, CSS, and JavaScript
    2. truly reactive and brings reactivity to JavaScript itself. It does not require more complex state management libraries
    3. does not require virtual DOM. It compiles the code to tiny, framework-less vanilla JS. That's why the Svelte.js app starts fast, loads fast, and stays fast
    4. comparatively better than its competitors (like React, Vue or Angular) because it provides less code, less boilerplate, smaller bundles, more speed, and better performance

    **[⬆ Back to Top](#table-of-contents)**

7.  ### **What is Data binding**

    Svelte data flow is top-down. Sometimes it is helpful to break this rule and provide two ways of data binding. Great example of such a need is the input element. Basically there we need to listen to on:input, read the event.target.value and manually set value. But with svelte we can avoid such boilerplate:

    ```javascript
    <input bind:value={color} />
    ```

    **[⬆ Back to Top](#table-of-contents)**

8.  ### **What are DOM events**

    DOM events are basically just known events from Document Object Model, such as click, change etc. You can listen to any event on an element with the `on:` directive:

    ```html
    <div on:click="{handleClick}">Element</div>
    ```

    **[⬆ Back to Top](#table-of-contents)**

9.  ### **What are Event Modifiers**

    Event modifiers allows us to modify base event behavior:

    1. self - _only fires the event if the clicked element is the target_
    2. preventDefault - _prevent the default action (run e.preventDefault())_
    3. stopPropagation - _prevent the event reaching the next element (run e.stopPropagation())_
    4. once - _make sure the event can fire only once (removes handler)_
    5. capture - _fires the handler during the capture phase instead of the bubbling phase_
    6. trusted - _only trigger handler if event.isTrusted is true. I.e. if the event is triggered by a user action_
    7. passive - \*improves scrolling performance on touch/wheel events (Svelte will add it automatically where it's safe to do so)
    8. nonpassive - explicitly set passive: false

    Example:

    ```html
    <button on:click|once="{toggleModal}" />

    <!-- You can chain modifiers like this: -->
    <button on:click|self|once="{handleClick}" />
    ```

    **[⬆ Back to Top](#table-of-contents)**

10. ### **What are Components events**

    Components can also dispatch events. To do so, they must create an event dispatcher.

    ```javascript
    import { createEventDispatcher } from "svelte";

    const dispatch = createEventDispatcher();

    function sayHello() {
      dispatch("message", {
        text: "Hello!",
      });
    }
    ```

    And thanks to that we can listen in parent component for such custom event:

    ```html
    <Child on:message="{handleMessage}" />
    ```

    **[⬆ Back to Top](#table-of-contents)**

11. ### **What is Event Forwarding**

    If you want to listen to an event on some deeply nested component, the intermediate components must forward the event.

    ```html
    <Inner on:message />
    ```

    Such `on:message` directive will forward all `message` events.

    **[⬆ Back to Top](#table-of-contents)**

12. ### **What is class directive**

    Class directive allows us to specify with a JavaScript, what classes should be attached to HTML element:

    ```html
    <button class={selected  === 'foo' ? 'selected' : ''}>foo</button>
    ```

    That means: if `selected` is equal to `foo` add `selected` class to button element.

    Or in other way when `selected` is `true`:

    ```html
    <button class:selected>foo</button>
    ```

    **[⬆ Back to Top](#table-of-contents)**

13. ### **Does svelte have a global store**

    Yup. Svelte has its own replacement for common solutions like Redux or Ngrx. It’s just called writable stores.

    A store is simply an object with a subscribe method that allows interested parties to be notified whenever the store value changes.

    We have two kinds of stores:

    1. writable - we can read and modify data
    2. readable - we can only read data
    3. derived - create a store whose value is based on the value of one or more other stores. Store will update themselves automatically, when based stores will change

    Example of writable store:

    ```javascript
    const name = writable("world");
    ```

    Example of derived store:

    ```javascript
    export const name = writable("world");

    export const greeting = derived(name, ($name) => `Hello ${$name}!`);
    ```

    **[⬆ Back to Top](#table-of-contents)**

14. ### **What is store binding**

    If a store is writable, we can bind it’s value, just as you can bind to local component state.

    Example:

    ```javascript
    const name = writable('world');

    <input bind:value={$name}>
    ```

    **[⬆ Back to Top](#table-of-contents)**

15. ### **What is Context API**

    Provides a mechanism for components to talk to each other without passing around data (avoid props drilling) and functions as props, or dispatching lots of events.

    Creation of context:

    ```javascript
    import { key } from "./mapbox.js";

    setContext(key, {
      getValue: () => value,
    });
    ```

    Usage of context:

    ```javascript
    const { getMap } = getContext(key);
    ```

    The key of context id should be Symbol:

    ```javascript
    const key = Symbol();
    ```

    or any other unique value.

    **[⬆ Back to Top](#table-of-contents)**

16. ### **Contexts vs stores**

    They differ in that stores are available to any part of an app (global state), while a context is only available to a _component and its descendants_. This can be helpful if you want to use several instances of a component without the state of one interfering with the state of the others.

    **[⬆ Back to Top](#table-of-contents)**

17. ### **Explain what are slots**

    Slot is a place where we can put children through props. Like we have something like this:

    ```html
    <div>
      <p>I'm a child of the div</p>
    </div>
    ```

    But, if we want to pass children to our component:

    ```html
    <!-- Box component -->
    <div class="box">
      <slot></slot>
    </div>
    ```

    And from the usage side:

    ```html
    <Box>
      <h2>Header</h2>
      <p>Paragraph</p>
    </Box>
    ```

    **[⬆ Back to Top](#table-of-contents)**

18. ### **What are named slots**

    In case when we want to pass a few slots, we can name them. Name works like an identifier and thanks to them Svelte knows where to put a specific slot.

    Example:

    ```html
    <!-- Box component -->
    <div class="box">
      <slot name="”first”"> </slot>
      <slot name="”last”"> </slot>
    </div>

    <!-- Usage of Box component -->
    <Box>
      <span slot="first"> Rafał </span>

      <span slot="last"> Kostecki </span>
    </Box>
    ```

    **[⬆ Back to Top](#table-of-contents)**

19. ### **What are slot props**

    Just like casual components, slots can also have props. For instance we can pass a boolean.

    Example:

    ```html
    <!-- Hoverable component -->
    <div on:mouseenter="{enter}" on:mouseleave="{leave}">
      <slot hovering="{hovering}"></slot>
    </div>

    <!-- Usage of Hoverable component -->
    <Hoverable let:hovering="{hovering}">
      <div class:active="{hovering}">
        {#if hovering}
        <p>I am being hovered upon.</p>
        {:else}
        <p>Hover over me!</p>
        {/if}
      </div>
    </Hoverable>
    ```

    **[⬆ Back to Top](#table-of-contents)**

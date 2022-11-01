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

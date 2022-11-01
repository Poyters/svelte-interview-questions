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

1. ### What is Svelte.js

   Svelte is a free and open-source front end compiler. It is used to solve the same problems for which React or Vue are used, but Svelte.js facilitates users to build applications in a declarative, component-driven way rather than to create an imperative DOM manipulation.

   **[⬆ Back to Top](#table-of-contents)**

2. ### What is the difference between Svelte and the most popular frameworks like Vue or React

   Svelte converts your app into ideal JavaScript at build time, rather than interpreting your application code at run time. This means you don't pay the performance cost of the framework's abstractions, and you don't incur a penalty when your app first loads.

   Traditional frameworks like ReactJS and VueJS do the bulk of their work in the browser i.e on the run time while Svelte shifts that work into build step i.e during compile time. So, instead of updating the DOM using Virtual DOM diffing, Svelte writes code that surgically updates the DOM when the state of your app changes.

   Using other frameworks, after being built there is still a framework. Svelte compiles code to pure, ideal JavaScript. That’s why it calls itself the “disappearing framework” – by the time the app’s code appears in the browser, there is really no framework anymore.

   **[⬆ Back to Top](#table-of-contents)**

3. ### Does Svelte support SSR and mobile app development

   Yes. Svelte has SvelteKit, similar to Next.js of React and Nuxt.js of Vue for SSR. SSR can speed up the first render of your app and improve its SEO. For mobile app development, there’s Svelte-Native. It works on top of NativeScript.

   **[⬆ Back to Top](#table-of-contents)**

4. ### What is Svelte used for

   1. Highly reactivity apps
   2. Fast performance, small bundle
   3. Low-energy app

   **[⬆ Back to Top](#table-of-contents)**

5. ### What is Reactivity in app development in Svelte

   Reactivity is a term that describes a behavior when input change is automatically and immediately reflected in the Document Object Model (DOM). For example, when an app is reactive, it means that any change of values (the result of user input) will be automatically reflected in the DOM.

   **[⬆ Back to Top](#table-of-contents)**

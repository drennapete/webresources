<!-- al:1 -->

-   [Skip to main content](#content)
-   [Skip to search](#search)

<!-- al:2 -->

# Beginning our React ToDo app

<!-- al:3 -->

-   [Previous](/en-US/docs/Learn_web_development/Core/Frameworks_libraries/React_getting_started)
-   [Overview: JavaScript frameworks and libraries](/en-US/docs/Learn_web_development/Core/Frameworks_libraries)
-   [Next](/en-US/docs/Learn_web_development/Core/Frameworks_libraries/React_components)

<!-- al:4 -->

Let's say that we've been tasked with creating a proof-of-concept in React – an app that allows users to add, edit, and delete tasks they want to work on, and also mark tasks as complete without deleting them. This article will walk you through the basic structure and styling of such an application, ready for individual component definition and interactivity, which we'll add later.

<!-- al:5 -->

**Note:** If you need to check your code against our version, you can find a finished version of the sample React app code in our [todo-react repository](https://github.com/mdn/todo-react). For a running live version, see [https://mdn.github.io/todo-react/](https://mdn.github.io/todo-react/).

<!-- al:6 -->

<!-- al:7 -->

| Prerequisites: | Familiarity with the core HTML, CSS, and JavaScript languages, and the terminal/command line. |
| --- | --- |
| Learning outcomes: | Familiarity with our todo list case study, and getting the basic App structure and styling in place. |

<!-- al:8 -->

## [Our app's user stories](#our_apps_user_stories)

<!-- al:9 -->

In software development, a user story is an actionable goal from the perspective of the user. Defining user stories before we begin our work will help us focus our work. Our app should fulfill the following stories:

<!-- al:10 -->

As a user, I can

<!-- al:11 -->

-   read a list of tasks.
-   add a task using the mouse or keyboard.
-   mark any task as completed, using the mouse or keyboard.
-   delete any task, using the mouse or keyboard.
-   edit any task, using the mouse or keyboard.
-   view a specific subset of tasks: All tasks, only the active task, or only the completed tasks.

<!-- al:12 -->

We'll tackle these stories one-by-one.

<!-- al:13 -->

## [Pre-project housekeeping](#pre-project_housekeeping)

<!-- al:14 -->

Vite has given us some code that we won't be using at all for our project. The following terminal commands will delete it to make way for our new project. Make sure you're starting in the app's root directory!

<!-- al:15 -->

**Note:** If you stopped your server to do the terminal tasks mentioned above, you'll have to start it again using `npm run dev`.

<!-- al:16 -->

## [Project starter code](#project_starter_code)

<!-- al:17 -->

As a starting point for this project, we're going to provide two things: an `App()` function to replace the one you just deleted, and some CSS to style your app.

<!-- al:18 -->

### [The JSX](#the_jsx)

<!-- al:19 -->

Copy the following snippet to your clipboard, then paste it into `App.jsx`:

<!-- al:20 -->

Now open `index.html` and change the [`<title>`](/en-US/docs/Web/HTML/Reference/Elements/title) element's text to `TodoMatic`. This way, it will match the [`<h1>`](/en-US/docs/Web/HTML/Reference/Elements/Heading_Elements) at the top of our app.

<!-- al:21 -->

When your browser refreshes, you should see something like this:

![todo-matic app, unstyled, showing a jumbled mess of labels, inputs, and buttons](/en-US/docs/Learn_web_development/Core/Frameworks_libraries/React_todo_list_beginning/unstyled-app.png)

<!-- al:22 -->

It's ugly, and doesn't function yet, but that's okay — we'll style it in a moment. First, consider the JSX we have, and how it corresponds to our user stories:

<!-- al:23 -->

-   We have a [`<form>`](/en-US/docs/Web/HTML/Reference/Elements/form) element, with an [`<input type="text">`](/en-US/docs/Web/HTML/Reference/Elements/input/text) for writing out a new task, and a button to submit the form.
-   We have an array of buttons that will be used to filter our tasks.
-   We have a heading that tells us how many tasks remain.
-   We have our 3 tasks, arranged in an unordered list. Each task is a list item ([`<li>`](/en-US/docs/Web/HTML/Reference/Elements/li)), and has buttons to edit and delete it and a checkbox to check it off as done.

<!-- al:24 -->

The form will allow us to *make* tasks; the buttons will let us *filter* them; the heading and list are our way to *read* them. The UI for *editing* a task is conspicuously absent for now. That's okay – we'll write that later.

<!-- al:25 -->

### [Accessibility features](#accessibility_features)

<!-- al:26 -->

You may notice some unusual markup here. For example:

<!-- al:27 -->

Here, `aria-pressed` tells assistive technology (like screen readers) that the button can be in one of two states: `pressed` or `unpressed`. Think of these as analogs for `on` and `off`. Setting a value of `"true"` means that the button is pressed by default.

<!-- al:28 -->

The class `visually-hidden` has no effect yet, because we have not included any CSS. Once we have put our styles in place, though, any element with this class will be hidden from sighted users and still available to assistive technology users — this is because these words are not needed by sighted users; they are there to provide more information about what the button does for assistive technology users that do not have the extra visual context to help them.

<!-- al:29 -->

Further down, you can find our [`<ul>`](/en-US/docs/Web/HTML/Reference/Elements/ul) element:

<!-- al:30 -->

The `role` attribute helps assistive technology explain what kind of element a tag represents. A `<ul>` is treated like a list by default, but the styles we're about to add will break that functionality. This role will restore the "list" meaning to the `<ul>` element. If you want to learn more about why this is necessary, you can check out [Scott O'Hara's article, "Fixing Lists"](https://www.scottohara.me/blog/2019/01/12/lists-and-safari.html).

<!-- al:31 -->

The `aria-labelledby` attribute tells assistive technologies that we're treating our list heading as the label that describes the purpose of the list beneath it. Making this association gives the list a more informative context, which could help assistive technology users better understand the list's purpose.

<!-- al:32 -->

Finally, the labels and inputs in our list items have some attributes unique to JSX:

<!-- al:33 -->

The `defaultChecked` attribute in the `<input />` tag tells React to check this checkbox initially. If we were to use `checked`, as we would in regular HTML, React would log some warnings into our browser console relating to handling events on the checkbox, which we want to avoid. Don't worry too much about this for now — we will cover this later on when we get to using events.

<!-- al:34 -->

The `htmlFor` attribute corresponds to the `for` attribute used in HTML. We cannot use `for` as an attribute in JSX because `for` is a reserved word, so React uses `htmlFor` instead.

<!-- al:35 -->

### [A note on boolean attributes in JSX](#a_note_on_boolean_attributes_in_jsx)

<!-- al:36 -->

The `defaultChecked` attribute in the previous section is a boolean attribute – an attribute whose value is either `true` or `false`. Like in HTML, a boolean attribute is `true` if it's present and `false` if it's absent; the assignment on the right-hand side of the expression is optional. You can explicitly set its value by passing it in curly braces – for example, `defaultChecked={true}` or `defaultChecked={false}`.

<!-- al:37 -->

Because JSX is JavaScript, there's a gotcha to be aware of with boolean attributes: writing `defaultChecked="false"` will set a *string* value of `"false"` rather than a *boolean* value. Non-empty strings are [truthy](/en-US/docs/Glossary/Truthy), so React will consider `defaultChecked` to be `true` and check the checkbox by default. This is not what we want, so we should avoid it.

<!-- al:38 -->

If you'd like, you can practice writing boolean attributes with another attribute you may have seen before, [`hidden`](/en-US/docs/Web/HTML/Reference/Global_attributes/hidden), which prevents elements from being rendered on the page. Try adding `hidden` to the `<h1>` element in `App.jsx` to see what happens, then try explicitly setting its value to `{false}`. Note, again, that writing `hidden="false"` results in a truthy value so the `<h1>` *will* hide. Don't forget to remove this code when you're done.

<!-- al:39 -->

**Note:** The `aria-pressed` attribute used in our earlier code snippet has a value of `"true"` because `aria-pressed` is not a true boolean attribute in the way `checked` is.

<!-- al:40 -->

### [Implementing our styles](#implementing_our_styles)

<!-- al:41 -->

Paste the following CSS code into `src/index.css`:

<!-- al:42 -->

Save and look back at your browser, and your app should now have reasonable styling.

<!-- al:43 -->

## [Summary](#summary)

<!-- al:44 -->

Now our todo list app actually looks a bit more like a real app! The problem is: it doesn't actually do anything. We'll start fixing that in the next chapter!

<!-- al:45 -->

-   [Previous](/en-US/docs/Learn_web_development/Core/Frameworks_libraries/React_getting_started)
-   [Overview: JavaScript frameworks and libraries](/en-US/docs/Learn_web_development/Core/Frameworks_libraries)
-   [Next](/en-US/docs/Learn_web_development/Core/Frameworks_libraries/React_components)

<!-- al:46 -->

## Help improve MDN

[Learn how to contribute](/en-US/docs/MDN/Community/Getting_started)

<!-- al:47 -->

This page was last modified on Oct 31, 2025 by [MDN contributors](/en-US/docs/Learn_web_development/Core/Frameworks_libraries/React_todo_list_beginning/contributors.txt).

[View this page on GitHub](https://github.com/mdn/content/blob/main/files/en-us/learn_web_development/core/frameworks_libraries/react_todo_list_beginning/index.md?plain=1 "Folder: en-us/learn_web_development/core/frameworks_libraries/react_todo_list_beginning (Opens in a new tab)") • [Report a problem with this content](https://github.com/mdn/content/issues/new?template=page-report.yml&mdn-url=https%3A%2F%2Fdeveloper.mozilla.org%2Fen-US%2Fdocs%2FLearn_web_development%2FCore%2FFrameworks_libraries%2FReact_todo_list_beginning&metadata=%3C%21--+Do+not+make+changes+below+this+line+--%3E%0A%3Cdetails%3E%0A%3Csummary%3EPage+report+details%3C%2Fsummary%3E%0A%0A*+Folder%3A+%60en-us%2Flearn_web_development%2Fcore%2Fframeworks_libraries%2Freact_todo_list_beginning%60%0A*+MDN+URL%3A+https%3A%2F%2Fdeveloper.mozilla.org%2Fen-US%2Fdocs%2FLearn_web_development%2FCore%2FFrameworks_libraries%2FReact_todo_list_beginning%0A*+GitHub+URL%3A+https%3A%2F%2Fgithub.com%2Fmdn%2Fcontent%2Fblob%2Fmain%2Ffiles%2Fen-us%2Flearn_web_development%2Fcore%2Fframeworks_libraries%2Freact_todo_list_beginning%2Findex.md%0A*+Last+commit%3A+https%3A%2F%2Fgithub.com%2Fmdn%2Fcontent%2Fcommit%2F9f7e7e9075e9f2b1937d2c8000f52a8ff76bff52%0A*+Document+last+modified%3A+2025-10-31T15%3A27%3A28.000Z%0A%0A%3C%2Fdetails%3E "This will take you to GitHub to file a new issue.")
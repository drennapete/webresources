<!-- al:1 -->

# Why semantic HTML still matters

<!-- al:2 -->

21st July, 2025

![](https://www.jonoalderson.com/wp-content/uploads/file_00000000aaf061faafa67952f692b4b1-1-760x350.png)

<!-- al:3 -->

Somewhere along the way, we forgot how to write HTML – or why it mattered in the first place.

<!-- al:4 -->

Modern development workflows prioritise components, utility classes, and JavaScript-heavy rendering. HTML becomes a *byproduct*, not a *foundation*.

<!-- al:5 -->

And that shift comes at a cost – in performance, accessibility, resilience, and how machines (and people) interpret your content.

<!-- al:6 -->

I’ve written elsewhere about [how JavaScript is killing the web](https://www.jonoalderson.com/conjecture/javascript-broke-the-web-and-called-it-progress/). But one of the most fixable, overlooked parts of that story is **semantic HTML**.

<!-- al:7 -->

This piece is about what we’ve lost – and why it still matters.

<!-- al:8 -->

## [Semantic HTML is how machines understand meaning](#h-semantic-html-is-how-machines-understand-meaning)

<!-- al:9 -->

HTML isn’t just how we place elements on a page. It’s a *language* – with a vocabulary that expresses meaning

<!-- al:10 -->

Tags like `<article>`, `<nav>` and `<section>` aren’t *decorative*. They express *intent*. They signal *hierarchy*. They tell machines what your content *is*, and how it *relates* to everything else.

<!-- al:11 -->

Search engines, accessibility tools, AI agents, and task-based systems all rely on structural signals – sometimes explicitly, sometimes heuristically. Not every system requires perfect markup, but when they can take advantage of it, semantic HTML can give them clarity. And in a web full of structurally ambiguous pages, that clarity can be a competitive edge.

<!-- al:12 -->

Semantic markup doesn’t guarantee better indexing or extraction – but it creates a foundation that systems can use, now and in the future. It’s a signal of *quality*, *structure*, and *intent*.

<!-- al:13 -->

If everything is a `<div>` or a `<span>`, then nothing is *meaningful*.

<!-- al:14 -->

## [It’s not just bad HTML – it’s meaningless markup](#h-it-s-not-just-bad-html-it-s-meaningless-markup)

<!-- al:15 -->

It’s easy to dismiss this as a purity issue. Who cares whether you use a `<div>` or a `<section>`, as long as it looks right?

<!-- al:16 -->

But this isn’t about pedantry. Meaningless markup doesn’t just make your site harder to read – it makes it harder to *render*, harder to *maintain*, and harder to *scale*.

<!-- al:17 -->

This kind of abstraction leads to markup that often looks like this:

<!-- al:18 -->

```
<div class="tw-bg-white tw-p-4 tw-shadow tw-rounded-md">
  <div class="tw-flex tw-flex-col tw-gap-2">
    <div class="tw-text-sm tw-font-semibold tw-uppercase tw-text-gray-500">ACME Widget</div>
    <div class="tw-text-xl tw-font-bold tw-text-blue-900">Blue Widget</div>
    <div class="tw-text-md tw-text-gray-700">Our best-selling widget for 2025. Lightweight, fast, and dependable.</div>
    <div class="tw-mt-4 tw-flex tw-items-center tw-justify-between">
      <div class="tw-text-lg tw-font-bold">$49.99</div>
      <button class="tw-bg-blue-600 tw-text-white tw-px-4 tw-py-2 tw-rounded hover:tw-bg-blue-700">Buy now</button>
    </div>
  </div>
</div>
```

<!-- al:19 -->

Sure, this works. It’s styled. It renders. But it’s semantically dead. 

<!-- al:20 -->

It gives you no sense of what this content is. Is it a product listing? A blog post? A call to action? 

<!-- al:21 -->

You can’t tell at a glance – and neither can a screen reader, a crawler, or an agent trying to extract your pricing data.

<!-- al:22 -->

Here’s the same thing with meaningful structure:

<!-- al:23 -->

```
<article class="product-card">
  <header>
    <p class="product-brand">ACME Widget</p>
    <h1 class="product-name">Blue Widget</h1>
  </header>
  <p class="product-description">Our best-selling widget for 2025. Lightweight, fast, and dependable.</p>
  <footer class="product-footer">
    <span class="product-price">$49.99</span>
    <button class="buy-button">Buy now</button>
  </footer>
</article>
```

<!-- al:24 -->

Now it tells a *story*. There’s *structure*. There’s *intent*. You can target it in your CSS. You can extract it in a scraper. You can navigate it in a screen reader. It means something.

<!-- al:25 -->

Semantic HTML is the foundation of accessibility. Without structure and meaning, assistive technologies can’t parse your content. Screen readers don’t know what to announce. Keyboard users get stuck. Voice interfaces can’t find what you’ve buried in divs. Clean, meaningful HTML isn’t just good practice – it’s how people access the web.

<!-- al:26 -->

That’s not to say frameworks are inherently bad, or inaccessible. Tailwind, atomic classes, and inline styles can absolutely be useful – especially in complex projects or large teams where consistency and speed matter. They can reduce cognitive overhead. They can improve velocity.

<!-- al:27 -->

But they’re *tools*, not *answers*. And when every component devolves into a soup of near-duplicate utility classes – tweaked for every layout and breakpoint – you lose the plot. The structure disappears. The purpose is obscured.

<!-- al:28 -->

This isn’t about abstraction. It’s about what you lose in the process.

<!-- al:29 -->

And that loss doesn’t just hurt semantics – it hurts *performance*. In fact, it’s one of the biggest reasons the modern web feels slower, heavier, and more fragile than ever.

<!-- al:30 -->

## [Semantic rot wrecks performance](#h-semantic-rot-wrecks-performance)

<!-- al:31 -->

We’ve normalised the idea that HTML is just a render target – that we can throw arbitrary markup at the browser and trust it to figure it out. And it does. Browsers are astonishingly good at fixing our messes.

<!-- al:32 -->

But that forgiveness has a *cost*.

<!-- al:33 -->

Rendering engines are designed to be fault-tolerant. They’ll infer roles, patch up bad structure, and try to render things as you intended. But every time they have to do that – every time they have to guess what your `<div>` soup is *trying* to be – it costs time. That’s CPU cycles. That’s GPU time. That’s power, especially on mobile.

<!-- al:34 -->

Let’s break down where and how the bloat hits hardest – and why it matters.

<!-- al:35 -->

### [Big DOMs are slow to render](#h-big-doms-are-slow-to-render)

<!-- al:36 -->

Every single node in the DOM adds overhead. During rendering, the browser walks the DOM tree, builds the CSSOM, calculates styles, resolves layout, and paints pixels. More nodes mean more work at each stage.

<!-- al:37 -->

It’s not just about download size (though that matters too – more markup means more bytes, and *potentially* less efficient compression). It’s about render performance. A bloated DOM means longer layout and paint phases, more memory usage, and higher energy usage.

<!-- al:38 -->

Even simple interactions – like opening a modal or expanding a list – can trigger reflows that crawl through your bloated DOM. And suddenly your “simple” page lags, stutters, or janks.

<!-- al:39 -->

You can see this in Chrome DevTools. Open the *Performance* tab, record a trace, and watch the flame chart light up every time your layout engine spins it’s wheels.

<!-- al:40 -->

> <!-- al:41 -->
>
> Fun fact: parsing isn’t the bottleneck — browsers like Chromium can process HTML at tens of GB/s on modern CPUs. The real cost comes during CSSOM construction, layout, paint, and composite. Also, HTML parsing is blocking only when you hit a non-deferred `<script>` or a render-blocking stylesheet – which again underscores why clean markup still matters, but you also need smart loading order.

<!-- al:42 -->

### [Complex trees cause layout thrashing](#h-complex-trees-cause-layout-thrashing)

<!-- al:43 -->

But it’s not just about how much markup you have – it’s about how it’s structured. Deep nesting, wrapper bloat, and overly abstracted components create DOM trees that are hard to reason about and costly to render. The browser has to work harder to figure out what changes affect what – and that’s where things start to fall apart.

<!-- al:44 -->

Toggle a single class, and you might invalidate layout across the entire viewport. That change cascades through parent-child chains, triggering layout shifts and visual instability. Components reposition themselves unexpectedly. Scroll anchoring fails, and users lose their position mid-interaction. The whole experience becomes unstable.

<!-- al:45 -->

And because this all happens in real time – on every interaction – it hits your frame budget. Targeting 60fps? That gives you just ~16ms per frame. Blow that budget, and users feel the lag instantly.

<!-- al:46 -->

You’ll see it in Chrome’s DevTools – in the “*Layout Shift Regions*” or in the “*Frames*” graph as missed frames stack up.

<!-- al:47 -->

> <!-- al:48 -->
>
> When you mutate the DOM, browsers don’t *always* re-layout the whole tree – there’s incremental layout processing. But deeply nested or ambiguous markup still triggers expensive ancestor checks. Projects like Facebook’s “Spineless Traversal” show that browsers still pay a performance penalty when many nodes need checking.

<!-- al:49 -->

### [Redundant CSS increases recalculation cost](#h-redundant-css-increases-recalculation-cost)

<!-- al:50 -->

A bloated DOM is bad enough – but bloated stylesheets make things even worse.

<!-- al:51 -->

Modern CSS workflows – especially in componentised systems – often lead to duplication. Each component declares its own styles – even when they repeat. There’s no cascade. No shared context. Specificity becomes a mess, and overrides are the default.

<!-- al:52 -->

For example, here’s what that often looks like:

<!-- al:53 -->

```
/* button.css */.btn {
  background-color: #006;
  color: #fff;
  font-weight: bold;
}

/* header.css */.header .btn {
  background-color: #005;
}

/* card.css */.card .btn {
  background-color: #004;
}
```

<!-- al:54 -->

Each file redefines the same thing. The browser has to parse, apply, and reconcile all of it. Multiply this by *hundreds* of components, and your CSSOM – the browser’s internal model of all CSS rules – balloons.

<!-- al:55 -->

Every time something changes (like a class toggle), the browser has to re-evaluate which rules apply where. More rules, more recalculations. And on lower-end devices, that becomes a bottleneck.

<!-- al:56 -->

Yes, atomic CSS systems like Tailwind can reduce file size and increase reuse. But only when used intentionally. When every component gets wrapped in a dozen layers of utility classes, and each utility is slightly tweaked (margin here, font there), you end up with thousands of unique combinations – many of which are nearly identical.

<!-- al:57 -->

The cost isn’t just size. It’s churn.

<!-- al:58 -->

> <!-- al:59 -->
>
> Browsers match selectors from right to left (e.g., for `div.card p span`, they check → parent → etc). This is efficient for clear, specific selectors – but bloated deep trees or generic cascading rules force lots of overs canning. 

<!-- al:60 -->

### [Autogenerated classes break caching and targeting](#h-autogenerated-classes-break-caching-and-targeting)

<!-- al:61 -->

It’s become common to see class names like `.sc-a12bc`, `.jsx-392hf`, or `.tw-abc123`. These are often the result of CSS-in-JS systems, scoped styles, or build-time hashing. The intent is clear: localise styles to avoid global conflicts. And that’s not a bad idea.

<!-- al:62 -->

But this approach comes with a different kind of *fragility*.

<!-- al:63 -->

If your classes are ephemeral – if they change with every build – then:

<!-- al:64 -->

-   Your analytics tags break.
-   Your end-to-end tests need constant maintenance.
-   Your caching strategies fall apart.
-   Your markup diffs become unreadable.
-   And your CSS becomes non-reusable by default.

<!-- al:65 -->

From a performance perspective, that last point is critical. Caching only works when things are predictable. The browser’s ability to cache and reuse parsed stylesheets depends on consistent selectors. If every component, every build, every deployment changes its class names, the browser has to reparse and reapply everything.

<!-- al:66 -->

Worse, it forces tooling to rely on brittle workarounds. Want to target a button in your checkout funnel via your tag manager? Good luck if it’s wrapped in three layers of hashed components.

<!-- al:67 -->

This isn’t hypothetical. It’s a common pain point in modern frontend stacks, and one that bloats everything – code, tooling, rendering paths.

<!-- al:68 -->

Predictable, semantic class names don’t just make your life easier. They make the web faster.

<!-- al:69 -->

### [Semantic tags can provide layout hints](#h-semantic-tags-can-provide-layout-hints)

<!-- al:70 -->

Semantic HTML isn’t just about meaning or accessibility. It’s scaffolding. Structure. And that structure gives both you and the browser something to work with.

<!-- al:71 -->

Tags like `<main>`, `<nav>`, `<aside>`, and `<footer>` aren’t just semantic – they’re block-level by default, and they naturally segment the page. That segmentation often lines up with how the browser processes and paints content. They don’t guarantee performance wins, but they create the conditions for them.

<!-- al:72 -->

When your layout has clear boundaries, the browser can scope its work more effectively. It can isolate style recalculations, avoid unnecessary reflows, and better manage things like scroll containers and sticky elements.

<!-- al:73 -->

More importantly: in the *paint* and *composite* phases, the browser can distribute rendering work across multiple threads. GPU compositing pipelines benefit from well-structured DOM regions – especially when they’re paired with properties like `contain: paint` or `will-change: transform`. By creating isolated layers, you reduce the overhead of re-rasterising large portions of the page.

<!-- al:74 -->

If everything is a giant stack of nested `<div>`s, there’s no clear opportunity for this kind of isolation. Every interaction, animation, or resize event risks triggering a reflow or repaint that affects the entire tree. You’re not just making it harder for yourself – you’re bottlenecking the rendering engine.

<!-- al:75 -->

Put simply: semantic tags help you work *with* the browser instead of *fighting* it. They’re not magic, but they make the magic possible.

<!-- al:76 -->

### [Animations and the compositing catastrophe](#h-animations-and-the-compositing-catastrophe)

<!-- al:77 -->

Animations are where well-structured HTML either shines… or fails catastrophically.

<!-- al:78 -->

Modern browsers aim to offload animation work to the GPU. That’s what enables silky-smooth transitions at 60fps or higher. But for that to happen, the browser needs to isolate the animated element onto its own compositing layer. Only certain CSS properties qualify for this kind of GPU-accelerated treatment – most notably `transform` and `opacity`.

<!-- al:79 -->

If you animate something like `top`, `left`, `width`, or `margin`, you’re triggering the layout engine. That means recalculating layout for everything downstream of the change. That’s main-thread work, and it’s expensive.

<!-- al:80 -->

On a simple page? Maybe you get away with it.

<!-- al:81 -->

On a deeply nested component with dozens of siblings and dependencies? Every animation becomes a layout thrash. And once your animation frame budget blows past 16ms (the limit for 60fps), things get janky. Animations stutter. Interactions lag. Scroll becomes sluggish.

<!-- al:82 -->

You can see this in DevTools’ Performance panel – layout recalculations, style invalidations, and paint operations lighting up the flame chart.

<!-- al:83 -->

Semantic HTML helps here too. Proper structural boundaries allow for more effective use of modern CSS containment strategies:

<!-- al:84 -->

`contain: layout;` tells the browser it doesn’t need to recalculate layout outside the element.

<!-- al:85 -->

`will-change: transform;` hints that a compositing layer is needed.

<!-- al:86 -->

`isolation: isolate;` and `contain: paint;` can help prevent visual spillover and force GPU layers.

<!-- al:87 -->

But these tools only work when your DOM is rational. If your animated component is nested inside an unpredictable pile of generic `<div>`s, the browser can’t isolate it cleanly. It doesn’t know what might be affected – so it plays it safe and recalculates everything.

<!-- al:88 -->

That’s not a browser flaw. It’s a developer failure.

<!-- al:89 -->

Animation isn’t just about what moves. It’s about what *shouldn’t*.

<!-- al:90 -->

> <!-- al:91 -->
>
> Rendering and painting are parallel operations in modern engines. But DOM/CSS changes often force main-thread syncs, killing that advantage. 

<!-- al:92 -->

> <!-- al:93 -->
>
> CSS layering via `will-change: transform` or the newer `layer()` syntax tells the GPU to handle composites separately. That avoids layout and paint in the main thread – but only when the DOM structure allows distinct layering containers.

<!-- al:94 -->

### [CSS containment and visibility: powerful, but fragile](#h-css-containment-and-visibility-powerful-but-fragile)

<!-- al:95 -->

Modern CSS gives us powerful tools to manage performance – but they’re only effective when your HTML gives them room to breathe.

<!-- al:96 -->

Take `contain`. You can use `contain: layout`, `paint`, or even `size` to tell the browser “*don’t look outside this box – nothing in here affects the rest of the page.*” This can drastically reduce the cost of layout recalculations, especially in dynamic interfaces.

<!-- al:97 -->

But that only works when your markup has clear structural boundaries.

<!-- al:98 -->

If your content is tangled in a nest of non-semantic wrappers, or if containers inherit unexpected styles or dependencies, then containment becomes unreliable. You can’t safely contain what you can’t isolate. The browser won’t take the risk.

<!-- al:99 -->

Likewise, `content-visibility: auto` is one of the most underrated tools in the modern CSS arsenal. It lets the browser skip rendering elements that aren’t visible on-screen – effectively “virtualising” them. That’s huge for long pages, feeds, or infinite scroll components.

<!-- al:100 -->

But it comes with caveats. It requires predictable layout, scroll anchoring, and structural coherence. If your DOM is messy, or your components leak styles and dependencies up and down the tree, it backfires – introducing layout jumps, rendering bugs, or broken focus states.

<!-- al:101 -->

These aren’t magic bullets. They’re performance contracts. And messy markup breaks those contracts.

<!-- al:102 -->

Semantic HTML – and a clean, well-structured DOM – is what makes these tools viable in the first place.

<!-- al:103 -->

<!-- al:104 -->

> <!-- al:105 -->
>
> MDN’s docs highlight how `contain: content` (shorthand for `layout`+`paint`+`style`) lets browsers optimize entire subtrees independently
> Real-world A/B tests show INP latency improvements on e‑commerce pages using `content-visibility: auto`.

<!-- al:106 -->

## [Agents are the new users – and they care about structure](#h-agents-are-the-new-users-and-they-care-about-structure)

<!-- al:107 -->

The web isn’t just for humans anymore.

<!-- al:108 -->

Search engines were the first wave – parsing content, extracting meaning, and ranking based on structure and semantics. But now we’re entering the era of AI agents, assistants, scrapers, task runners, and LLM-backed automation. These systems don’t browse your site. They don’t scroll. They don’t click. They parse.

<!-- al:109 -->

They look at your markup and ask:

<!-- al:110 -->

-   What is this?
-   How is it structured?
-   What’s important?
-   How does it relate to everything else?

<!-- al:111 -->

A clean, semantic DOM answers those questions clearly. A soup of `<div>`s does not.

<!-- al:112 -->

And when these agents have to choose between ten sites that all claim to sell the same widget, the one that’s easier to interpret, extract, and summarise will win.

<!-- al:113 -->

That’s not hypothetical. Google’s shopping systems, summarisation agents like Perplexity, AI browsers like Arc, and assistive tools for accessibility are all examples of this shift in motion. Your site isn’t just a visual experience anymore – it’s an interface. An API. A dataset.

<!-- al:114 -->

If your markup can’t support that? You’re out of the conversation.

<!-- al:115 -->

And yes – smart systems can and do infer structure when they have to. But that’s extra work. That’s imprecise. That’s risk.

<!-- al:116 -->

In a competitive landscape, well-structured markup isn’t just an optimisation – it’s a differentiator.

<!-- al:117 -->

## [Structure is resilience](#h-structure-is-resilience)

<!-- al:118 -->

Semantic HTML isn’t just about helping machines understand your content. It’s about building interfaces that hold together under pressure.

<!-- al:119 -->

Clean markup is easier to debug. Easier to adapt. Easier to progressively enhance. If your JavaScript fails, or your stylesheets don’t load, or your layout breaks on an edge-case screen – semantic HTML means there’s still something usable there.

<!-- al:120 -->

That’s not just good practice. It’s how you build software for the real world.

<!-- al:121 -->

Because real users have flaky connections. Real devices have limited power. Real sessions include edge cases you didn’t test for.

<!-- al:122 -->

Semantic markup gives you a baseline. A fallback. A foundation.

<!-- al:123 -->

## [Structure isn’t optional](#h-structure-isn-t-optional)

<!-- al:124 -->

If you want to build for performance, accessibility, discoverability, or resilience – if you want your site to be fast, understandable, and adaptable – start with HTML that means something.

<!-- al:125 -->

Don’t treat markup as an afterthought. Don’t let your tooling bury the structure. Don’t build interfaces that only work when the stars align and the JavaScript loads.

<!-- al:126 -->

Semantic HTML is a foundation. It’s fast. It’s robust. It’s self-descriptive. It’s future-facing.

<!-- al:127 -->

It doesn’t stop you using Tailwind. It doesn’t stop you using React. But it does ask you to be deliberate. To design your structure with intent. To write code that tells a story – not just to humans, but to browsers, bots, and agents alike.

<!-- al:128 -->

This isn’t nostalgia. This is infrastructure.

<!-- al:129 -->

And if the web is going to survive the next wave of complexity, automation, and expectation – we need to remember how to build it properly.

<!-- al:130 -->

That starts with remembering how to write HTML – and why we write it the way we do. Not as a byproduct of JavaScript, or an output of tooling, but as the foundation of everything that follows. 

![](https://www.jonoalderson.com/wp-content/gravatars/ee1661ba8e00226c4b361e7610437714caa1aae1f9913efda4617e639e98732b.jpeg)

 Name\*

 Email\*

<!-- al:131 -->

10 Comments

<!-- al:132 -->

Inline Feedbacks

<!-- al:133 -->

View all comments

![](https://www.jonoalderson.com/wp-content/gravatars/5c5fb6f7e796bf5b7869fd3cd306cbf00a99c021fa47bb80ed844b1aeda1b331.jpeg)

<!-- al:134 -->

Simon

<!-- al:135 -->

Sep 11, 2025 6:15 pm

<!-- al:136 -->

Good article and I agree that semantic markup is a bit of a dead art. Two points though:

<!-- al:137 -->

It’s slightly disingenuous in your example to imply that Tailwind or utility classes cannot be used with semantic markup. Makes no difference how you decide to apply your styles. 

<!-- al:138 -->

And I’ve been curious just how critical semantic markup is. For example if I made a very popular website with tables or div soup I can almost put money on it that search engines would surface it just fine. Their job is to sift through all the cruft

<!-- al:139 -->

For accessibility sake, you could also achieve the same with ARIA and role attributes. Personally that isn’t for me, and you get a lot for free with some elements but if you look at Twitter web which used React Native Web, it’s entirely accessible

Reply

![](https://www.jonoalderson.com/wp-content/gravatars/5ce79ba286041ee7a2d40d051684ebb15fa44bfa0e2a84e1bb8f355f9918bd58.jpeg)

<!-- al:140 -->

Glen Ihrig

<!-- al:141 -->

Aug 14, 2025 3:01 am

<!-- al:142 -->

I program in Rust, where the argument against its use is that it takes too long to write. But the argument is favor is that once written time is saved on maintenance. I suspect the same arguments would apply to semantic HTML. I have spent way too many hours wading through pages afflicted with div-itis trying to find a simple style bug.

<!-- al:143 -->

I suppose maybe it comes down to the expected longevity of the project. If it’s a quick POC (proof of concept), maybe “quick and dirty” will pass. But if, or when, the POC becomes a production product, will there be time to trash the POC and start from scratch? Usually time pressure and deadlines require the POC, and the mess, to persist.

Reply

![](https://www.jonoalderson.com/wp-content/gravatars/ffc9641a48e2ce1cc3b55e7ce695cda733b048ac5790731661c2d2bc9f4c23c3.png)

<!-- al:144 -->

Jon

<!-- al:145 -->

Aug 9, 2025 5:47 pm

<!-- al:146 -->

I really like pico.css for this. It encourages proper layout. And now with Layering I can bring it in as a base layer and then add any changes on top of it easily. I wish most CSS frameworks were this way. Even if you keep the same semantics as pico and then just change things around.

<!-- al:147 -->

Now, I just need to find a good lib for structuring the page. I can use vanilla CSS for some of it. But it is nice to have something that helps with that. Some small CSS lib would work. I suppose I could just do all my own. I’ve done simple grid and flex classes that get me most of the way.

Reply

![](https://www.jonoalderson.com/wp-content/gravatars/68002b5e62c9149f6ac0bec2e2f2eb6ae63f61ba42bffdb0e0b68e1633a24a1d.png)

<!-- al:148 -->

Danny Engelman

<!-- al:149 -->

Aug 6, 2025 6:43 pm

<!-- al:150 -->

Don’t know if I spammed you already.
There is more to fighting the DIV-soup.
I wrote a blog-post about the Custom Elements hardly anyone is using:
[https://dev.to/dannyengelman/not-a-div-insidein-sightsite-18lj](https://dev.to/dannyengelman/not-a-div-insidein-sightsite-18lj)

Reply

![](https://www.jonoalderson.com/wp-content/gravatars/f3d4179509cc073caafa786919d7e40d6757a21a6e68dcf04cb7558b10327e1e.png)

<!-- al:151 -->

Shaji Ahmed

<!-- al:152 -->

Aug 5, 2025 8:50 am

<!-- al:153 -->

Interesting… as an experiment I started writing specifications for something similar for myself a few days ago to see how far I get with semantic component tags, and non-cascading styles. 

<!-- al:154 -->

I build applications and most of the time I’m wrestling with div-itis and what not. I look around at all the nice components that can be offered as first-class citizens in browsers, but are not. 

<!-- al:155 -->

And like you said, it will be a lot simpler for AI to deal with semantic html than the mess it is right now.

Reply

![](https://www.jonoalderson.com/wp-content/gravatars/dee8fc566a4bf3783c16ed93cbb476e36c13bd98b8ca64227c12824aa086ac53.png)

<!-- al:156 -->

MyQuests

<!-- al:157 -->

Jul 28, 2025 11:10 pm

<!-- al:158 -->

Absolutely spot on. Structure is the backbone of the web, not a luxury, but a necessity. This is a clear reminder that semantic HTML isn’t old-fashioned; it’s timeless engineering. It provides resilience when scripts fail, clarity for search engines and assistive tech, and a solid base for performance and maintainability. Frameworks and tooling should enhance, not obscure, the fundamentals. If we want a web that lasts, fast, accessible, and adaptable, we must stop treating HTML as an implementation detail and start treating it as infrastructure.

Reply

![](https://www.jonoalderson.com/wp-content/gravatars/5d88aa35348b441645d8da0131b5d11235f2421daec6e4006950c9ae8b73839e.jpeg)

<!-- al:159 -->

Ikenna Ene

<!-- al:160 -->

Jul 23, 2025 6:10 pm

<!-- al:161 -->

This is a very detailed analysis of the cost of poor design architecture. While semantics are great factor in render efficiency they might be impractical in business environments where deadlines and sprints are a daily occurrence. In any case they are vital for maintenance and experience. Thanks for sharing.

Reply

![](https://www.jonoalderson.com/wp-content/gravatars/479b55d17644eed86c1ce89af5ae4087fb0e2c0ffe9178e8bfd11faa99f20fc4.jpeg)

<!-- al:162 -->

Helena Plantin

<!-- al:163 -->

Reply to  [Ikenna Ene](#comment-4483)

<!-- al:164 -->

Aug 9, 2025 9:58 am

<!-- al:165 -->

I do not understand the belief that semantic HTML should take a longer time to code than div?

Reply

![](https://www.jonoalderson.com/wp-content/gravatars/0fb221a069cbdba0248f20c94df54ea49fb30e9b8353a60ad6b9c175a146b0a3.jpeg)

<!-- al:166 -->

Kim Krause Berg

<!-- al:167 -->

Jul 23, 2025 2:54 pm

<!-- al:168 -->

Bravo! So much in this article that’s vital and should be part of every design and QA methodology. This is one of the reasons why AI bothers me. I prefer to do the work. I need to know why it matters.

Reply

![](https://www.jonoalderson.com/wp-content/gravatars/7d81ae2ca2bce190aab4edfabde03b1eebb6f16bd84bc493732dd54b22db1e45.jpeg)

<!-- al:169 -->

Curtis Osano

<!-- al:170 -->

Jul 22, 2025 11:58 am

<!-- al:171 -->

This is truly inspiring and will add this to minimum requirement for developers i work with. Div soups everywhere i look.

Reply

Insert
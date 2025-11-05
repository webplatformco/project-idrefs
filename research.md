# User Quotes around IDREF pain points

## State of HTML surveys

### 2023

> TODO

### 2024

> TODO

### 2025

> TODO

## Social media

### Bramus’s posts

> 🙋‍♂️❓
>
> Using attributes like `for` require you to reference another element using that element’s `id`.
>
> E.g. `<label for="x"></label> … <input id="x">`
>
> Do you sometimes wish you had another way to refer to another element on the page, without needing to generate an id? If so, what would you want?

#### [Bluesky Post](https://bsky.app/profile/did:plc:343p6xcgmvkpz5abgezlgyep/post/3lw7kzprc6c25)

> TODO

#### [Mastodon Post](https://front-end.social/@bramus/115016389746283451)

> TODO

#### [X Post](https://x.com/bramus/status/1955283107134709886)

> TODO

### Noam’s posts

### Alice’s posts

> - What are the specific pain points around using IDs?
> - How does existing tooling address these pain points (i.e. what “cow paths” are there that we could look at?)
> - How does existing tooling fail to adequately address those pain points?
> - How are these pain points impacting authors’ abilities to author usable, accessible web pages?
> - What do authors like about IDs?
> - What design constraints should we consider for any potential solution?
> - What is the user impact of breakages in element associations? Who is impacted? How can we minimise that risk?

Responses (also on [HedgeDoc](https://notes.igalia.com/XlsPwU5sQfuaWYHwhtBMtA)):

---

I love using AlpineJs’s `x-id` and `$id` and `:id` to have it magically make sure id attributes are unique. https://alpinejs.dev/directives/id

https://mas.to/@maxfenton/115049731728027508

---

- What are the specific pain points around using IDs?

1. Frequently have to append a uuid or database ID to make it prefixed but unique, which means JS required.
2. Lots of noisy duplication between properties like: href, for, aria-controls, aria-labeledby, aria-describedby, anchor-name idents, etc. Then IDs like foo-123, foo-label-123, foo-error-123, foo-tab-123, foo-tab-panel-123, etc.

- How does existing tooling address these pain points (i.e. what "cow paths" are there that we could look at?)

1. Due to ads/SEO/framework/etc I might not control the ID, but I can access via a ref.
2. ref() in FASTElement acts like a local shortcut for this.querySelector(‘input’), and we can use that to grab the id when wiring up errors, etc.
2. uuids are a frequent need. Means building form parts in JS templates and looping inputs/options is easier than writing out the DOM.

- How does existing tooling *fail* to adequately address those pain points?

JS required or is easier.

- How are these pain points impacting authors' abilities to author usable, accessible web pages?

Needs (JS) templating.
Brittle if ID changes or wired wrong

- What do authors *like* about IDs?

The automatic JS variable reference is awesome.
The “this is one of a kind” expression is rad, but need a way express “this is semi-unique” or “in this section/scope of dom, this is unique”

- What design constraints should we consider for any potential solution?

Polyfillable, Declarative

- What is the user impact of breakages in element associations? Who is impacted? How can we minimise that risk?

A11y is a risk. Polyfill helps.

https://mastodon.social/@davatron5000/115049860001671621 (and earlier posts in the same thread)

---

> What are the specific pain points around using IDs?

Guaranteeing uniqueness on a page and keeping that uniqueness consistent across page renderings (e.g. if list elements have IDs, and an item gets inserted, do IDs remain consistent?)

> How does existing tooling *fail* to adequately address those pain points?

drawing attention to "you have more than one element with the same ID" in dev-tools

> What do authors *like* about IDs?

Can use as URL #anchors; allows for `<label for="…">`

https://mastodon.bsd.cafe/@gumnos/115050068997019695

---

The biggest pain point about IDs is the need for whole-page uniqueness, which conflicts with component-based templates, especially when there are repeated components.

Duplicate IDs break functionality (links, labels, ARIA associations) or rendering (SVG).

What is usually needed is a way to scope ID references to a specific iteration of a component template.

Shadow DOM in theory scopes IDs, but breaks a lot of uses of them, among other complications.

Component or template-based web page tooling generally addresses the need for unique IDs by inserting some sort of prefix to the ID when instantiating a template.

Generating unique IDs is a pain when combining output of multiple tools, using simple text-based server-side templates, or using the native HTML template element.

A solution should define a way to select a unique element (CSS selectors probably too broad), while supporting component-based content authoring (so, scoping).

https://front-end.social/@AmeliaBR/115050814509549309 (and previous post in the same thread)

---

[T]he key pain point is that component architectures are a very good pattern, but break IDs. Relative association paths are necessary: I'm a label and I associate to the next sibling input, for instance.

I'm not sure how often duplicate IDs actually cause issues for people, but the fact that they throw errors is enough that people have to generate UUIDs on the fly. If that were trivial, it'd be okay (not great), but it isn't (especially w/o a db)

 As for where and when IDs are useful, I'm not that sure. The fact that they work with associative attributes (for/ARIA etc.) is super useful, but for the reasons above feels suboptimal and becomes irritating. Any better mechanism would be preferable.

Otherwise, I don't think I'd ever use them. Their impact on specificity is enough reason to never use them on CSS, and it's rare that I have a high-level page element that still needs them, thanks to the HTML5 sectioning elems

https://indieweb.social/@theadhocracy/115050953488289313 (and previous post in the same thread)

---

- The only pain point I can think of is not really one honestly, it's the whole page uniqueness. That's a bit tricky to satisfy in some rare situations because the different elements linked by the IDREF are not in the same component.

But I can remember only a single time it made things a bit challenging to do when I was working on a menu and menuitem abstraction layer in Vue.

- Usually when I need to get an id I either use a random uuid in js or a framework provided helper when doing stuff from the backend.

Vue has useId that guarantees equality between frontend and backend and can be used to get a random opaque value to set as the id where needed.

- I never found myself in a case where a random uuid or a framework provided tool didn't solve the issue.

- For the times I had issues with making something accessible the issue always stemmed from a poor understanding of either the html attributes or aria attributes uses. Never from the IDREF itself.

For example which element should have which attribute (can't remember which one it was sarry)

- what I like about them? Meh... They're alright...

- what design constraints [...] ? Nothing comes to mind.
- What is the user impact [...] ? From what? Things work ok currently when you stop 5s to think about how to make something work with tools with a good DX like Vue or Svelte.

https://bsky.app/profile/ragnar-oock.bsky.social/post/3lwrwswxum226 (and subsequent posts)

---

* IDs don't work well with repeated content blocks, you have to uniquify them and refer to that unique'd name
* Dunno, don't use any

https://bsky.app/profile/tabatkins.com/post/3lwomsbywac2n

---

The only pain point I have is templates where I need to relate two elements together using an id (`for`, `aria-labelledby`, etc.), and the template is usually repeated in the page. Common fixes are expecting the template's calling code to pass a unique id, or to generate a random string.

Both workarounds are okay but are easy to forget, especially for less experienced devs.

I kinda wish that we could have non-unique ids and that features that take an IDREF did a local-first traversal to find the closest element with that id. Boom, 99% of use cases solved. 😅

(I figure it would be a performance problem and would break existing implementations and tooling, so probably not a practical solution. But it would automatically fix a bunch of currently live bugs caused by repeated templates with static id attribute values.)

https://bsky.app/profile/fvsch.com/post/3lwtambyhac2c (and subsequent posts)

---

One example I just stumbled upon: Random UUIDs not being ideal in static site generation as every page would be different in every build, making selective syncing of _actually_ changed pages to storage impossible.

https://bsky.app/profile/thomasjaggi.bsky.social/post/3lwsnc3rqss2t

---
Selectors for association feels like an obvious thing to do, but it is probably overly complex for these, especially when it is 99% 1∶1 relations.

https://yatil.social/@yatil/115049059201190417

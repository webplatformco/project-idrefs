# User Quotes around IDREF pain points

## State of HTML surveys

These are responses to pain points questions around different web platform areas.
For example, the the question around accessibility pain points was: _"What are your biggest pain points around web accessibility?"_

Responses around cross-root ARIA have been omitted, as this is a well-known pain point.

### 2023

#### Accessibility

> aria attributes requiring elements to have IDs to use them (like aria-controls, aria-labelledby), which is a pain in dynamic applications

> have to use tons of id's

> Generating IDs for just about every piece of content and keeping up with the IDs and letting the upper realm know about them.

> adding unique id for labels to work

> The platform doesn't help with basic needs like creating unique IDREFs.

#### Forms

> ids for everything for labels even though they're siblings

> assigning ids to labels

> Absolute ids for label input relations. Wish to have relative, form - scoped binding

> associating labels with form controls is awkward; in today's component world, i tend to avoid IDs, and wrapping inputs in labels is a poor solution

> oohohohohohohoho SCOPED IDs AND NAMES FOR FORMS. Right so check this out, what it you have multiple forms gathering similar data on a page, (this is especially prevalent with micro-frontends), you need a custom ID for each field, like a name with `performance.now()` or something tagged on the end. But it would be really nice if you could "scope" IDs and input names to individual forms so if can reference `:form-id>input#name` rather than just a global `#name` element

> That nesting inputs in labels have fallen out of favor and ids are wanted for nested inputs

> associating labels via unique IDs

> having to generate ids for datalist and label's for

> Creating IDs in hostile component-based frameworks, so I can match labels to inputs. I would love to have implicit for attributes when a label/input pair is wrapped in a parent container, something like `<div type="inputgroup"><label><input></div>`. Getting my developer community to care about generating unique IDs for every input is too hard; they aren't doing it and our code is inaccessible.

> Setting labels to the ids needed htmlFor

> non scoped IDs

> Manually connecting the label with the input via "for" and "ids". The other method of enclosing the input within the label tag is odd. Seems like it should be the opposite like enclosing the label tag within the input tag. Similar to how the details and summary tags work.

> Label/input association with unique IDs

> the ways to create input labels are weird. the wrapping does not always make sense to the structure and we don't always want to create ids just for the labels

> Overreliance on IDs

#### Interactivity

> scoping events and ids without shadow dom

> All the new features are using id attribute

#### Web Components

> Scoped ids. Some things require ids which must be unique to the document, but authors have know way of knowing what ifs may ultimately exist in the document when it is used.

> state of SVG url references and canvas filter ids inside shadow DOMs


### 2024

#### Accessibility

> having to use globally unique IDs to associate elements

> massive usage of id attributes prevent easy component creation


#### Forms

> Having to make unique input IDs is annoying, I wish there was a way to namespace ids. e.g. `idgroup="some-prefix">`

> id required in input

> naming things the same as their ID

#### Interactivity

> popover API can't easily be used without js or ids

> popovertarget to be any valid selector

#### Content

> SVG masks requiring unique IDs



### 2025

#### Accessbility

> Again uniqueness. E.g. errors like "The landmark must have a unique aria-label, aria-labelledby, or title to make landmarks distinguishable", means I can't use e.g. "aside" CMS content like blockquotes, meaning I instead endup with non-semantic HTML

> Generating unique-but-matching for-ID pairs in component-based dev frameworks, especially when the actual input is separated from its label and potentially seventeen levels deeper. (Dear God, I hate Angular.) It would be great if I could do something like id="foo[index]" and let the browser do the counting.

> Having to manage tons of unique IDs in components and template loops

> ids. Managing ids is painful. Wish I could use selectors instead.

> Coming up with strategies for unique id attributes

#### Forms

> Having to think about _everything_: set a name, set an id, make sure it has a `<label>`, make sure there's an autocomplete attribute, make sure the client-side validation is on par with the server-side validation, etc...

> labels use the ID, so you can't repeat similar forms and instead have to dynamically generate unique IDs for every form

> Label aria/id is strange. Use to be if you nested an input within a label that was good enough to establish a relationship but now we always need ids which seems like overkill.

> Aside from inputs nested inside a label, no way to use something other than IDs like scoped ids or name references to connect things.

> the fact that wrapping an input with `<label>` is not recommended for accessibility means ensuring unique ids per field, and complicates hand-made authoring and generating content both

> Unique IDs (in HTML in general) can be a pain, would like there to be another way.

> Having to choose unique ids with label for attributes. Give me scoped ids!

> settings ids and labels is very repetitive

> No relative addressing: all IDs global

> having to come up with unique ids

> IDs vs names vs fors

> requirement for ids

> Reliance on ids

#### Web Components

> Never quite clear that shadow dom ID's are constrained to the component instance - many IDE's/Linter's complain

#### Content

> Having to add unique IDs for a11y within components. I would prefer any other way to reference elements.

> I would like template-scoped element ids so I can precisely target sub-elements and fill content without having to use tag query or class query

> Scope id so they aren’t in a global namespace. Maybe there’s some way to add prefixes to child elements. e.g. `<div idprefix=“foo”>`

> lack of scoping for identifiers in HTML, every id is in document scope

#### Graphics

> IDs in inline SVGs needing to be unique on the page

#### Overall Platform Limitations

> Referencing via ids is painful and forces me into heavyweight solutions

> Html ul li counters as native performant unique ID generators would enable so much functionality, it's hard to think of all the use cases.

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

> `<label for=“id”>` (backward compatibility)
>
> `<label for-name=“name”>`
>
> `<label for-selector=“css-selector”>`
>
> Or is the last one, easier to recall when like this?
>
> `<label for-select=“css-selector”>`
>
> Or?
>
> `<label for-query=“css-selector”>`

> Yes, every time. Something that allows relative selecting.
>
> The ID model creates issues in the component model, forcing us to rely on some PRNG ID generator. With components, you cannot guarantee only one instance of the element.

> The for attribute accepting a querySelector would be handy.
>
> That way you could target `[name=foo]` or maybe even `& + *`
>
> When querySelector returns multiple fields, pick first one.

> Previous and next with some kind of CSS selector

> I haven't figured out all the details, but having options like `nearest(<css selector>)` and similar `nearestChild()` and `nearestParent()` would help.
>
> To be clear, I envision something like this:
>
> `<label for="nearest(my-wc-input)">`

> I wish we could write labels without `for`, or with for-nearest="true", to make the browser walk the tree in depth-first order looking for the nearest form control to associate

> What if you could  scope id's within the DOM? So you'd put an attribute on your component's outer element that it's a scope, and then things like for look for eloements with an ID within that scope? Then you're not executing a whole CSS query for every "for" attribute

> Similar to what others have said here already, some sort of query selector-like syntax would be suuuuper useful, especially for pointing to a sibling input.
>
> E.g. something that says "hey this label is for the input next to it" like:
>
> `<label for="+input">...</label>`
>
> `<input type="text" />`

> I agree and previous with minus? (Not valid css, but ok)
>
> `<input type=“checkbox” />`
>
> `<label for=“-input”>yes</label>`
>
> for="+next"
>
> and
>
> for="-previous”
>
> to select the adjacent form elements could be a way to declare this. So it could also apply to `<select>` and `<textarea>`

> I've been wanting this for ages. Pretty much everything on a web page is context dependent, so essentially if you have a way to define the context and then execute a selector pattern in that context, you could do almost anything.
>
> for="form:has(:scope) [name=field]"
>
> for=":scope + *"
>
> for="body #x"

> I would love to be able to refer to a CSS dashed ident of another object, and also to scope it to parts of the DOM as others already mentioned. Would be way more useful than what we have now with for and id 😁

> I know you probably meant something declarative in HTML, but I'd like a *property* instead: a `forElement` that, like `commandForElement`, can refer to an element without an id and even inside or outside a shadow root.

> Others have said everything already, but I'll add my name to the list wishing that `for` worked like `querySelector` and took any selector. Being able to hand roll `data-` attributes dynamically, grab the next/nth sibling of a specific type, even traversing the DOM.
>
> There's definitely scope for abuse and confusing logic, but I think the current association trips people up a lot anyway, particularly in component architectures where guaranteeing uniqueness on a page is hard-to-impossible
>
> Plus it feels possible to do this without a new attribute. Could allow a fallback for older browsers, and some kind of syntactic sugar to enhance with better selectors. Because `for` is a decent name.

> I'd love to have something similar to anchor positioning for this. Based on e.g. name but where I could also define a scope for that name.
>
> Although reusing 'name' might not be ideal. There might be use cases where it make sense to set multiple 'names' that have different scopes.
So a dedicated attribute might be better... Maybe 'target'?

> For me it's okay to call useId in my components. Some kind of selector would lead to debugging overhead imo.

#### [Mastodon Post](https://front-end.social/@bramus/115016389746283451)

> I haven't run into this a lot but it's happened a few times, namely in JS, where I wished to do something like `inputElement.for = labelElement` as a direct reference (kind of how like `inputElement.form` would give you the DOM reference). Directly in HTML, though, it's a little annoying to have to add an ID but if I'm writing it I don't mind so much.
>
> Though I could see how`<label forselector=":scope > :first-child"><input name="foo"></label>` could be interesting (but quickly complex).

> I wonder if we should just add a new `forElement` reflection property? Should be pretty trivial, though perhaps there's others that need that treatment too? Is the question of what should it return in the case of "auto" for where the label wraps the input.

> what's hard about generating an id? I can't imagine anything being easier (especially since it's such an established convention).

> Let’s say you have a component appearing 2 times on a page, each time with a different title:
>
> - `<schwitz-bloups title="Walala">`
> - `<schwitz-bloups title="Wololo">`
>
> In the SchwitzBloups implementation (pseudo-code):
>
```
<script>const uniqueId = uniqueId()</script>

<div aria-labelledby={uniqueId}>
  <h3 id="{uniqueId}" class="visually-hidden">{title}</h3>
</div>
```
>
> It would be simpler to write `aria-labelledby=":scope > h3.visually-hidden"` or `":scope > role(heading)"`.

> No, id works well and can be referenced by multiple things simultaneously.
>
> From an accessibility point of view, I don't think the use cases are dependably either the next element or an input within a parent (think `aria-describedby`, `aria-labelledby`, `aria-details`, `aria-activedescendant` etc.), but the need for id to be unique I do agree with.
>
> This makes me wonder if that restriction serves any purpose other than accessibility where a 1:1 relationship is needed?

> The ´name´ attribute maybe

> For referencing in JS, maybe something similar to ARIA Reflection, like `label.forElement = input`.
>
> But in a declarative context, given a `<label>` can only label one form control, referencing an ID seems to be logical.

>  i want "template instantiation" without shadow DOM.
>
> when you create an instance of the following template, it should have automatically managed associations that are guaranteed not to conflict with global IDs.
>
```
<template>
 <label for="foo">…</label>
 <input id="foo" />
</template>
```
>
> i don't want selectors or any new syntax.
>
> i think the difference between a template vs an instance is very much relevant here. what i'm talking about is a sort of transformation that simplifies the authoring experience by allowing the final DOM output to diverge.
>
> an `idscope` attribute would work completely differently and it would lead to duplicate IDs (which can break CSS selectors or custom parsers). i definitely see the appeal for simple one-off cases, but i'm not sure how practical it is.

> Yes. For naming things, I'd like to see more implicit naming by descendant elements, in addition to `<label>` and `<input>`, `<table>` and `<caption>`, `<figure>` and `<figcaption>`.
>
> But it would also be great to be able to reference any element, something like `querySelector()` in HTML attribute values. I'm imagining something like `aria-labelledby="query(> :where(h1, h2, h3))"`, `commandfor="query(~ dialog.settings)"`. First matching element "wins."
>
> I assume there could be performance concerns if each instance had to recalculate every time there's any DOM change. Maybe beginning the query value with `>` could scope it to descendants of that element.

> I'd like some form of derived ID based on a form control's name. I often need a couple of idref associations like for/id, aria-errormessage/id, etc. and the principal element in such contexts is typically a named form control. Currently, there are some extra steps involved in getting all the form elements on the page their right label/control association and to hook up error messages and possibly anchor links in a validation error case. Maybe this can be aided with some additional stuff.

> I have *not* thought this through, but just off the cuff, CSS queries would be sweeeet
>
> `<label fancyfor="+ input">`

> Yes, always. Not sometimes ☺️
>
> Some type of CSS selector that is relative to the `<label>` would be great.
>
> Like:
>
> :scope ~ input
>
> .widget:has(>:scope) input

#### [X Post](https://x.com/bramus/status/1955283107134709886)

> In case of name specifically we have for example the radio in which case multiple elements share same name.
What element would be focused when you click the label?
>
> But the key here is the way of identifying the element we want to address. For now we have one implicit way to establish relationship: put input element inside the label.
>
> But even then there are some ambiguity: we should refer first one if there are more than one inside?
>
>If this ambiguity and handling it by conventions is ok, we can for example pick up first match in some scope.
>
> Next html element (sibling) if no input inside the label would also be an option.
>
> This could be handy in some cases, but how complicated this kind of agreement could be?

> `<label querySelector=...` ?

> Any css selector maybe? The first match will be the one. Making it possible to limit the search within the scope will make it easy to create an elements with linking inside but without need of generating unique ids for each instance

> css selector comes to mind?

> Scoping. Either implicit (parent's DOM tree) or some explicit, through distinct attributes, or something like that. Global (entire-document) IDs were a mistake, and subscribing to a global scope should have been something special.

> Is “ref”/“reference” to obvious? 😁

> Yes, because using `id` makes me handle random id generation when generating inputs dynamically

> Have wished referencing an input element using it's name within the form. This would work for label's "for" but for attributes like aria-labelledby, it doesn't feel right

> I want a way to use UL LI counter values as unique IDs. Better yet, CSS counters - no extra markup.
>
> Game changer.

> simply wrap them in an parent and label should automatically associate itself with all its immediate sibling nodes.  helps scope the things, solves name or other identifier collision problem too. leaves the naming of the parent element as open question. just a thought.

> Blazor `@ref=""` ?

> This would be awesome for certain instances where forms are dynamically generated and you don’t want to come up with id strings. I’ve liked nesting controls within labels to solve this to an extent but doesn’t always work - I think name attr might work well enough?

> I guess a data attribute would work but that's state in most apps. The attribute has to be something that can never be changed even by JS!

> Using a `data-*` attribute.

> In this particular case, if it wasn't an issue for screen readers, nesting the input in `label` and keeping the association implicitly without the need for `for` attribute, descendant selector and using `querySelector()` with class could have been just fine.

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

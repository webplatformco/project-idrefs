# IDREF scoping

A concept for making it easier to manage IDREFs in documents that are composed from multiple fragments/components

## State of this document

Exploring/brainstorming a solution, as it pertains to a few particular painful aspects of the problem as it was initially introduced.

## Narrower definition of the problem

Modern HTML documents have two common qualities to them:
1. They are composed of multiple fragments/components, some of them imported from elsewhere.
1. For the purpose of elements referencing each other, the document is one global monolith, where globally unique IDs are the only referencing mechanism.

This is somewhat revised in shadow DOM, where IDs are only global within a shadow root.
However, shadow DOM is a heavy-handed solution for some solutions, e.g., when the styles and querying needs to work like one document but not cross-element references.

A relatively common example is SVG. Inline SVGs use IDs for internal references, and also tend to be imported from various sources.
However, this problem is not SVG-specific. Embedding HTML snippets inside a bigger HTML document can cause the same issues.

There are other pain points listed in the [explainer](https://github.com/WICG/idrefs/blob/main/README.md),
however this solution focuses specifically on documents that are composed of multiple fragments that come from different sources,
and the friction of maintaining the structural integrity of the fragment's references,
without making those entirely "alien" to the document in other ways.

## Previously proposed solutions

A solution discussed previously was using some subset of DOM selectors (aka CSS selectors), with a relative scoping mechanism, to express these references.
However, this type of solution seems complex, both in terms of the aforementioned scoping mechanism and in terms of implementing it efficiently within browser engines,
specifically around invalidation tracking.
Moreover, selectors tend to become complex, and the web development community is not in consensus about whether it is a concept that should be extended beyond its current scope of styling and imperative querying.

## Prior art as a source of inspiration

A common way to mitigate this problem in the React world is the `useId()` hook.
This hook generates a globally unique ID in the scope of a React component, and then propogates that generated ID to all nested parties requiring it.

The interesting aspect of `useId` is that the author of the component is in control of propogating it, and it doesn't leak to the outside context unless explicitly exported in some means.

## Constraints on the solution
Solutions in this space should:
- provide a good match for the composability/integrity problem
- still allow global ID references, e.g. when some relationships are explicitly cross-component or for document-level references such as `#fragment` URLs.
- Keep it simple with respect to changes in a11y engines, who already suffer from underfunding and stability issues.
- Allow for an efficiently implemented algorithm

## The `idscope` idea
The `idscope` attribute (name bikesheddable etc), is a boolean global attribute that can go on any HTML/SVG/MathML element.
When used, it changes the order in which internal IDREFs are resolved.
This only has effect when there is an IDREF conflict.
Instead of resolving the IDREF in document order like today, the IDREF is resolved by nearest-idscope-ancestor first, and only then in document order.

For example, this is a simple illustration of the difference:

```html
<form id="form1">
   <label for="enabled-cb">Enabled</label>
   <input type=checkbox id="enabled-cb">
</form>

<form id="form2">
   <label for="enabled-cb">Enabled</label>
   <input type=checkbox id="enabled-cb">
</form>

<form id="form3" idscope>
   <label for="enabled-cb">Enabled</label>
   <input type=checkbox id="enabled-cb">
</form>
```

In both `form1` and `form2`, the label would reference the checkbox with ID `enabled-cb` from `form1`. That is because it is the first element with that ID, in document order.
However, `form3`, which has an `idscope` attribute, the label would reference the checkbox right after it, because it is the first `enabled-cb` element in *scope-first* order.

## Some notes/questions
* Does this sufficiently help with the composition/integrity issue?
* This does require an algorithm that is a bit more involved than global IDs. However, the worst case complexity of this algorithm (if not using any kind of caching) is derived from the amount of conflicts and depth of `idscope` nesting.
* For this to apply to SVG, it would need to work for SVG hash fragments and not only for regular IDREFs.
* Would this *encourage* people to make their IDs less unique, even when unnecessary? Is that a problem?












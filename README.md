#simple-css
version 0.1.0

## What is it?

An opinionated set of guidelines for writing organized & scaleable CSS.

## What it is not

A replacement for tools for writing CSS like LESS or SASS.

It is more comparable to other philosophies on how to write `CSS`, like `OOCSS` or `SMACSS`. While not entirely orthogonal to either of these philosophies, there are some differences. Of the two, it more closely aligns with OOCSS.

# The Principles

Simple CSS can be summarized in 5 principles. They'll be listed here, then elaborated on in the rest of this document.

1. Use a preprocessor
2. Scope everything
3. Make class names nouns or adjectives
4. Use short names
5. There can be exceptions

# Details

## Use a preprocessor

Preprocessors have a lot to offer you in terms of functionality when writing `CSS`, but I won't elaborate on all of their merits here. In addition to all of those gains, using preprocessors makes following the second principle, keeping things scoped, incredibly simple to follow. More on that below.

## Scope everything

Two problems that any `CSS` philosophy attempts to solve are avoiding collisions between styling and building scaleable projects. With `Simple CSS`, these issues are both solved for with scoping. The idea behind scoping is simple: avoid styling elements globally when it doesn't make sense to. Instead, use descendant and child selectors to style your elements.

For instance, if you have a menu with links that are different than the rest of your page, your `SASS` or `LESS` file may look like the following:

```
// Start of file
nav {
  
  a {}      // nav-specific links
  span {}   // nav-specific span
  // ...the rest of your styling

}
// End of file
```

As the above example shows, using preprocessors makes this incredibly simple to follow. Each individual `LESS` or `SASS` file can be used to represent a different scope.

## Nouns and Adjectives

Use two types of `CSS` names: nouns and adjectives. Use noun classes to make new scopes and reusable components. For instance,

```
.slider-bar {
  h1 {}
  a {}
}
```

In this case, we use a noun, `slider-bar`, as a class name to create our new scope. This can now also be used as a reusable component.

Use adjectives to differentiate between elements within a scope. For instance,

```
.data-bar {
  .left {}
  .right {}
}
```

```
.name-tags {
  .left {}
  .right {}
}
```

In these two examples, we use adjectives within the scope to target specific elements. Though the same class names are used, `left` and `right`, there is no collision because they are scoped.

Adjectives can be stateful, such as: `active` `disabled` `hover`

They can also refer to position and order: `one` `two` `three` `left` `right` `top`

Styling unscoped adjectives is discouraged. Instead, attaching adjectives to noun classes or elements is encouraged. See the examples below

**Discouraged:**

```
.active { border: 1px solid #eee; }
```

**Encouraged:**

```
nav {
  a.active { 1px solid #eee; }
}
```

This allows you to use adjectives without fear of collision.

## Use short names

A `CSS` philosophy that has been gaining attention lately is `SMACSS`. There are many benefits to using `SMACSS`, which is, no doubt, why it is becoming more widespread. But SMACSS promotes writing class names that are unintuitive and very verbose. I believe that following the rules of Simple CSS allows you to use short class names with all of the gains of `SMACSS`.

**An example of SMACSS verbosity** (from the excellent plugin headroom.js)

```
<header class="headroom headroom--unpinned">
```

**Simple CSS**

```
<header class="headroom unpinned">
```

When the rules of Simple CSS are followed the second example is no more likely to cause collisions. But the class names used are shorter and easier to digest.

## Exceptions

Simple CSS outlines guidelines, not strict rules. Always do what you believe makes the most sense on a per-project, and even per-element, basis.



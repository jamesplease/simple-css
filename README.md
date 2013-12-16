#simple-css
version 0.1.2

## What is it?

An opinionated set of guidelines for writing organized & scaleable `CSS`.

## What it is not

A replacement for tools for writing `CSS` like `LESS` or `SASS`.

It is more comparable to other philosophies on how to write `CSS`, like `OOCSS` or `SMACSS`. While not entirely orthogonal to either of these philosophies, there are some differences. Of the two, it more closely aligns with `OOCSS`.

# The Principles

`Simple CSS` can be summarized in 5 principles. They'll be listed here, then elaborated on in the rest of this document.

1. Use a preprocessor
2. Scope all that you can
3. Make class names nouns or adjectives
4. Use short names
5. Exceptions are okay

# Details

## 1. Use a preprocessor

Preprocessors have a lot to offer you in terms of functionality when writing `CSS`, but it's beyond the scope of this document to elaborate on all of their merits here. There are two specific reasons I will describe that explain their placement as the first principle of `Simple CSS`: the first being their ability to improve organization. `CSS` philosophies that emphasis modular styling, like `Simple CSS`, benefit immensely from being able to easily break up your scripts into multiple files during the development phase. The second reason these are mentioned first is that preprocessors take all of the effort out of following the second principle, which is explained below.

## 2. Scope all that you can

Two problems that any `CSS` philosophy attempts to solve are avoiding collisions between styling and building scaleable projects. With `Simple CSS`, these issues are both solved for with scoping. The idea behind scoping is simple: avoid styling elements globally when it doesn't make sense to. Instead, use descendant and child selectors to style your elements.

For instance, if you have a menu with links that are different than the rest of your page, your `SASS` or `LESS` file may look like the following:

```
// Contents of nav.js
nav {
  
  a {}      // nav-specific links
  span {}   // nav-specific span
  ...       //the rest of your styling

}
```

As the above example shows, using preprocessors makes this a painless process. Each individual `LESS` or `SASS` file can be used to represent a different scope.

## 3. Nouns and Adjectives

Use two types of `CSS` names: nouns and adjectives, but never mix the two. Use noun classes to make new scopes and reusable components. For instance,

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

Styling unscoped adjectives is discouraged. Instead, attaching adjectives to noun classes or elements is encouraged. See the examples below.

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

## 4. Use short names

Keep class and ID names short and simple. Ideally only a single word, if possible. When phrases or compound words must be used, separate words with hyphens and never capitalize. Short names result in cleaner markup that's easier for humans to read.

## 5. Exceptions are okay

The last thing to keep in mind is that Simple CSS is not a rigid set of rules, by any means. Rather, it should be viewed as suggestions that are a good idea to follow when you can. There might come a time in your project to break from the rules of Simple CSS to do what works best for the situation. Go for it. The last principle of Simple CSS is to always do what makes sense on a per-project, and even per-element, basis.

# Trade-Offs, Considerations, and Comparisons

If you're excited at the thought of incorporating `Simple CSS` into your project, allow me to share with you instances where it might not be the best idea.

Environments where you can't be sure that all of the `CSS` was written following `Simple CSS` are more likely to lead to naming (and therefore styling) collisions that competing philosophies. Example environments include incorporating Simple CSS into an already-existing application, as well as open source projects that include CSS class names. Attaching an `.active` class on any element in such cases as these might be a bad idea, as they are so commonly used to style elements.

A `CSS` philosophy that has been gaining much attention lately is `SMACSS`. There are many benefits to using `SMACSS`, which is, no doubt, why it is becoming more widespread. But the thing that differentiates `SMACSS` from other philosophies of writing stylesheets are the unintuitive and very verbose class names. Let's look at an example from the excellent plugin [headroom.js](http://wicky.nillia.ms/headroom.js/):

```
<header class="headroom headroom--unpinned">
```

The practice of appending the base class name to every following class name quickly becomes unwieldy and ugly. But this convention has great utility in that the issue of collisions is, for the most part, completely eliminated.

With that said, the future of the web looks good for more minimalist CSS, like `Simple CSS`. [Scoped stylesheets](http://updates.html5rocks.com/2012/03/A-New-Experimental-Feature-style-scoped) and [web components](http://css-tricks.com/modular-future-web-components/) are slowly becoming available to more and more users of the web. In these environments, there's no fear of collisions, and `Simple CSS` really shines.

But don't let all of that discourage you. `Simple CSS` is a great solution in environments where you have greater control over your code's styling.

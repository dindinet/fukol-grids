# ![Fukol Grid System](logo.png)

**Fukol&trade;** is a lightweight, breakpoint free, completely responsive, element query driven\*, progressive enhancement based CSS grid framework. It exists in this `README.md` file, in the section titled **The CSS** (below). It is **264 bytes** in size unminified and, when you minify it, it fits in a tweet:

<img src="tweet.png" alt="Fukol minified and in a tweet" width="450" />

Just edit the lines marked 'edit me!' to your requirements and write an HTML structure like the one illustrated in the section titled **The HTML** (also below).

(\* Not really, but kind of. See **3**, below.)

## The CSS

```css
.fukol {
  overflow: hidden; /* 7 */
}

.fukol-grid {
  display: flex; /* 1 */
  flex-flow: row wrap; /* 2 */
  margin: -0.5em; /* 6 (edit me!) */
}

.fukol-grid > * {
  flex-basis: 10em; /* 3 (edit me!) */
  flex-grow: 1; /* 4 */
  margin: 0.5em; /* 5 (edit me!) */
}
```

1. **Fukol&trade;** is a Flexbox based grid system. Even Opera Mini supports Flexbox. Older user agents that don't support Flexbox ignore the `display: flex` declaration, degrading to a single column layout. No harm done.
2. This line determines how items are handled. The important part is `wrap` which means items will start a new row if there's not enough room on the current one.
3. This is the 'element query' part. Instead of setting an arbitrary number of columns and using breakpoints, we decide how wide we would like each item to be. How many items you get per row depends on the width of the container.
4. This declaration means that items will 'flex' to use up the available space. If an item wraps onto a new row, it will take up 100% of that row's space. If you add another item to that new row and the overall width is more than twice your `flex-basis`, the row will be divided into two. If not, another new row is created.
5. This is for gutters. A `0.5em` margin here means gutters of `1em` (the margins double up).
6. This should always be a negative version of **5**. It compensates for the margins created by the items. It makes sure the outside of the `.fukol-grid` container remains flush horizontally and no additional margin is added to the vertical flow.
7. Having used negative margins (**6**) on `.fukol-grid`, a container element is provided for the application of positive margins where desired. The `overflow: hidden` declaration suppresses horizontal scrollbars caused by negative margins in some browsers and circumstances.

## The HTML

```html
<div class="fukol">
  <ul class="fukol-grid">
    <li><!-- grid cell/item/child/whatever --></li>
    <li><!-- grid cell/item/child/whatever --></li>
    <li><!-- grid cell/item/child/whatever --></li>
    <li><!-- grid cell/item/child/whatever --></li>
    <li><!-- grid cell/item/child/whatever --></li>
    <li><!-- grid cell/item/child/whatever --></li>
    <li><!-- grid cell/item/child/whatever --></li>
    <li><!-- grid cell/item/child/whatever --></li>
  </ul>
</div>
```

## Demo

![Grid items as boxes, collapsing into fewer columns at smaller viewports automatically](fukol-demo.gif)

## Items with different widths

Sometimes you want certain items to be narrower or wider. You can target these using `:nth-child`. For example, you may want to make the first item take up the full width. In which case:

```css
.fukol-grid > *:nth-child(1) {
  flex-basis: 100%;
}
```

Or maybe you want the fifth item to always be approximately twice the size of a regular item (where space permits). If the regular `flex-basis` is `10em`, then&hellip;

```css
.fukol-grid > *:nth-child(5) {
  flex-basis: 20em;
}
```

Don't worry, flexbox will make sure there aren't any gaps.

## RTL Grids

Flexbox supports `rtl` already. Just add `dir="rtl"` to the `.fukol-grid` element and the flex direction will automatically be reversed.

## FAQs

1. *How do I install Fukol&trade;? Is it on bower/npm?* You install it by copy/pasting it from this `README.md` file. See the **The CSS** section above.
2. *Is Fukol&trade; the answer to all my grid system hopes and dreams?* No. Fukol&trade; is just a servicable solution, written with very little code.
3. *Why are there a load of old dicks in the Fukol&trade; logo? Are you some sort of misogynist?* No, fuck the patriarchy. There are a load of old dicks in Fukol&trade;'s logo because grid systems are a load of old dicks.
4. *Is there a Sass version?* Yes: inside your head.

## That's it

That's it.

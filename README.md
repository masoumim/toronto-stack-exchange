# Toronto Stack Exchange
This project is a simple static and responsive website for the Toronto Stack Exchange Meetup group.

Link: https://masoumim.github.io/toronto-stack-exchange

# Project technical stack:

**Language:** HTML 5

**Styling / Front-end:** CSS Grid + CSS Flexbox

# Project info:
The main goal of this project was to demonstrate and utilize the CSS Grid Layout as a styling and layout model. CSS Grid, while being a powerful layout tool, has some limitations in regards to responsive web design. Methods for overcoming this limitation are discussed in the next section.

In addition to CSS Grid, I also utilized Media Queries along with Flexbox's responsive elements to create a website that is viewable on a variety of devices and screen sizes. In addition, I used Google Chrome's "Device Mode" which lets developers see how their project will render on a variety of different mobile devices.

# CSS Grid
As mentioned, CSS Grid is very good for quickly and intuitively laying out page elements. However, out of the box, CSS Grid only has a single method for dynamically resizing columns. The minmax() method allows for the setting of minimum and maximum column sizes which will size dynamically as the size of the browser window / viewport is changed.

The issue is that columns are only able to resize horizontally to their minimum and maximum size value. This means that columns do not wrap, readjust or stack on top of each other when the browser window size reaches the minimum of the minmax() method. Due to this issue, there are limitations on creating a truly responsive web design.

A novel solution is to make use of the `grid-template-columns` property. Instead of creating fixed columns and rows for a page using CSS Grid's various column and row properties, all columns will be added dynamically using a combination of `grid-template-columns`, the `repeat()` method, the `auto-fit` property and finally, the `minmax()` method.

In an element that has it's CSS `display` property set to `grid`, we use the `grid-template-columns` property as follows:

`grid-template-columns: repeat(auto-fit, minmax(min, max));`

What the above line does is create a column for each child element inside the parent grid element. For example, for the following HTML, 3 columns would be created:

`<div class="my-div">`
`<p> I am column 1 </p>`
`<p> I am column 2 </p>`
`<p> I am column 3 </p>`
`</div>`

If the `grid-template-columns` property for the div above was set as follows: `grid-template-columns: repeat(auto-fit, minmax(5rem, 1fr));`, then 3 columns of size `5rem` would be equally spaced in the row. The `1fr` is what gives each column an equal amount of spacing in the row.

While this approach works well for simple layouts, we may want to have two columns and control how close / far they are from each other. This can't be accomplished using the `1fr` measurement as this will space the two elements equally apart using the width of the entire row.

To have finer control over how close / far columns are from each other, the `grid-template-columns` property can be adjusted like so: 

`grid-template-columns: repeat(auto-fit, minmax(1rem, 30rem));`

In the above line, we are creating columns that are a minimum of `1rem` and a maximum of `30rem`. If we have two child elements in the parent grid element, we can adjust how close / far the elements are from each other by increasing or decreasing the maximum value in `minmax()`.

By using this approach combined with Media Queries for finer control of elements at different browser window / viewport sizes, a fully **responsive** layout can be achieved.

# References
I used the following 2 articles which go in to more detail on this particular use of `grid-template-columns` to create responsive layouts:

1. [Look Ma, No Media Queries! Responsive Layouts Using CSS Grid](https://css-tricks.com/look-ma-no-media-queries-responsive-layouts-using-css-grid/)

2. [Auto-Sizing Columns in CSS Grid: `auto-fill` vs `auto-fit`](https://css-tricks.com/auto-sizing-columns-css-grid-auto-fill-vs-auto-fit/)






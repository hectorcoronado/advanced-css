# Flexbox
----------------------------

#### Module in CSS3 that makes it easy to align elements to one another, in different directions and orders

#### Main idea:
- give container ability to expand and shrink elements to best use available space

#### Replaces float layouts, using less, more readable code

## General principles for usage:

##### Flex container:
The element that we use `display: flex` on (or `sisplay: flex-inline`)

Once set, all children elements in that container will be `flex items`

The container's elements are then arranged along 2 axes, in `display: flex`, they are:
1. *Main axis*: horizontal x-axis
2. *Cross axis*: vertical y-axis

## Container properties (first value is default):

1. flex-direction:
    - describes how flex items should display, in which order
    - *row* | row-reverse | column | column-reverse
2. flex-wrap:
    - defines if flex items should fall into new line if there's not enough space
    - *nowrap* | wrap | wrap-reverse
3. justify-content:
    - defines how items will align *along the main axis*
    - *flex-start* | flex-end | center | space-between | space-around | space-evenly
    - the values above will do the following (in `flex-direction: row`)
        - `space-between` will add equal space *between* each flex-item, but no additional space to the left of the first or right of the last items (in a `flex-direction: row` setting)
        - `space-around` will add space *around* each on the left and right sides of each flex-item, including to the left of the first and right of the last item
            - the space between each item will be twice the width of the space to the left of the first and right of the last items
        - `space-evenly` will add equal space to the left and right sides of every flex-item
        - `center` adds no space, and centers the flex-items horizontally
        - `flex-start` aligns all items to the left
        - `flex-end` aligns all items to the right
4. align-items:
    - defines how items will align *along the cross axis*
    - *stretch* | center | start | end | baseline
    - the values above will do the following (in `flex-direction: row`)
        - `stretch` will increase default height of all flex-items to height of "tallest" one
        - `center` will align all flex items to the center of the *cross axis*
        - `start` will align all flex items to the top of the cross axis
        - `end` will align all flex items to the bottom of the cross axis
        - `baseline` will align *the text* of the flex items along a line corresponding to the bottom of the rendered text
5. align-content:
    - only applies when there is more than one row of content
    - controls how the **rows** are aligned *along the cross axis* if there is any empty space
    - *flex-start* | flex-end | center | space-between | space-around
    - the logic of the property's values are the same as those for `justify-content`

## Item properties (first value is default):

1. align-self:
    - similar to `align-items` except used for individual items
    - can be used to override the container's `align-items` if e.g. we want all items to center-align, except one in the bottom
    - *auto* | stretch | flex-start | flex-end | center | baseline
2. order:
    - defines the order in which one specific flex item should render
    - *0* | <integer>
    - by default, items are arranged in the order they appear in markup, with a default value of `order: 0`
        - if we want e.g. the 4th item to display before the 1st, we set the 4th's order property to less than 0: `order: -1`
3. flex-grow:
    - defines how much individual flex-item can grow in its row/column
    - *0* | <integer>
    - a trick to get an element to render as wide as possible within its container is to set `flex-grow: 1` (shorthand: `flex: 1`)
    - this setting is relative to the setting of other flex-items' `flex-grow` values, such that if one element has it set to 2, and the rest to 1, then the former will occupy twice as much space as the others
4. flex-shrink:
    - defines how much individual flex-item can shrink
    - *1* | <integer>
5. flex-basis:
    - defines its base width; generally this setting is used in lieu of the `width` property
    - *auto* | <length>
    - it's generally good practice to use a % value, such that an item with e.g. `flex-basis: 20%` will occupy 20% of the space available in the container
6. **flex**
    - this is the property that ought to be used to set the above three like so:
    - `flex: 0 1 auto`
        - where the 1st setting corresponds to `flex-grow`, 2nd to `flex-shrink`, 3rd `flex-basis`
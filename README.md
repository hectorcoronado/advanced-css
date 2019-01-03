# To run a dev-server:

`$ cd Natours && npm run live-server`

# CSS properties and values explanations:

## `box-sizing`

- by default in the CSS box model, the width and height assigned to an element is applied only to the element's content box.
- if the element has a border or padding, it's then added to the width and height;
- this meands that when width and height are set, one must adjust the value to account for any border or padding values
- `box-sizing: border-box` property tells the browser to account for any border and padding in the values specified for an element's width and height.
    - if an element's widht is set to 100px, that 100px will include any border or padding added

## `position: relative` & `position: absolute`

- if we're using these properties/values, and using `absolute` to position an element via e.g. `top: 40px`, `left: 40px`, etc, how are these values calculated?
- they're calculated by the parent element with the `relative` value
    - the parent element becomes the *origin*, the place from where `top` & `left` values begin, so to speak.
- on the other hand, the `transform: translate(x, y)` value/property is calculated in relation to the element itself, not the parent. So we can do something like the following to center an element:

```html
<div class='parent'>
    <p class='centered-text'>i'm centered</p>
</div>
```

```css
.parent {
    position: relative;
}

.centered-text {
    position: absolute;
    top: 50%; /* calculated relative to `.parent` */
    left: 50%; /* calculated relative to `.parent` */
    transform: translate(50%, 50%); /* calculated relative to self */
}
```

## `@keyframes` -- can be used to animate the `opacity` and `transform` properties (that's what browsers are optimized for)

- use in conjunction with percentages, to signify what kind of animation you want to happen and over what timespan -- to clarify, if you set e.g. 

```css
@keyframes nameOfAnimation {
    0% {
        opacity: 0; /* element is completely transparent at start of animation */
        transform: translateX(-100px); /* element is 100px to the left of its normal position at start of animation  */
    }
    100% {
        opacity: 1; /* element is completely opaque at end of animation */
        transform: translate(0); /* element is at its normal position at end of animation */
    }
}
```

## to use animations:

- you *must* use two properties in a specific element:
    - **animation-name**
    - **animation-duration**

```css
.animated-class {
    animation-name: nameOfAnimation;
    animation-duration: 1s;
}
```

- there are several optional properties that may be declared; these are some of the most common/useful:
    - `animation-timing-function`: its value specifies how `animation-duration` value should progress over each cycle
    - `animation-delay`: start animation after interval declared in its value
    - `animation-iteration-count`: animation will run number of times declared in its value

- and we may also use the `animation` shorthand to declare all these values **in this order** at once:
    
    1. animation-name
    2. animation-duration
    3. animation-timing-function
    4. animation-delay
    5. animation-iteration-count
    6. animation-direction
    7. animation-fill-mode
    8. animation-play-state

## `:link` pseudo-element
    - can be used on an `<a>` anchor element to make it behave as a link

## `box-shadow`
specify a single box-shadow using:

- Two, three, or four <length> values.
    - If only two values are given, they are interpreted as <offset-x><offset-y> values.
    - If a third value is given, it is interpreted as a <blur-radius>.
    - If a fourth value is given, it is interpreted as a <spread-radius>.
- Optionally, the inset keyword.
- Optionally, a <color> value.
- To specify multiple shadows, provide a comma-separated list of shadows.

# Visual Formatting Model:
an algorithm that calculates boxes & determines the layout of these boxes for each element in the render tree, in order to determine the final layout of the page. It does so by taking into account:

- dimensions of boxes: the box model
    - `margin`
    - `border`
    - `padding`
    - content (`width` & `height`)
        - with `box-sizing: content-box`:
            - total width of an element: right border + right padding + specified width + left padding + left border
            - total height of an element: top border + top padding + specified height + bottom padding + bottom border
                - this means that for an element:
                    ```html
                    <p class="content-box-text">text here<p>
                    ```
                    
                    ```css
                    .content-box-text {
                        border: 1px solid black;
                        padding: 20px 10px;
                        width: 100px;
                        height: 50px;
                    }
                    ```
                    - the actual width will be 122px (1 + 10 + 100 + 10 + 1)
                    - and the height will be 92px (1 + 20 + 50 + 20 + 1)
        - with `box-sizing: border-box`:
            - total width of an element: specified width
            - total height of an element: specified height
            - `border`s and `padding`s will be added **within** the content box's width and height settings
    - ...and there's also the `fill-area`: it includes all of the above **excecpt** `margin` and is the area that gets filled in with `background-color` &/or `background-image`
- box type: inline, block, inline-block
- positioning scheme: floats & positioning
- stacking contexts
- other elements in the render tree
- viewport size, dimensions of images, etc.

# Box Types:

1. Block-level boxes:

- elements formatted visually as blocks
- 100% of parent's width
- vertically, one after another
- box model applies as shown
    - `display: block`
    - `display: flex`
    - `display: list-item`
    - `display: table`

2. Inline boxes:

- content is distributed in lines
- occupies only content's space
- no line-breaks
- no heights or widths
- paddings and margins only horizontal (left and right)
    - `display: inline`

3. Inline-block boxes:

- a mix of block and inline
- occupies only content's space
- no line breaks
- box-model applies as shown
    - `display: inline-block`

# Positioning Schemes: Normal flow, Absolute Positioning, & Floats
*positioning does not cascade*

1. Normal flow:

- *not* floated
- *not* absolutely positioned
- elements laid out according to their source order
    - `position: relative`

2. Floats:

- element is removed from the normal flow
- text and inline elements will wrap around the floated element
- the container **will not adjust its height** to the element
    - `float: left`
    - `float: right`

3. Absolute positioning:

- element is removed from the normal flow
- no impact on surrounding content or elements
- we use `top`, `bottom`, `left`, and `right` to offset the element from its `relative`ly positioned container
    - example:
    ```css
    .parent {
        position: relative;
    }

    .child {
        position: absolute;
        top: 50%;
        left: 50%;
        transform: translateX(-50%); /* this centers the element horizontally */
    }
    ```
4. Fixed:

- this type of positioning is fairly rare, but has its uses
- a fixed position element is positioned relative to the *viewport*
- it's useful for e.g. a navbar that should render at the top of the page and stay there as a user scrolls down

# Maintaining image aspect-ratios:

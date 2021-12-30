# Responsive Web Design

https://www.freecodecamp.org/learn/responsive-web-design/

## Basic HTML and HTML5

- At the top of your document, you need to tell the browser which version of HTML your page is using. HTML is an evolving language, and is updated regularly. Most major browsers support the latest specification, which is HTML5. However, older web pages may use previous versions of the language.
  
  You tell the browser this information by adding the `<!DOCTYPE ...>` tag on the first line, where the `...` part is the version of HTML. For HTML5, you use `<!DOCTYPE html>`.
  
  The `!` and uppercase `DOCTYPE` is important, especially for older browsers. The `html` is not case sensitive.
  
  Next, the rest of your HTML code needs to be wrapped in `html` tags. The opening `<html>` goes directly below the `<!DOCTYPE html>` line, and the closing `</html>` goes at the end of the page.
  
  Here's an example of the page structure. Your HTML code would go in the space between the two `html` tags.

```html
<!DOCTYPE html>
<html>

</html>
```

- Metadata elements, such as `link`, `meta`, `title`, and `style`, typically go inside the `head` element.

```html
<!DOCTYPE html>
<html>
  <head>
    <meta />
  </head>
  <body>
    <div>
    </div>
  </body>
</html>
```

- Comments in HTML start with `<!--` and end with a `-->`

- HTML5 introduces more descriptive HTML tags. These include `main`, `header`, `footer`, `nav`, `video`, `article`, `section` and others. These tags give a descriptive structure to your HTML, make your HTML easier to read, and help with Search Engine Optimization (SEO) and accessibility. The `main` HTML5 tag helps search engines and other developers find the main content of your page.

```html
<img src="https://www.f.com/image.jpg" alt="Acat.">
```

```html
<a href="https://www.f.org">this links to f.org</a>
```

- To create an internal link, you assign a link's `href` attribute to a hash symbol `#` plus the value of the `id` attribute for the element that you want to internally link to, usually further down the page. You then need to add the same `id` attribute to the element you are linking to. An `id` is an attribute that uniquely describes an element.

```html
<a href="#contacts-header">Contacts</a>
...
<h2 id="contacts-header">Contacts</h2>
```

```html
<ul>
  <li>milk</li>
  <li>cheese</li>
</ul>
```

```html
<ol>
  <li>Garfield</li>
  <li>Sylvester</li>
</ol>
```

```html
<form action="/url-where-you-want-to-submit-form-data">
  <input type="text" placeholder="cat photo URL" required>
  <button type="submit">Submit</button>
// maybe input better
</form>
```

- Radio buttons are a type of `input`.

Each of your radio buttons can be nested within its own `label` element. By wrapping an `input` element inside of a `label` element it will automatically associate the radio button input with the label element surrounding it.

All related radio buttons should have the same `name` attribute to create a radio button group. 

```html
<label> 
  <input type="radio" name="indoor-outdoor">Indoor 
</label>
```

It is considered best practice to set a `for` attribute on the `label` element, with a value that matches the value of the `id` attribute of the `input` element. This allows assistive technologies to create a linked relationship between the label and the related `input` element. For example:

```html
<input id="indoor" type="radio" name="indoor-outdoor">
<label for="indoor">Indoor</label>
```

Also:

```html
<label for="indoor">
  <input id="indoor" value="indoor" type="radio" name="indoor-outdoor">Indoor
</label>
<label for="outdoor">
  <input id="outdoor" value="outdoor" type="radio" name="indoor-outdoor">Outdoor
</label>
```

When the user submits the form with the `indoor` option selected, the form data will include the line: `indoor-outdoor=indoor`. This is from the `name` and `value` attributes of the "indoor" input.

- Checkbox:

```html
<label for="loving"><input id="loving" type="checkbox" name="personality"> Loving</label>
```

- checked: default checked selection.

## Basic CSS

- inline

```html
<h2 style="color: blue;">CatPhotoApp</h2>
```

Note that it is a good practice to end inline `style` declarations with a `;` .

- At the top of your code, create a `style` block. Inside that style block, you can create a CSS selector for all `h2` elements. For example, if you wanted all `h2` elements to be red, you would add a style rule that looks like this:

```html
<style>
  h2 {
    color: red;
  }
</style>
```

- class declaration

```html
<style>
  .blue-text {
    color: blue;
    font-size: 30px;
    font-wight: 200;
    font-family: sans-serif;
  }
</style>
```

You can see that we've created a CSS class called `blue-text` within the `<style>` tag. You can apply a class to an HTML element like this: `<h2 class="blue-text">CatPhotoApp</h2>`. Note that in your CSS `style` element, class names start with a period. In your HTML elements' class attribute, the class name does not include the period.

- [Google Fonts](https://fonts.google.com/) is a free library of web fonts that you can use in your CSS by referencing the font's URL. To do this, copy the following code snippet and paste it into the top of your code editor (before the opening `style` element):

```html
<link href="https://fonts.googleapis.com/css?family=Lobster" rel="stylesheet" type="text/css">
```

Now you can use the `Lobster` font in your CSS by using `Lobster` as the FAMILY_NAME as in the following example:

```css
font-family: FAMILY_NAME, GENERIC_NAME;
font-family: Helvetica, sans-serif;
```

The GENERIC_NAME is optional, and is a fallback font in case the other specified font is not available. There are several default fonts that are available in all browsers. These generic font families include `monospace`, `serif` and `sans-serif`.

Family names are case-sensitive and need to be wrapped in quotes if there is a space in the name. For example, you need quotes to use the `"Open Sans"` font, but not to use the `Lobster` font.

- size your img

```html
<style>
  .larger-image {
    width: 500px;
  }
</style>
```

- CSS borders have properties like `style`, `color` and `width`.

```html
<style>
  .thin-red-border {
    border-color: red;
    border-width: 5px;
    border-style: solid;
    border-radius: 10px;     # rounded corners // =50% (circle)
  }
</style>
```

- Remember that you can apply multiple classes to an element using its `class` attribute, by separating each class name with a space. For example:

```html
<img class="class1 class2">
```

- how you can take your element with the `id` attribute of `cat-photo-element` and give it the background color of green. In your `style` element:

```css
#cat-photo-element {
  background-color: green;
}
```

- An element's `padding` controls the amount of space between the element's content and its `border`.

![Screen Shot 2021-12-26 at 13.17.03.png](https://raw.githubusercontent.com/yxshi610/images/main/2021/12/26-13-17-06-Screen%20Shot%202021-12-26%20at%2013.17.03.png)

- An element's `margin` controls the amount of space between an element's `border` and surrounding elements. If you set an element's `margin` to a negative value, the element will grow larger.

- Instead of specifying an element's `padding-top`, `padding-right`, `padding-bottom`, and `padding-left` properties individually, you can specify them all in one line, like this:

```css
padding: 10px 20px 10px 20px;
```

- For this challenge, you will use the `[attr=value]` attribute selector to style the checkboxes in CatPhotoApp. This selector matches and styles elements with a specific attribute value. For example, the below code changes the margins of all elements with the attribute `type` and a corresponding value of `radio`:

```css
[type='radio'] {
  margin: 20px 0px 20px 0px;
}
```

- The last several challenges all set an element's margin or padding with pixels (`px`). Pixels are a type of length unit, which is what tells the browser how to size or space an item. In addition to `px`, CSS has a number of different length unit options that you can use.
  
  The two main types of length units are absolute and relative. Absolute units tie to physical units of length. For example, `in` and `mm` refer to inches and millimeters, respectively. Absolute length units approximate the actual measurement on a screen, but there are some differences depending on a screen's resolution.
  
  Relative units, such as `em` or `rem`, are relative to another length value. For example, `em` is based on the size of an element's font. If you use it to set the `font-size` property itself, it's relative to the parent's `font-size`.

- It doesn't matter which order the classes are listed in the HTML element. However, the order of the `class` declarations in the `<style>` section is what is important. The second declaration will always take precedence over the first. Because `.blue-text` is declared second, it overrides the attributes of `.pink-text`
  
  inline-style > #id > .class
  
  In many situations, you will use CSS libraries. These may accidentally override your own CSS. So when you absolutely need to be sure that an element has specific CSS, you can use `!important`. Let's add the keyword `!important` to your pink-text element's color declaration to make 100% sure that your `h1` element will be pink.

```css
color: red !important;
```

- In CSS, we can use 6 hexadecimal digits to represent colors, two each for the red (R), green (G), and blue (B) components. For example, `#000000` is black and is also the lowest possible value. You can find more information about the [RGB color system here](https://www.freecodecamp.org/news/rgb-color-html-and-css-guide/#whatisthergbcolormodel).
- RGB values

       The `RGB` value for black looks like this:

```css
rgb(0, 0, 0)
```

- CSS Variables are a powerful way to change many CSS style properties at once by changing only one value. To create a CSS variable, you just need to give it a name with two hyphens in front of it and assign it a value like this:

```css
--penguin-skin: gray;
```

After you create your variable, you can assign its value to other CSS properties by referencing the name you gave it. (black is a fallback color)

```css
background: var(--penguin-skin, black);
```

- `:root` is a pseudo-class selector that matches the root element of the document, usually the `html` element. By creating your variables in `:root`, they will be available globally and can be accessed from any other selector in the style sheet.

- play with media size. (responsive)

```css
<style>
    :root {
    --penguin-size: 300px;
    --penguin-skin: gray;
    }

    @media (max-width: 350px) {
        :root {
        --penguin-size: 200px;
        --penguin-skin: black;
        }
    }
</style>
```

## Applied Visual Design

- Text is often a large part of web content. CSS has several options for how to align it with the `text-align` property.
  
  `text-align: justify;` spaces the text so that each line has equal width.
  
  `text-align: center;` centers the text
  
  `text-align: right;` right-aligns the text
  
  And `text-align: left;` (the default) left-aligns the text.

- width, height.

- To make text bold, you can use the `strong` tag. This is often used to draw attention to text and symbolize that it is important. With the `strong` tag, the browser applies the CSS of `font-weight: bold;` to the element.

```html
<p>Google at <strong>Stanford University</strong>.</p>
```

- To underline text, you can use the `u` tag. This is often used to signify that a section of text is important, or something to remember. With the `u` tag, the browser applies the CSS of `text-decoration: underline;` to the element.

- To emphasize text, you can use the `em` tag. This displays text as italicized, as the browser applies the CSS of `font-style: italic;` to the element.

- To strikethrough text, which is when a horizontal line cuts across the characters, you can use the `s` tag. It shows that a section of text is no longer valid. With the `s` tag, the browser applies the CSS of `text-decoration: line-through;` to the element.

- You can use the `hr` tag to add a horizontal line across the width of its containing element. This can be used to define a change in topic or to visually separate groups of content.

<img title="" src="https://raw.githubusercontent.com/yxshi610/images/main/2021/12/26-14-11-00-Screen%20Shot%202021-12-26%20at%2014.10.56.png" alt="Screen Shot 2021-12-26 at 14.10.56.png" data-align="center">

- Instead of adjusting your overall background or the color of the text to make the foreground easily readable, you can add a `background-color` to the element holding the text you want to emphasize. This challenge uses `rgba()` instead of `hex` codes or normal `rgb()`.
  
  > rgba stands for:  
  >   r = red  
  >   g = green  
  >   b = blue  
  >   a = alpha/level of opacity
  
  The RGB values can range from 0 to 255. The alpha value can range from 1, which is fully opaque or a solid color, to 0, which is fully transparent or clear. `rgba()` is great to use in this case, as it allows you to adjust the opacity. This means you don't have to completely block out the background.

- box-shadow to card-like ele

        `offset-x` (how far to push the shadow horizontally from the element),

        `offset-y` (how far to push the shadow vertically from the element),

        `blur-radius`,

        `spread-radius` and

        `color`, in that order.

The `blur-radius` and `spread-radius` values are optional.

Multiple box-shadows can be created by using commas to separate properties of each `box-shadow` element.

```css
box-shadow: 0 10px 20px rgba(0,0,0,0.19), 0 6px 6px rgba(0,0,0,0.23);
```

<img src="https://raw.githubusercontent.com/yxshi610/images/main/2021/12/26-14-15-53-Screen%20Shot%202021-12-26%20at%2014.15.48.png" title="" alt="Screen Shot 2021-12-26 at 14.15.48.png" data-align="center">

- opacity: 0.7; line-height: 20px;

- text-transform

| Value        | Result                                                 |
| ------------ | ------------------------------------------------------ |
| `lowercase`  | "transform me"                                         |
| `uppercase`  | "TRANSFORM ME"                                         |
| `capitalize` | "Transform Me"                                         |
| `initial`    | Use the default value                                  |
| `inherit`    | Use the `text-transform` value from the parent element |
| `none`       | **Default:** Use the original text                     |

- A pseudo-class is a keyword that can be added to selectors, in order to select a specific state of the element.
  
  For example, the styling of an anchor tag can be changed for its hover state using the `:hover` pseudo-class selector. Here's the CSS to change the `color` of the anchor tag to red during its hover state.

```css
a:hover {
  color: red;
}
```

- CSS treats each HTML element as its own box, which is usually referred to as the CSS Box Model. Block-level items automatically start on a new line (think headings, paragraphs, and divs) while inline items sit within surrounding content (like images or spans). The default layout of elements in this way is called the normal flow of a document, but CSS offers the position property to override it.
  
  When the position of an element is set to `relative`, it allows you to specify how CSS should move it *relative* to its current position in the normal flow of the page. It pairs with the CSS offset properties of `left` or `right`, and `top` or `bottom`. These say how many pixels, percentages, or ems to move the item *away* from where it is normally positioned. The following example moves the paragraph 10 pixels away from the bottom:

```css
p {
  position: relative;
  bottom: 10px;
}
```

       does not affect others.

- The next option for the CSS `position` property is `absolute`, which locks the element in place relative to its parent container. Unlike the `relative` position, this removes the element from the normal flow of the document, so surrounding items ignore it. The CSS offset properties (top or bottom and left or right) are used to adjust the position.
  
  One nuance with absolute positioning is that it will be locked relative to its closest *positioned* ancestor. If you forget to add a position rule to the parent item, (this is typically done using `position: relative;`), the browser will keep looking up the chain and ultimately default to the `body` tag.

- The next layout scheme that CSS offers is the `fixed` position, which is a type of absolute positioning that locks an element relative to the browser window. Similar to absolute positioning, it's used with the CSS offset properties and also removes the element from the normal flow of the document. Other items no longer "realize" where it is positioned, which may require some layout adjustments elsewhere.
  
  One key difference between the `fixed` and `absolute` positions is that an element with a fixed position won't move when the user scrolls.

- The next positioning tool does not actually use `position`, but sets the `float` property of an element. Floating elements are removed from the normal flow of a document and pushed to either the `left` or `right` of their containing parent element. It's commonly used with the `width` property to specify how much horizontal space the floated element requires.

```css
<style>    
    #left {
      float: left;
      width: 50%;
    }
    #right {
      float: right;
      width: 40%;
    }
</style>
```

- When elements are positioned to overlap (i.e. using `position: absolute | relative | fixed | sticky`), the element coming later in the HTML markup will, by default, appear on the top of the other elements. However, the `z-index` property can specify the order of how elements are stacked on top of one another. It must be an integer (i.e. a whole number and not a decimal), and higher values for the `z-index` property of an element move it higher in the stack than those with lower values.

```css
.first {
    background-color: red;
    position: absolute;
    z-index: 2;
  }
  .second {
    background-color: blue;
    position: absolute;
    left: 40px;
    top: 50px;
    z-index: 1;
  }
```

- Another positioning technique is to center a block element horizontally. One way to do this is to set its `margin` to a value of auto.
  
  This method works for images, too. Images are inline elements by default, but can be changed to block elements when you set the `display` property to `block`.

- Some examples of complementary colors with their hex codes are:
  
  > red (#FF0000) and cyan (#00FFFF)  
  > green (#00FF00) and magenta (#FF00FF)  
  > blue (#0000FF) and yellow (#FFFF00)

- There are various methods of selecting different colors that result in a harmonious combination in design. One example that can use tertiary colors is called the split-complementary color scheme. This scheme starts with a base color, then pairs it with the two colors that are adjacent to its complement. The three colors provide strong visual contrast in a design, but are more subtle than using two complementary colors.
  
  Here are three colors created using the split-complement scheme:
  
  | Color     | Hex Code |
  | --------- | -------- |
  | orange    | #FF7F00  |
  | cyan      | #00FFFF  |
  | raspberry | #FF007F  |

- **Hue** is what people generally think of as 'color'. If you picture a spectrum of colors starting with red on the left, moving through green in the middle, and blue on right, the hue is where a color fits along this line. In `hsl()`, hue uses a color wheel concept instead of the spectrum, where the angle of the color on the circle is given as a value between 0 and 360.
  
  **Saturation** is the amount of gray in a color. A fully saturated color has no gray in it, and a minimally saturated color is almost completely gray. This is given as a percentage with 100% being fully saturated.
  
  **Lightness** is the amount of white or black in a color. A percentage is given ranging from 0% (black) to 100% (white), where 50% is the normal color.
  
  Here are a few examples of using `hsl()` with fully-saturated, normal lightness colors:
  
  | Color   | HSL                 |
  | ------- | ------------------- |
  | red     | hsl(0, 100%, 50%)   |
  | yellow  | hsl(60, 100%, 50%)  |
  | green   | hsl(120, 100%, 50%) |
  | cyan    | hsl(180, 100%, 50%) |
  | blue    | hsl(240, 100%, 50%) |
  | magenta | hsl(300, 100%, 50%) |

- CSS provides the ability to use color transitions, otherwise known as gradients, on elements. This is accessed through the `background` property's `linear-gradient()` function.

```css
background: linear-gradient(gradient_direction, color 1, color 2, color 3, ...);
```

The first argument specifies the direction from which color transition starts - it can be stated as a degree, where `90deg` makes a horizontal gradient (from left to right) and `45deg` makes a diagonal gradient (from bottom left to top right). The following arguments specify the order of colors used in the gradient.

Example:

```css
background: linear-gradient(90deg, red, yellow, rgb(204, 204, 255));
```

- The angle value is the direction of the gradient. Color stops are like width values that mark where a transition takes place, and are given with a percentage or a number of pixels.
  
  The gradient starts with the color `yellow` at 0 pixels which blends into the second color `blue` at 40 pixels away from the start. Since the next color stop is also at 40 pixels, the gradient immediately changes to the third color `green`, which itself blends into the fourth color value `red` as that is 80 pixels away from the beginning of the gradient.
  
  For this example, it helps to think about the color stops as pairs where every two colors blend together.
  
  ```css
  0px [yellow -- blend -- blue] 40px [green -- blend -- red] 80px
  
  background: repeating-linear-gradient(
        90deg,
        yellow 0px,
        blue 40px,
        green 40px,
        red 80px
      );
  ```

<img src="https://raw.githubusercontent.com/yxshi610/images/main/2021/12/26-14-47-57-Screen%20Shot%202021-12-26%20at%2014.47.54.png" title="" alt="Screen Shot 2021-12-26 at 14.47.54.png" data-align="center">

<img src="https://raw.githubusercontent.com/yxshi610/images/main/2021/12/26-14-50-05-Screen%20Shot%202021-12-26%20at%2014.50.00.png" title="" alt="Screen Shot 2021-12-26 at 14.50.00.png" data-align="center">

- The `background` property supports the `url()` function in order to link to an image of the chosen texture or pattern. The link address is wrapped in quotes inside the parentheses.

- To change the scale of an element, CSS has the `transform` property, along with its `scale()` function. The following code example doubles the size of all the paragraph elements on the page:
  
  ```css
  p {
    transform: scale(2);
  }
  ```

- `transform` property is `skewX()`, which skews the selected element along its X (horizontal) axis by a given degree. Same with `skewY()`.
  
  The following code skews the paragraph element by -32 degrees along the X-axis.
  
  ```css
  p {
    transform: skewX(-32deg);
  }
  ```

![Screen Shot 2021-12-26 at 15.02.52.png](https://raw.githubusercontent.com/yxshi610/images/main/2021/12/26-15-02-55-Screen%20Shot%202021-12-26%20at%2015.02.52.png)

- `::before` creates a pseudo-element that is the first child of the selected element; `::after` creates a pseudo-element that is the last child of the selected element. In the following example, a `::before` pseudo-element is used to add a rectangle to an element with the class `heart`:
  
  ```css
  .heart::before {
    content: "";
    background-color: yellow;
    border-radius: 25%;
    position: absolute;
    height: 50px;
    width: 70px;
    top: -50px;
    left: 5px;
  }
  ```
  
  For the `::before` and `::after` pseudo-elements to function properly, they must have a defined `content` property. This property is usually used to add things like a photo or text to the selected element. When the `::before` and `::after` pseudo-elements are used to make shapes, the `content` property is still required, but it's set to an empty string. 

- To animate an element, you need to know about the animation properties and the `@keyframes` rule. The animation properties control how the animation should behave and the `@keyframes` rule controls what happens during that animation. There are eight animation properties in total. 
  
  `animation-name` sets the name of the animation, which is later used by `@keyframes` to tell CSS which rules go with which animations.
  
  `animation-duration` sets the length of time for the animation.
  
  `@keyframes` is how to specify exactly what happens within the animation over the duration. This is done by giving CSS properties for specific "frames" during the animation, with percentages ranging from 0% to 100%. Then CSS applies the magic to transition the element over the given duration to act out the scene. Here's an example to illustrate the usage of `@keyframes` and the animation properties:
  
  ```css
  #anim {
    animation-name: colorful;
    animation-duration: 3s;
  }
  
  @keyframes colorful {
    0% {
      background-color: blue;
    }
    100% {
      background-color: yellow;
    }
  }
  ```

- You can use CSS `@keyframes` to change the color of a button in its hover state.
  
  Here's an example of changing the width of an image on hover:
  
  ```html
  <style>
    img {
      width: 30px;
    }
    img:hover {
      animation-name: width;
      animation-duration: 500ms;
    }
  
    @keyframes width {
      100% {
        width: 40px;
      }
    }
  </style>
  ```

- This can be done by setting the `animation-fill-mode` property to `forwards`. The `animation-fill-mode` specifies the style applied to an element when the animation has finished. You can set it like so:
  
  ```css
  animation-fill-mode: forwards;
  ```

- The previous challenges covered how to use some of the animation properties and the `@keyframes` rule. Another animation property is the `animation-iteration-count`, which allows you to control how many times you would like to loop through the animation. Here's an example:
  
  ```css
  animation-iteration-count: 3;
  ```
  
  In this case the animation will stop after running 3 times, but it's possible to make the animation run continuously by setting that value to `infinite`.

- In CSS animations, the `animation-timing-function` property controls how quickly an animated element changes over the duration of the animation. If the animation is a car moving from point A to point B in a given time (your `animation-duration`), the `animation-timing-function` says how the car accelerates and decelerates over the course of the drive.
  
  There are a number of predefined keywords available for popular options. For example, the default value is `ease`, which starts slow, speeds up in the middle, and then slows down again in the end. Other options include `ease-out`, which is quick in the beginning then slows down, `ease-in`, which is slow in the beginning, then speeds up at the end, or `linear`, which applies a constant animation speed throughout.

- In CSS animations, Bezier curves are used with the `cubic-bezier` function. The shape of the curve represents how the animation plays out. The curve lives on a 1 by 1 coordinate system. The X-axis of this coordinate system is the duration of the animation (think of it as a time scale), and the Y-axis is the change in the animation.
  
  The `cubic-bezier` function consists of four main points that sit on this 1 by 1 grid: `p0`, `p1`, `p2`, and `p3`. `p0` and `p3` are set for you - they are the beginning and end points which are always located respectively at the origin (0, 0) and (1, 1). You set the x and y values for the other two points, and where you place them in the grid dictates the shape of the curve for the animation to follow. This is done in CSS by declaring the x and y values of the `p1` and `p2` "anchor" points in the form: `(x1, y1, x2, y2)`. Pulling it all together, here's an example of a Bezier curve in CSS code:
  
  ```css
  animation-timing-function: cubic-bezier(0.25, 0.25, 0.75, 0.75);
  ```
  
  In the example above, the x and y values are equivalent for each point (x1 = 0.25 = y1 and x2 = 0.75 = y2), which if you remember from geometry class, results in a line that extends from the origin to point (1, 1). This animation is a linear change of an element during the length of an animation, and is the same as using the `linear` keyword. In other words, it changes at a constant speed.
  
  Can be larger than 1.
  
  ## Applied Accessibility

- add alt="" to make img more beautiful.

- As an example, a page with an `h2` element followed by several subsections labeled with `h4` elements would confuse a screen reader user. With six choices, it's tempting to use a tag because it looks better in a browser, but you can use CSS to edit the relative sizing.
  
  One final point, each page should always have one (and only one) `h1` element, which is the main subject of your content. This and the other headings are used in part by search engines to understand the topic of the page.

- HTML5 introduced several new elements that give developers more options while also incorporating accessibility features. These tags include `main`, `header`, `footer`, `nav`, `article`, and `section`, among others. By default, a browser renders these elements similar to the humble `div`.
  
  The `main` element is used to wrap (you guessed it) the main content, and there should be only one per page. It's meant to surround the information related to your page's central topic. It's not meant to include items that repeat across pages, like navigation links or banners.
  
  The `main` tag also has an embedded landmark feature that assistive technology can use to navigate to the main content quickly. If you've ever seen a "Jump to Main Content" link at the top of a page, using the `main` tag automatically gives assistive devices that functionality.

- `article` is another one of the new HTML5 elements that add semantic meaning to your markup. `article` is a sectioning element and is used to wrap independent, self-contained content. The tag works well with blog entries, forum posts, or news articles.
  
  **Note:** The `section` element is also new with HTML5, and has a slightly different semantic meaning than `article`. An `article` is for standalone content, and a `section` is for grouping thematically related content. They can be used within each other, as needed. For example, if a book is the `article`, then each chapter is a `section`. When there's no relationship between groups of content, then use a `div`.
  
  `<div>` - groups content `<section>` - groups related content `<article>` - groups independent, self-contained content

- `header` tag. It's used to wrap introductory information or navigation links for its parent tag and works well around content that's repeated at the top on multiple pages.
  
  `header` shares the embedded landmark feature you saw with `main`, allowing assistive technologies to quickly navigate to that content.
  
  **Note:** The `header` is meant for use in the `body` tag of your HTML document. It is different than the `head` element, which contains the page's title, meta information, etc.

- wrap around the main navigation links in your page.
  
  If there are repeated site links at the bottom of the page, it isn't necessary to markup those with a `nav` tag as well. Using a `footer` (covered in the next challenge) is sufficient.

- `footer` element has a built-in landmark feature that allows assistive devices to quickly navigate to it. It's primarily used to contain copyright information or links to related documents that usually sit at the bottom of a page.

- The `audio` tag supports the `controls` attribute. This shows the browser default play, pause, and other controls, and supports keyboard functionality. This is a boolean attribute, meaning it doesn't need a value, its presence on the tag turns the setting on.
  
  Here's an example:
  
  ```html
  <audio id="meowClip" controls>
    <source src="audio/meow.mp3" type="audio/mpeg">
    <source src="audio/meow.ogg" type="audio/ogg">
  </audio>
  ```

<img src="https://raw.githubusercontent.com/yxshi610/images/main/2021/12/26-15-41-20-Screen%20Shot%202021-12-26%20at%2015.41.17.png" title="" alt="Screen Shot 2021-12-26 at 15.41.17.png" data-align="center">

- note that the `figcaption` goes inside the `figure` tags and can be combined with other elements:
  
  ```html
  <figure>
    <img src="roundhouseDestruction.jpeg" alt="Photo of Camper Cat executing a roundhouse kick">
    <br>
    <figcaption>
      Master Camper Cat demonstrates proper form of a roundhouse kick.
    </figcaption>
  </figure>
  ```

- The value of the `for` attribute must be the same as the value of the `id` attribute of the form control. Here's an example:
  
  ```html
  <form>
    <label for="name">Name:</label>
    <input type="text" id="name" name="name">
  </form>
  ```

- The `fieldset` tag surrounds the entire grouping of radio buttons to achieve this. It often uses a `legend` tag to provide a description for the grouping, which screen readers read for each choice in the `fieldset` element.
  
  The `fieldset` wrapper and `legend` tag are not necessary when the choices are self-explanatory, like a gender selection. Using a `label` with the `for` attribute for each radio button is sufficient.
  
  Here's an example:
  
  ```html
  <form>
    <fieldset>
      <legend>Choose one of these three items:</legend>
      <input id="one" type="radio" name="items" value="one">
      <label for="one">Choice One</label><br>
      <input id="two" type="radio" name="items" value="two">
      <label for="two">Choice Two</label><br>
      <input id="three" type="radio" name="items" value="three">
      <label for="three">Choice Three</label>
    </fieldset>
  </form>
  ```

![Screen Shot 2021-12-26 at 15.47.06.png](https://raw.githubusercontent.com/yxshi610/images/main/2021/12/26-15-47-09-Screen%20Shot%202021-12-26%20at%2015.47.06.png)

- time
  
  ```html
  <input type="date">
  <p>S<time datetime="2013-02-13">last Wednesday</time>a.</p>
  ```

- what exactly does "sufficient" mean?
  
  The Web Content Accessibility Guidelines (WCAG) recommend at least a 4.5 to 1 contrast ratio for normal text. The ratio is calculated by comparing the relative luminance values of two colors. This ranges from 1:1 for the same color, or no contrast, to 21:1 for white against black, the most substantial contrast. There are many contrast checking tools available online that calculate this ratio for you.

- HTML offers the `accesskey` attribute to specify a shortcut key to activate or bring focus to an element. Adding an `accesskey` attribute can make navigation more efficient for keyboard-only users.
  
  HTML5 allows this attribute to be used on any element, but it's particularly useful when it's used with interactive ones. This includes links, buttons, and form controls.
  
  Here's an example:
  
  ```html
  <button accesskey="b">Important Button</button>
  ```

- The HTML `tabindex` attribute has three distinct functions relating to an element's keyboard focus. When it's on a tag, it indicates that the element can be focused on. The value (an integer that's positive, negative, or zero) determines the behavior.
  
  Certain elements, such as links and form controls, automatically receive keyboard focus when a user tabs through a page. It's in the same order as the elements come in the HTML source markup. This same functionality can be given to other elements, such as `div`, `span`, and `p`, by placing a `tabindex="0"` attribute on them. Here's an example:
  
  ```html
  <div tabindex="0">I need keyboard focus!</div>
  ```
  
  **Note:** A negative `tabindex` value (typically -1) indicates that an element is focusable, but is not reachable by the keyboard. This method is generally used to bring focus to content programmatically (like when a `div` used for a pop-up window is activated), and is beyond the scope of these challenges.
  
  Bonus - using `tabindex` also enables the CSS pseudo-class `:focus` to work on the `p` tag.
  
  Setting a `tabindex="1"` will bring keyboard focus to that element first. Then it cycles through the sequence of specified `tabindex` values (2, 3, etc.), before moving to default and `tabindex="0"` items.

## Responsive Web Design Principles

- Media Queries consist of a media type, and if that media type matches the type of device the document is displayed on, the styles are applied. You can have as many selectors and styles inside your media query as you want.
  
  Here's an example of a media query that returns the content when the device's width is less than or equal to `100px`:
  
  ```css
  @media (max-width: 100px) { /* CSS Rules */ }
  ```
  
  and the following media query returns the content when the device's height is more than or equal to `350px`:
  
  ```css
  @media (min-height: 350px) { /* CSS Rules */ }
  ```
  
  Remember, the CSS inside the media query is applied only if the media type matches that of the device being used.

- Making images responsive with CSS is actually very simple. You just need to add these properties to an image:
  
  ```css
  img {
    max-width: 100%;
    height: auto;
  }
  ```
  
  The `max-width` of `100%` will make sure the image is never wider than the container it is in, and the `height` of `auto` will make the image keep its original aspect ratio.

- The simplest way to make your images properly appear on High-Resolution Displays, such as the MacBook Pros "retina display" is to define their `width` and `height` values as only half of what the original file is. Here is an example of an image that is only using half of the original height and width:
  
  ```html
  <style>
    img { height: 250px; width: 250px; }
  </style>
  <img src="coolPic500x500" alt="A most excellent picture">
  ```

- Instead of using `em` or `px` to size text, you can use viewport units for responsive typography. Viewport units, like percentages, are relative units, but they are based off different items. Viewport units are relative to the viewport dimensions (width or height) of a device, and percentages are relative to the size of the parent container element.
  
  The four different viewport units are:
  
  - `vw` (viewport width): `10vw` would be 10% of the viewport's width.
  - `vh` (viewport height): `3vh` would be 3% of the viewport's height.
  - `vmin` (viewport minimum): `70vmin` would be 70% of the viewport's smaller dimension (height or width).
  - `vmax` (viewport maximum): `100vmax` would be 100% of the viewport's bigger dimension (height or width).
  
  Here is an example that sets a `body` tag to 30% of the viewport's width.
  
  ```css
  body { width: 30vw; }
  ```

## CSS Flexbox

- Placing the CSS property `display: flex;` on an element allows you to use other flex properties to build a responsive page.

- Adding `display: flex` to an element turns it into a flex container. This makes it possible to align any children of that element into rows or columns. You do this by adding the `flex-direction` property to the parent item and setting it to row or column. Creating a row will align the children horizontally, and creating a column will align the children vertically.
  
  Other options for `flex-direction` are `row-reverse` and `column-reverse`.
  
  **Note:** The default value for the `flex-direction` property is `row`.

- Sometimes the flex items within a flex container do not fill all the space in the container. It is common to want to tell CSS how to align and space out the flex items a certain way. Fortunately, the `justify-content` property has several options to do this. But first, there is some important terminology to understand before reviewing those options.
  
  <img title="" src="https://raw.githubusercontent.com/yxshi610/images/main/2021/12/26-16-35-48-Screen%20Shot%202021-12-26%20at%2016.35.46.png" alt="Screen Shot 2021-12-26 at 16.35.46.png" data-align="inline">
  
  Recall that setting a flex container as a row places the flex items side-by-side from left-to-right. A flex container set as a column places the flex items in a vertical stack from top-to-bottom. For each, the direction the flex items are arranged is called the **main axis**. For a row, this is a horizontal line that cuts through each item. And for a column, the main axis is a vertical line through the items.
  
  There are several options for how to space the flex items along the line that is the main axis. One of the most commonly used is `justify-content: center;`, which aligns all the flex items to the center inside the flex container. Other options include:
  
  - `flex-start`: aligns items to the start of the flex container. For a row, this pushes the items to the left of the container. For a column, this pushes the items to the top of the container. This is the default alignment if no `justify-content` is specified.
  - `flex-end`: aligns items to the end of the flex container. For a row, this pushes the items to the right of the container. For a column, this pushes the items to the bottom of the container.
  - `space-between`: aligns items to the center of the main axis, with extra space placed between the items. The first and last items are pushed to the very edge of the flex container. 
  - `space-around`: similar to `space-between` but the first and last items are not locked to the edges of the container, the space is distributed around all the items with a half space on either end of the flex container.
  - `space-evenly`: Distributes space evenly between the flex items with a full space at either end of the flex container

- CSS offers the `align-items` property to align flex items along the cross axis. For a row, it tells CSS how to push the items in the entire row up or down within the container. And for a column, how to push all the items left or right within the container.
  
  The different values available for `align-items` include:
  
  - `flex-start`: aligns items to the start of the flex container. For rows, this aligns items to the top of the container. For columns, this aligns items to the left of the container.
  - `flex-end`: aligns items to the end of the flex container. For rows, this aligns items to the bottom of the container. For columns, this aligns items to the right of the container.
  - `center`: align items to the center. For rows, this vertically aligns items (equal space above and below the items). For columns, this horizontally aligns them (equal space to the left and right of the items).
  - `stretch`: stretch the items to fill the flex container. For example, rows items are stretched to fill the flex container top-to-bottom. This is the default value if no `align-items` value is specified.
  - `baseline`: align items to their baselines. Baseline is a text concept, think of it as the line that the letters sit on.

- CSS flexbox has a feature to split a flex item into multiple rows (or columns). By default, a flex container will fit all flex items together. For example, a row will all be on one line.
  
  However, using the `flex-wrap` property tells CSS to wrap items. This means extra items move into a new row or column. The break point of where the wrapping happens depends on the size of the items and the size of the container.
  
  CSS also has options for the direction of the wrap:
  
  - `nowrap`: this is the default setting, and does not wrap items.
  
  - `wrap`: wraps items onto multiple lines from top-to-bottom if they are in rows and left-to-right if they are in columns.
  
  - `wrap-reverse`: wraps items onto multiple lines from bottom-to-top if they are in rows and right-to-left if they are in columns.
    
    ![Screen Shot 2021-12-26 at 16.42.32.png](https://raw.githubusercontent.com/yxshi610/images/main/2021/12/26-16-42-36-Screen%20Shot%202021-12-26%20at%2016.42.32.png)

- When it's used, it allows an item to shrink if the flex container is too small. Items shrink when the width of the parent container is smaller than the combined widths of all the flex items within it.
  
  The `flex-shrink` property takes numbers as values. The higher the number, the more it will shrink compared to the other items in the container. For example, if one item has a `flex-shrink` value of `1` and the other has a `flex-shrink` value of `3`, the one with the value of `3` will shrink three times as much as the other.
  
  ![Screen Shot 2021-12-26 at 16.43.55.png](https://raw.githubusercontent.com/yxshi610/images/main/2021/12/26-16-43-59-Screen%20Shot%202021-12-26%20at%2016.43.55.png)

- opposite is `flex-grow`

- The `flex-basis` property specifies the initial size of the item before CSS makes adjustments with `flex-shrink` or `flex-grow`.
  
  The units used by the `flex-basis` property are the same as other size properties (`px`, `em`, `%`, etc.). The value `auto` sizes items based on the content.

- There is a shortcut available to set several flex properties at once. The `flex-grow`, `flex-shrink`, and `flex-basis` properties can all be set together by using the `flex` property.
  
  For example, `flex: 1 0 10px;` will set the item to `flex-grow: 1;`, `flex-shrink: 0;`, and `flex-basis: 10px;`.
  
  The default property settings are `flex: 0 1 auto;`.

- The `order` property is used to tell CSS the order of how flex items appear in the flex container. By default, items will appear in the same order they come in the source HTML. The property takes numbers as values, and negative numbers can be used.

- `align-self` allows you to adjust each item's alignment individually, instead of setting them all at once. This is useful since other common adjustment techniques using the CSS properties `float`, `clear`, and `vertical-align` do not work on flex items.
  
  `align-self` accepts the same values as `align-items` and will override any value set by the `align-items` property.

## CSS Grid

- Turn any HTML element into a grid container by setting its `display` property to `grid`. This gives you the ability to use all the other properties associated with CSS Grid.
  
  **Note:** In CSS Grid, the parent element is referred to as the container and its children are called items.

- You need to define the structure of the grid as well. To add some columns to the grid, use the `grid-template-columns` property on a grid container as demonstrated below:
  
  ```css
  .container {
    display: grid;
    grid-template-columns: 50px 50px;
  }
  ```

<img title="" src="https://raw.githubusercontent.com/yxshi610/images/main/2021/12/27-14-02-37-Screen%20Shot%202021-12-27%20at%2014.02.34.png" alt="Screen Shot 2021-12-27 at 14.02.34.png" data-align="center">

      same with `grid-template-rows`

- You can use absolute and relative units like `px` and `em` in CSS Grid to define the size of rows and columns. You can use these as well:
  
  `fr`: sets the column or row to a fraction of the available space,
  
  `auto`: sets the column or row to the width or height of its content automatically,
  
  `%`: adjusts the column or row to the percent width of its container.
  
  Here's the code that generates the output in the preview:
  
  ```css
  grid-template-columns: auto 50px 10% 2fr 1fr;
  ```

<img src="https://raw.githubusercontent.com/yxshi610/images/main/2021/12/27-14-05-24-Screen%20Shot%202021-12-27%20at%2014.05.20.png" title="" alt="Screen Shot 2021-12-27 at 14.05.20.png" data-align="center">

- To add a gap between the columns:
  
  ```css
  grid-column-gap: 10px;
  ```
  
  This creates 10px of empty space between all of our columns。
  
  same with row.

- If `grid-gap` has one value, it will create a gap between all rows and columns. If there are two values, it will use the first one to set the gap between the rows and the second value for the columns.

- The hypothetical horizontal and vertical lines that create the grid are referred to as lines. These lines are numbered starting with 1 at the top left corner of the grid and move right for columns and down for rows, counting upward. This is what the lines look like for a 3x3 grid:
  
  <img src="https://raw.githubusercontent.com/yxshi610/images/main/2021/12/27-14-09-26-Screen%20Shot%202021-12-27%20at%2014.09.23.png" title="" alt="Screen Shot 2021-12-27 at 14.09.23.png" data-align="center">
  
  To control the number of columns an item will consume, you can use the `grid-column` property in conjunction with the line numbers you want the item to start and stop at.
  
  Here's an example:
  
  ```css
  grid-column: 1 / 3;
  ```
  
  This will make the item start at the first vertical line of the grid on the left and span to the 3rd line of the grid, consuming two columns.
  
  same with row.

- In CSS Grid, the content of each item is located in a box which is referred to as a cell. You can align the content's position within its cell horizontally using the `justify-self` property on a grid item. By default, this property has a value of `stretch`, which will make the content fill the whole width of the cell. This CSS Grid property accepts other values as well:
  
  `start`: aligns the content at the left of the cell,
  
  `center`: aligns the content in the center of the cell,
  
  `end`: aligns the content at the right of the cell.

- Just as you can align an item horizontally, there's a way to align an item vertically as well. To do this, you use the `align-self` property on an item. 

- align them all at once horizontally by using `justify-items` on your grid container. same with align.

- You can group cells of your grid together into an area and give the area a custom name. Do this by using `grid-template-areas` on the container like this:
  
  ```css
  grid-template-areas:
    "header header header"
    "advert content content"
    "footer footer footer";
  ```
  
  The code above groups the cells of the grid into four areas; `header`, `advert`, `content`, and `footer`. Every word represents a cell and every pair of quotation marks represent a row.

- After creating an area template for your grid container, as shown in the previous challenge, you can place an item in your custom area by referencing the name you gave it. To do this, you use the `grid-area` property on an item like this:
  
  ```css
  .item1 {
    grid-area: header;
  }
  ```

- If your grid doesn't have an areas template to reference, you can create an area on the fly for an item to be placed like this:
  
  ```css
  item1 { grid-area: 1/1/2/4; }
  ```
  
  This is using the line numbers you learned about earlier to define where the area for this item will be. The numbers in the example above represent these values:
  
  ```css
  grid-area: horizontal line to start at / vertical line to start at / horizontal line to end at / vertical line to end at;
  ```
  
  So the item in the example will consume the rows between lines 1 and 2, and the columns between lines 1 and 4.

- by using the `repeat` function to specify the number of times you want your column or row to be repeated, followed by a comma and the value you want to repeat.
  
  Here's an example that would create the 100 row grid, each row at 50px tall.
  
  ```css
  grid-template-rows: repeat(100, 50px);
  ```
  
  You can also repeat multiple values with the repeat function and insert the function amongst other values when defining a grid structure. Here's what that looks like:
  
  ```css
  grid-template-columns: repeat(2, 1fr 50px) 20px;
  ```
  
  This translates to:
  
  ```css
  grid-template-columns: 1fr 50px 1fr 50px 20px;
  ```
  
  **Note:** The `1fr 50px` is repeated twice followed by 20px.

- There's another built-in function to use with `grid-template-columns` and `grid-template-rows` called `minmax`. It's used to limit the size of items when the grid container changes size. To do this you need to specify the acceptable size range for your item. Here is an example:
  
  ```css
  grid-template-columns: 100px minmax(50px, 200px);
  ```
  
  In the code above, `grid-template-columns` is set to create two columns; the first is 100px wide, and the second has the minimum width of 50px and the maximum width of 200px.

- The repeat function comes with an option called auto-fill. This allows you to automatically insert as many rows or columns of your desired size as possible depending on the size of the container. You can create flexible layouts when combining `auto-fill` with `minmax`, like this:
  
  ```css
  repeat(auto-fill, minmax(60px, 1fr));
  ```
  
  When the container changes size, this setup keeps inserting 60px columns and stretching them until it can insert another one. **Note:** If your container can't fit all your items on one row, it will move them down to a new one.

- `auto-fit` works almost identically to `auto-fill`. The only difference is that when the container's size exceeds the size of all the items combined, `auto-fill` keeps inserting empty rows or columns and pushes your items to the side, while `auto-fit` collapses those empty rows or columns and stretches your items to fit the size of the container.
  
  **Note:** If your container can't fit all your items on one row, it will move them down to a new one.
  
  ![Screen Shot 2021-12-27 at 14.23.04.png](https://raw.githubusercontent.com/yxshi610/images/main/2021/12/27-14-23-08-Screen%20Shot%202021-12-27%20at%2014.23.04.png)

- by setting the `display` and `grid-template-columns` properties of the element with the `item3` class, you create a grid within your grid.

## Responsive Web Design Projects

1. Tribute Page
- center image:

```css
img {
    display: block;
    margin: auto;
}
```

2. Survey Form
- input

```css
<label for="n">number:</label>
<input type="number" id="n" name="n" min="1" max="5">
# dropdown
<select id="most-like" name="mostLike" class="form-control" required="">
  <option disabled="" selected="" value="">Select an option</option>
  <option value="challenges">Challenges</option>
  <option value="projects">Projects</option>
</select>
<input type="submit" id="submit">
```

3. Landing Page

4. tech doc
- code

```html
<code>var x = 1;</code>
```

5. personal portfolio

# Roadmap

https://roadmap.sh/frontend

skip optional at present and maybe skip some history things.

## Internet

a global network of computers connected to each other which communicate through a standardized set of protocols.

### Where is the Internet

- The last mile: connects homes and small businesses to the internet.

- Data centers: rooms full of servers that store user data and host online apps and content.

- The backbone: consists of long-distance networks — mostly on fiber optic cables — that carry data between data centers and consumers.

### Decentralized network

No one runs the internet. It’s organized as a decentralized network of networks. Thousands of companies, universities, governments, and other entities operate their own networks and exchange traffic with each other based on voluntary interconnection agreements.

### IP Address

Internet Protocol addresses are numbers that computers use to identify each other on the internet.

IPv6: new standard for addresses.

### wireless internet

- Wifi networks use unlicensed spectrum: electromagnetic frequencies that are available for anyone to use without charge. To prevent neighbors’ networks from interfering with each other, there are strict limits on the power (and therefore the range) of wifi networks.

- Cellular networks are more centralized. They work by breaking up the service territory into cells. Each cell has a tower at its center providing services to devices there. Cells are too large to use the unlicensed, low-power spectrum used by wifi networks. Instead, cellular networks use spectrum licensed for their exclusive use.

### Packet

A packet is the basic unit of information transmitted over the internet. Splitting information up into small, digestible pieces allows the network’s capacity to be used more efficiently.

- header: information that helps the packet get to its destination, including the length of the packet, its source and destination, and a checksum value that helps the recipient detect if a packet was damaged in transit.

- data: contain up to 64 kilobytes of data.

If internet routers experience congestion or other technical problems, they are allowed to deal with it by simply discarding packets. It’s the sending computer’s responsibility to detect that a packet didn’t reach its destination and send another copy.

### Web

- The World Wide Web is a popular way to publish information on the internet.

- A web browser is a computer program that allows users to download and view websites.

### SSL

SSL, short for Secure Sockets Layer, is a family of encryption technologies that allows web users to protect the privacy of information they transmit over the internet.

That lock beside URL is supposed to signal that third parties won't be able to read any information you send or receive. Under the hood, SSL accomplishes that by transforming your data into a coded message that only the recipient knows how to decipher.

### DNS

The Domain Name System (DNS) is the reason you can access Vox by typing vox.com into your browser rather than a hard-to-remember numeric address such as 216.146.46.10.

The system is hierarchical. For example, the .com domain is administered by a company called Verisign. Verisign assigns sub-domains like google.com and vox.com. Owners of these second-level domains, in turn, can create sub-domains such as mail.google.com and maps.google.com.

The domain name system is administered by the Internet Corporation for Assigned Names and Numbers (ICANN), a non-profit organization based in California.

- generic top-level domains (gTLDs) such as .com, .edu, .org, and .gov. 

- country-code top-level domains (ccTLDs). Each country in the world has its own 2-letter code. For example, the ccTLD for the United States is .us, Great Britain’s is .uk, and China’s is .cn. These domains are administered by authorities in each country. 

### How does the Internet work

If you connect to the Internet through an Internet Service Provider (ISP), you are usually assigned a temporary IP address for the duration of your dial-in session. If you connect to the Internet from a local area network (LAN) your computer might have a permanent IP address or it might obtain a temporary one from a DHCP (Dynamic Host Configuration Protocol) server. In any case, if you are connected to the Internet, your computer has a unique IP address.

- The Ping Program: to see if a computer on the Internet is alive. ping www.yahoo.com. The ping program will send a 'ping' (actually an ICMP (Internet Control Message Protocol) echo request message) to the named computer. The pinged computer will respond with a reply. The ping program will count the time expired until the reply comes back (if it does). Also, if you enter a domain name (i.e. www.yahoo.com) instead of an IP address, ping will resolve the domain name and display the computer's IP address.

- protocol stack: Every computer needs one to communicate on the Internet and it is usually built into the computer's operating system. The protocol stack used on the Internet is refered to as the TCP/IP protocol stack because of the two major communication protocols used. The TCP/IP stack looks like this:  
  
  | Protocol Layer                      | Comments                                                                                                              |
  | ----------------------------------- | --------------------------------------------------------------------------------------------------------------------- |
  | Application Protocols Layer         | Protocols specific to applications such as WWW, e-mail, FTP, etc.                                                     |
  | Transmission Control Protocol Layer | TCP directs packets to a specific application on a computer using a port number.                                      |
  | Internet Protocol Layer             | IP directs packets to a specific computer using an IP address.                                                        |
  | Hardware Layer                      | Converts binary packet data to network signals and back.<br>(E.g. ethernet network card, modem for phone lines, etc.) |
  
  ![Screen Shot 2021-12-28 at 23.02.04.png](https://raw.githubusercontent.com/yxshi610/images/main/2021/12/28-23-02-09-Screen%20Shot%202021-12-28%20at%2023.02.04.png)
  
  If the message to be sent is long, each stack layer that the message passes through may break the message up into smaller chunks of data. This is because data sent over the Internet (and most computer networks) are sent in manageable chunks. On the Internet, these chunks of data are known as **packets**.
  
  The packets would go through the Application Layer and continue to the TCP layer. Each packet is assigned a **port number**. We need to know which program on the destination computer needs to receive the message because it will be listening on a specific port.
  
  After going through the TCP layer, the packets proceed to the IP layer. This is where each packet receives it's destination address, 5.6.7.8.
  
  The hardware layer takes care of turning our packets containing the alphabetic text of our message into electronic signals and transmitting them over the phone line.
  
  On the other end of the phone line your ISP has a direct connection to the Internet. The ISPs **router** examines the destination address in each packet and determines where to send it. Often, the packet's next stop is another router.
  
  go up and stipe headers and re-assembled.

#### Networking Infrastructure

![](http://web.stanford.edu/class/msande91si/www-spr04/readings/week1/InternetWhitepaper_files/ruswp_diag3.gif)

The ISP maintains a pool of modems for their dial-in customers. This is managed by some form of computer (usually a dedicated one) which controls data flow from the modem pool to a backbone or dedicated line router. This setup may be referred to as a port server, as it 'serves' access to the network. Billing and usage information is usually collected here as well.

After your packets traverse the phone network and your ISP's local equipment, they are routed onto the ISP's backbone or a backbone the ISP buys bandwidth from. 

**traceroute** and it shows the path your packets are taking to a given Internet destination. Like ping, you must use traceroute from a command prompt. type `traceroute www.yahoo.com`. will print out a list of all the routers, computers, and any other Internet entities that your packets must travel through to get to their destination.

#### Internet Infrastructure

The Internet backbone is made up of many large networks which interconnect with each other. These large networks are known as **Network Service Providers** or **NSP**s. These networks **peer** with each other to exchange packet traffic. Each NSP is required to connect to three **Network Access Points** or **NAP**s. At the NAPs, packet traffic may jump from one NSP's backbone to another NSP's backbone. NSPs also interconnect at **Metropolitan Area Exchanges** or **MAE**s. MAEs serve the same purpose as the NAPs but are privately owned. Both NAPs and MAEs are referred to as Internet Exchange Points or **IX**s. NSPs also sell bandwidth to smaller networks, such as ISPs and smaller bandwidth providers. 

![](http://web.stanford.edu/class/msande91si/www-spr04/readings/week1/InternetWhitepaper_files/ruswp_diag4.gif)

#### Routing

**Routers are packet switches.** A router is usually connected between networks to route packets between them. Each router knows about it's sub-networks and which IP addresses they use. The router usually doesn't know what IP addresses are 'above' it.

![](http://web.stanford.edu/class/msande91si/www-spr04/readings/week1/InternetWhitepaper_files/ruswp_diag5.gif)

When a packet arrives at a router, the router examines the IP address put there by the IP protocol layer on the originating computer. The router checks it's routing table. If the network containing the IP address is found, the packet is sent to that network. If the network containing the IP address is not found, then the router sends the packet on a default route, usually up the backbone hierarchy to the next router. Hopefully the next router will know where to send the packet. If it does not, again the packet is routed upwards until it reaches a NSP backbone. The routers connected to the NSP backbones hold the largest routing tables and here the packet will be routed to the correct backbone, where it will begin its journey 'downward' through smaller and smaller networks until it finds it's destination.

#### Domain Name Service or DNS

The DNS is a **distributed**** database which keeps track of computer's names and their corresponding IP addresses on the Internet.

![](http://web.stanford.edu/class/msande91si/www-spr04/readings/week1/InternetWhitepaper_files/ruswp_diag6.gif)

The Domain Name Service is structured as a hierarchy similar to the IP routing hierarchy. The computer requesting a name resolution will be re-directed 'up' the hierarchy until a DNS server is found that can resolve the domain name in the request. 

When an Internet connection is setup (e.g. for a LAN or Dial-Up Networking in Windows), one primary and one or more secondary DNS servers are usually specified as part of the installation. This way, any Internet applications that need domain name resolution will be able to function correctly. For example, when you enter a web address into your web browser, the browser first connects to your primary DNS server. After obtaining the IP address for the domain name you entered, the browser then connects to the target computer and requests the web page you wanted.

#### Internet Protocols

- Application Protocols: HTTP and the World Wide Web
  
  One of the most commonly used services on the Internet is the World Wide Web (WWW). The application protocol that makes the web work is **Hypertext Transfer Protocol** or **HTTP**. is used by specific applications to talk to one another. In this case the applications are web browsers and web servers.
  
  HTTP is a connectionless text based protocol. Clients (web browsers) send requests to web servers for web elements such as web pages and images. After the request is serviced by a server, the connection between client and server across the Internet is disconnected. A new connection must be made for each request. Most protocols are connection oriented. 
  
  When you type a URL into a web browser:
  
  1. If the URL contains a domain name, the browser first connects to a domain name server and retrieves the corresponding IP address for the web server.
  2. The web browser connects to the web server and sends an HTTP request (via the protocol stack) for the desired web page.
  3. The web server receives the request and checks for the desired page. If the page exists, the web server sends it. If the server cannot find the requested page, it will send an HTTP 404 error message. (404 means 'Page Not Found' as anyone who has surfed the web probably knows.)
  4. The web browser receives the page back and the connection is closed.
  5. The browser then parses through the page and looks for other page elements it needs to complete the web page. These usually include images, applets, etc.
  6. For each element needed, the browser makes additional connections and HTTP requests to the server for each element.
  7. When the browser has finished loading all images, applets, etc. the page will be completely loaded in the browser window.

































# React

## Deploying to GitHub Pages

```shell
npx create-react-app app-name
cd app-name
npm install gh-pages --save-dev
```

`package.json` file:

- At the top level, add a `homepage` property: 

```js
//... same level with name and vesion
"homepage": "http://{username}.github.io/{repo-name}"
```

- add a `predeploy` property and a `deploy` property, each having the values shown below:

```js
"scripts": {
 //...
 "predeploy": "npm run build",
 "deploy": "gh-pages -d build"
}
```

```shell
git init
git remote add origin https://github.com/yxshi610/characters.git
npm run deploy    // accessible through URL
```

- optionally commit to "master" branch

```shell
git add .
git commit -m "Create a React app and publish it to GitHub Pages"
git push origin master
```

the `master` branch held the source code, and the `gh-pages` branch held the *built* app code.

Problem: GitHub Pages doesn't natively support single page apps. When there is a fresh page load for a url like `example.tld/foo`, where `/foo` is a frontend route, the GitHub Pages server returns 404 because it knows nothing of `/foo`.

Solution: https://github.com/rafgraph/spa-github-pages

change to Surge: 

```shell
npm run build
cd build
cp index.html 200.html
surge
```

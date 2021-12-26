# Responsive Web Design

## Basic HTML and HTML5

https://www.freecodecamp.org/learn/responsive-web-design/

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

![Screen Shot 2021-12-25 at 22.33.47.png](/var/folders/y6/ttkvjskx6778fclb29vmw7qw0000gn/T/TemporaryItems/NSIRD_screencaptureui_7ybVuv/Screen%20Shot%202021-12-25%20at%2022.33.47.png)

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

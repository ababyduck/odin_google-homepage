# google-homepage

This repo is my approach to an assignment from [The Odin Project](http://www.theodinproject.com/courses/web-development-101/lessons/html-css). The goal is to use HTML and CSS to recreate the general look and feel of Google's home and search results pages, ideally without directly examining their source code.

## What I learned

### CSS positioning techniques

- Vertical centering of the "main" content is achieved through absolute positioning and translation.
- Top and bottom bars are placed by giving them `position: fixed` and definining the `top` and/or `bottom` properties. [Further reference here](https://www.w3schools.com/css/css_positioning.asp)
- Top and bottom bar links are written as unordered lists and floated to the left and right, allowing links on both sides of the bar.

### Fontawesome is a lot less awesome now.

Apparently the fontawesome CDN now requires even free users to register an account. In other words, they now require your email in order to [collect, store, and share your data.](https://fontawesome.com/privacy) Merely annoying for projects like this, but in production this may be an argument in favor of self-hosting any necessary glyph fonts.

### `box-shadow` can have unintended results on elements scaled with `transform`.

After applying `transform: translate()` to the div containing the search bar, the `box-shadow` on the text input had an unintended single-pixel gap between the element itself and its shadow. In other words, the shadow was drawn in the wrong position. This was resolved *only on some displays* by [modifying the size of the input itself](ababyduck/odin_google-homepage@34b84f2).

### Image mapping

When I tried to grab the image link for the "Goooooooooogle" nav I quickly realized that Google uses an interesting technique here. Rather than having multiple images for each letter, they use a single image with all logos and UI elements and just map the positions of the parts they want to use, similar to spritesheets in a 2D video game. While this approach is a little less intuitive to set up, it's more maintainable in that updating that image is all that's needed to completely reskin the site's image elements.

### Scalable Vector Graphics as inline code

Google uses SVG paths defined directly in the html code to achieve their glyph icons. Copying those felt like cheating, so I used FontAwesome instead, but it's definitely a nice feature to have.

### Weird inconsistencies with vertical alignment

Images don't respect the `vertical-align` property of their parent div, and must instead have their own `vertical-align` defined.

# CSS Radiant Glow

This project demonstrates a CSS radiant glow effect on cards that respond to mouse movements.

## Files

- `index.html`: The main HTML file that includes the structure of the webpage.
- `style.css`: The CSS file that contains styles for the cards and the radiant glow effect.
- `script.js`: The JavaScript file that handles the mouse movement events to update the glow effect.
- `README.md`: This file.

## implementations
### Structure the layout using HTML

First of all links to our CSS stylesheet named "styles.css" to the HTML document.

Here, I have created 3 times, `<div>` elements with the class "card" representing a card element with a title (`<h1>`) and a description (`<p>`). Additionally, cards contain another child `<div>` element with the class "glow", which will be the container for the glowing border effect.

### Styling with CSS
Make sure you have linked your CSS file to the HTML document.

In CSS first of all I have imported fonts from Google Fonts . Then reset the default margin, padding and box-sizing properties.

Here, as you can see, I have created the CSS variable called --gradient defines a conic gradient  with multiple colour stops, which will be used with the background property as gradient border & glow later in the code.

Then applied styles to the body, (`<h1>`) and description (`<p>`) elements.

### How to create gradient border in CSS
In this project, the main part is to add a Gradient border to .card elements using CSS. We will use conic-gradient() CSS function  and mask property  to add a Gradient border to .card elements.

So, first of all, I have added some styles to the .card elements, like display to flex, flex-direction to the column, content alignments, width, height, margin, padding, border-radius, transition, etc.

You can notice here I have created a --start custom property (CSS variable), defined to control the starting angle of the conic gradient. Its initial value is ‘0’, which will change dynamically through JavaScript.

Then I added styles to the card’s Pseudo-element to create the Gradient Border Glowing Animation around the .card elements. I have set its height & width to 100%, and border width to “2px” but it’s colour to transparent.

Then I specified .card::before background property to gradient by the --gradient variable, setting the background-attachment property to fixed.

Then the main part comes, where I have used the mask property  to define a combination of linear and conical gradients. By this masking technique, we have achieved a gradient effect that emanates from the border of the .card elements.

```
mask: linear-gradient(#0000, #0000), conic-gradient(from calc((
            var(--start) - (20 * 1.1)
          ) * 1deg), #ffffff1f 0deg, white, #ffffff00 100deg);
```
Then I set the mask-composite property  to intersect, for a precise intersection of the two gradient layers. Additionally, I specified the mask-clip property to padding-box & border-box.

```
.card::before {
  mask-composite: intersect;
  mask-clip: padding-box, border-box;
}
```
Also, I set the card’s Pseudo-element opacity to 0 by default and added a transition.


### Adding animation functionality with JavaScript
We have so far designed the card gradient border glowing animation project using CSS.

Now it is time to enable the functionality using JavaScript that tracks the movement of the mouse cursor over the .card elements and runs the animation accordingly by updating the --start CSS variable.

So let’s break down the javascript code, First of all, I have created a variable called cards, which stores all the .card elements by using `document.querySelectorAll()` method.

Then I have added an event listener for the mousemove event on each .card element using the `forEach()` method and this will trigger the handleMouseMove function. It means when the user moves the mouse over .card elements handleMouseMove function will be triggered.

## Usage

1. Open `index.html` in a web browser.
2. Move your mouse cursor over the cards to see the radiant glow effect.

## Dependencies

- Google Fonts: Inter and Poppins

## License

This project is licensed under the MIT License.
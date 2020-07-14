---
title: Getting started with Google Fonts
date: '2020-07-14T09:06:00.000Z'
description: 'Give your Website a fresh look using Google Web Fonts'
---

The font you choose for your website can really make or break your design. One of the best resources for free licensed font families is [Google Fonts](https://fonts.google.com/). Currently they have 993 fonts that you can add to your sites or web apps in just a few minutes.

![Fonts Home](./fonts-home.png 'Google Fonts Home')

Once you choose a font you like we can go about adding it to your site. For the rest of this tutorial I'm going to use a personal favourite of mine, [Merriweather](https://fonts.google.com/specimen/Merriweather).

On a fonts specimen page you can see how each individual character will be rendered as well as pick from different styles of that font. For Merriweather we can see this includes mainly font weights ranging from 300 - 900 and also some italic variations of these weights.

![Merriweather Styles](./style.png 'Merriweather Styles')

![Merriweather Glyphs](./glyph.png 'Merriweather Glyphs')

Another useful part of this page is right down the bottom, the pairings section. Here we can see other fonts that are often paired with Merriweather on the Web. As well as a preview of both being used in a realistic scenario.

![Merriweather Pairings](./pairing.png 'Merriweather Popular Pairings')

So how do we add this font to our website? Well It's actually very simple, scroll back to the top of the page and select the styles you want. As you select them you'll see them appear on the selected family pane on the right.

![Selected Pane](./selected.png 'Selected Pane')

Once you've picked the styles you want click on the **embed** heading within the selected family pane and you'll get instructions on how to add it.

![Selected Pane Embed](./embed.png 'Selected Pane Embed')

So to add the fonts I've selected here I just need to add this `link` tag to my html:

```html
<link
  href="https://fonts.googleapis.com/css2?family=Merriweather:wght@400;700&display=swap"
  rel="stylesheet"
/>
```

<br/>

And then use this CSS to specify the font:

```css
font-family: 'Merriweather', serif;
```

<br/>

You can see from the CSS that we've defined a fallback font **serif**, this will be the font used if we fail to fetch Merriweather from Google Fonts.

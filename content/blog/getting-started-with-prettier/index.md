---
title: Getting started with Prettier in VSCode
date: '2020-07-11T11:06:00.000Z'
description: 'Consistent, easy and automatic code formatting for you and your team'
---

Formatting your code is an issue as old as programming itself, but modern developer tooling has been making big strides toward addressing it.

Prettier is an opinionated code formatter that supports many languages and integrates with most editors. It's really made development a hell of a lot easier, so much so it's one of the first things I reach for when starting a new project.

In this tutorial I'm going to go over getting started with Prettier in VSCode so if you don't have VSCode already you'll need to install it first. You can download it [here](https://code.visualstudio.com/).

Next you'll need to install the extension. Search for `Prettier - Code Formatter` in the extension panel and hit `install`.

Here's a little bit of sample code that you can try to format using Prettier:

```javascript
```

<br/>

With the extension installed you can now format the document from the command palette, to pull it up hit `CTRL + SHIFT + P`. Search for format and select `Format Document`. You should notice a change in your code, it will now be formatted to have consistent spacing, line wrapping and quotes.

This is a big improvement but what if we want to be able to format our document automatically? Well we can modify our `settings.json` to make that happen. Open up the command palette again, search for settings and select `Preferences: Open Settings (JSON)`.

"editor.formatOnSave": true,

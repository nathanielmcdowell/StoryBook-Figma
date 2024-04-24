# Guide to StoryBoook Figma Integration: 

  This guide will demonstrate how to link figma **components** into storybook stories, allowing for easy cross referencing between designs and development.



## @storybook/addon-designs

A [Storybook](https://github.com/storybooks/storybook) addon that embed Figma or websites in the addon panel for better design-development workflow.

- [Docs & Demo](https://storybookjs.github.io/addon-designs)

## Requirements

- Storybook@>=8.0.0 (Version 7 of this addon supports Storybook 7)

This addon should work well with any framework. If you find that the addon does not work, please open an issue.

## Getting started

### 1. Install

```sh
npm install -D @storybook/addon-designs

yarn add -D @storybook/addon-designs

pnpm add -D @storybook/addon-designs
```

### 2. Register the addon in `main.js`

```js
export default {
  addons: ["@storybook/addon-designs"],
};
```

### 3. Add it to story!

```js
export default {
  title: "My stories",
  component: Button,
};

export const myStory = {
  parameters: {
    design: {
      type: "figma",
      url: "https://www.figma.com/file/LKQ4FJ4bTnCSjedbRpk931/Sample-File",
    },
  },
};
```

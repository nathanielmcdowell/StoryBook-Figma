# Guide to StoryBoook Figma Integration: 

  This guide will demonstrate how to link figma **components** into storybook stories, allowing for easy cross referencing between designs and development.

## Requirements

- Storybook@>=8.0.0 (Version 7 of this addon supports Storybook 7)

This addon should work well with any framework. If you find that the addon does not work, please open an issue.

## Setting up Storybook

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

## Linking Figma Components

### 1. Copy link to page, component, or variant

  #### a. Linking to components and variants. 
  Navigate to the desired selection and right click, select option ```Copy/Paste as``` -> ```Copy link to selection```. 
  ![Screenshot 2024-04-24 at 9 22 23 AM](https://github.com/nathanielmcdowell/notes1/assets/142334567/ef75ee79-29d7-46b6-b0d0-d1ea72d0c0f1)
  #### b. Linking pages 
  Copy the link from the search bar. 
  
### 2. Add it to story!

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

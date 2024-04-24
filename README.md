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
Paste the link in the ```url``` section.
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

#### Setting up permissions for access

### 1. Obtaining Access Token
Go to the home page in figma and click your account icon in the top left. In the dropdown select ```Settings```. Within the setteings menu, scroll down and you should see a section titled ```Personal Access Token```. Within this section, click the link ```Generate New Token```. <br>
![Screenshot 2024-04-24 at 10 27 33 AM](https://github.com/nathanielmcdowell/notes1/assets/142334567/d60a0999-6982-4762-a7e7-d3dc78be3d7c)![Screenshot 2024-04-24 at 9 21 49 AM](https://github.com/nathanielmcdowell/notes1/assets/142334567/5952d28a-0d9a-4780-b609-c1fd37d6109a)

### 2. Embedding Access
#### a. Add the token as a Enviroment variable
Create a ```.env``` file within your storybook directory, assign the token to a variable i.e ```STORYBOOK_FIGMA_ACCESS_TOKEN = figd_abcdefghijklmnopqrstuv1234567890```. 
#### b. Link token within the story
add ```accessToken: process.env.STORYBOOK_FIGMA_ACCESS_TOKEN``` under the ```url`` link to the figma selection. Your file should look like this. 
```js
const meta = {
  title: 'Example/Button',
  component: Button,
  parameters: {
    // Optional parameter to center the component in the Canvas. More info: https://storybook.js.org/docs/configure/story-layout
    layout: 'centered',
  design: {
     type: "figspec",
     url: "https://www.figma.com/file/JSBkHssvnSRXqFsKhXtNZS/Component-Library?type=design&node-id=164-420&mode=dev",
     accessToken: process.env.STORYBOOK_FIGMA_ACCESS_TOKEN
    },
  },
```




---
title: "5 Good practices to scale your React projects easily"
date: 2022-06-28T10:13:16+08:00
draft: true
---

For most React developers, it's easy to just get our hands on writting new lines of code. However, we sometimes missed keeping them organized and planned for future use as the project scales.

Having a plan for scaling can help you:

Reuse and reduce development time
Organize project and prevent project reconstructions
Show you are good developer by taking consideration of the project and other devs :)
Here are 5 lessons I learned from scaling my React projects. They help me to plan ahead for my projects while writting pretty React code.

1. Always start with state management
When a project was small, I jumped right into writing state for individual components. However, it got messy when I wanted to sync up states for several components and tried to to use props and callback functions.

Always start with a state mangement tool, whether it's Redux, Recoil, or context and hooks. Even if a project is small, you'll need Authenticaiton and Alert to be managed globally.

React state managment

Besides, state management seperates logic from components. When handling backend calls, it serves like a controller/service layer between UI and database. State and actions in this layer can be reused across many components.

A tip here is always track waiting status for backend calls for conditional component rendering. It saves you from unnecessary errors and a nice loading spinner shown to the user.

2. Make your own component library
I found that even when I'm using a UI library like Material UI, I still need customization on props, logics, and styles for my project.

Create a custom components library allowed me to reuse them across pages and even exported to other projects.

Include styles, tests, types, and Storybook templates (recommended) for each custom component. A good practice is to organize the library in atomic design like the following.
custom-components
├── atoms
│   └── CustomButton
│       ├── CustomButton.tsx
│       ├── CustomButton.types.tsx
│       ├── CustomButton.styles.tsx  
│       ├── CustomButton.test.tsx
│       ├── CustomButton.stories.tsx
│       └── index.tsx
├── molecules
│   └── CustomDialog
└── organizations
    └── CustomTable
3. Define types
As we know, JavaScript is dynamic-typed language. When a project scales, props passed across components and functions increases.

If there is no type checking, many unnecessary errors involving edge cases like null and undefined could happen. Define types also increase readibility of code.

It's better to start with or migrate to TypeScript if possible, but define PropTypes also works.

4. Use global AND specific styles
Styling is always a big headache for frontend devs. We have to handle both unified styles and individual styles.

CSS meme

If a project has UI design provided like Figma, try to define styles in global theme first. It's better to define them in the theme provider of a UI library to easily make customization on defined palettes. The theme provider also handles light & dark themes for you.

For styles of individual components, try to include them in custom components library mentioned above. If they are specific to one component, include them in a styles file under that component.

The rule of thumb is to include styles at the top level needed for reuse.

5. Sync pages folder with routes
Previously, I made pages and components folders quite a mess, keeping two in only either one folder.

Then I learned that it's better to organize the pages folder in sync with the routes. This increases readability for other devs to understand the website structure, like the following.
pages
├── events
│   ├── index.tsx
│   └── event
│       ├── index.tsx
└── user
    └── index.tsx
events correspondes to /events, and event correspondes to /events/:id.

I'm having the same structure for the components folder to correspond components to a page where they are used. But you can also have a /components folder under each page, and make the components folder for other use.

These are my good practices on planning a React project for scale, and everyone has their own way. The two rules of thumb to conclude these good practices are:

1. Seperate & Reuse
2. Organize for readability

Happy coding! 🚀

---
layout: post
title:  "Tailwind CSS with React"
date:   2020-03-31 09:09:16 +0530
categories: react tailwindCSS
---
Tailwind CSS is a highly customizable, low-level CSS framework. It provides low-level utility classes tto  build completely custom designs without ever leaving your HTML.  Here we can check on how to integrate Tailwind CSS with React

To use Tailwind CSS with React, first we can create a react app with the following command

```shell
$ npx create-react-app react-tailwindcss
```

The above command create a basic react app.  Change directory to  react-tailwindcss

```shell
$ cd react-tailwindcss
```

 Then we do install Tailwind CSS as dev dependency

```shell
$ yarn add tailwindcss --dev
```

After installing we need to create Tailwind CSS configuration file. For that we have to run the following command

```shell
$ ./node_modules/.bin/tailwind init tailwind.js
```

The above command generate following output



![](/assets/images/03_20/Screenshot_2020-03-31_12_18_45.png)



After that create a Tailwind CSS Source file, ` /src/css/tailwind.src.css ` and write Tailwind directives

```css
@tailwind base;
@tailwind components;
@tailwind utilities;
```

Next step is to add custom script in `package.json` file. We can call it as `tailwind:css`

```json
"scripts": {
  "tailwind:css":"tailwind build src/css/tailwind.src.css -c  tailwind.js -o src/css/tailwind.css",
  "start": "npm run tailwind:css && react-scripts start",
  "build": "npm run tailwind:css && react-scripts build"
}
```

This script will create `src/css/tailwind.css` file from `src/css/tailwind.src.css`

> Note:  Prepend **start** and **build** scripts with `tailwind:css` script.



Now you can run `yarn start`  to start the React server, this will open React dev server at `http://localhost:3000` and will generate ` tailwind.css` file in `src/css/` .

![](/assets/images/03_20/Screenshot_2020-03-31_12_18_42.png)


The Tailwind successfully generated `tailwind.css ` file. We have to import `tailwind.css` in the `src/index.js` file.

```javascript
...
import './index.css';
import './css/tailwind.css';
...
```

It's the time to use some CSS class from Tailwind in our React application

```javascript
import React from 'react';
import logo from './logo.svg';
import './App.css';

function App() {
  return (
    <div>
      <h1 className="text-center bg-blue-400">
        Hello World!
      </h1>
    </div>
  );
}

export default App;
```

Source code of the demo application is avaiable in Github [Repository]( https://github.com/sumith68/react-tailwindcss)


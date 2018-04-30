# Setup Storybook
## References
[Storybook - Development tool for working on UI in different states](https://storybook.js.org/)

## Add Storybook to the application

```
npm i -g @storybook/cli
getstorybook
yarn storybook
# note: you can quit storybook with ^C
```

Create file **src/Movies.js** with the following contents

``` 
import React from "react";

export const Movies = () => {
  return <div>Hello React!</div>;
};
```

Modify **src/index.js** 
```diff
import React from "react";
import ReactDOM from "react-dom";

+ import { Movies } from './Movies';

- const Index = () => {
-   return <div>Hello React!</div>;
- };

+ ReactDOM.render(<Movies />, document.getElementById("index"));
- ReactDOM.render(<Index />, document.getElementById("index"));
```

Replace the contents of **stories/index.stories.js**
```
import React from 'react';
import { storiesOf } from '@storybook/react';

import { Movies } from '../src/Movies';

storiesOf('Movies', module)
  .add('storybook', () => <Movies/>);
```

Run storybook again to watch changes
``` 
yarn storybook
```

Modify Hello React! to Hello (your name) in **src/Movies.js** and watch storybook in browser
```diff
import React from "react";

export const Movies = () => {
-   return <div>Hello React!</div>;
+   return <div>Hello Jeff!</div>;
};
```

Watch browser where storybook is running

## Turn app into a component
Update **src/Movies.js**

```diff
import React from "react";

- export const Movies = () => {
-  return <div>Hello React!</div>;
- };

+ export class Movies extends React.Component {
+  constructor(props) {
+    super(props);
+  }
+
+  render() {
+    return (<div>Hello Jeff!!</div>);
+  }
+ }
```

[Proceed to Step 4 - Add Internationalization support](setup-i18n.md)

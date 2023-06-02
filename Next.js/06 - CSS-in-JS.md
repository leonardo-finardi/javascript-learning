## CSS Modules

Step 1: Create a CSS module file
Create a CSS module file with a .module.css extension, such as styles.module.css. Define your CSS rules in this file.

```css
/* styles.module.css */
.container {
  background-color: #f1f1f1;
  padding: 20px;
}

.title {
  font-size: 24px;
  color: #333;
}

```

Step 2: Import and use the CSS module

Import the CSS module into your component and assign it to a variable. Use the class names from the imported CSS module in your JSX elements.

```javascript
import styles from './styles.module.css';

const MyComponent = () => (
  <div className={styles.container}>
    <h1 className={styles.title}>Hello, CSS Modules!</h1>
    <p>This is a paragraph with CSS Modules styling.</p>
  </div>
);

export default MyComponent;


```

## styled-components

Step 1: Install styled-components
Install the styled-components library using npm or yarn.

```bash
npm install styled-components
```

Step 2: Define a styled component
Create a new file (e.g., Button.js) and import the necessary dependencies.

```javascript
import styled from 'styled-components';

const Button = styled.button`
  background-color: #f1f1f1;
  color: #333;
  padding: 10px 20px;
  border: none;
  cursor: pointer;
`;

export default Button;

```

Step 3: Use the styled component
Import the styled component and use it in your application.

```javascript
import Button from './Button';

const MyComponent = () => (
  <div>
    <h1>Hello, styled-components!</h1>
    <Button>Click me</Button>
  </div>
);

export default MyComponent;

```

These examples provide a basic understanding of how to use CSS-in-JS in Next.js with CSS Modules and styled-components. Remember to install the necessary dependencies and adjust the styles according to your requirements. Feel free to explore more advanced features and options offered by CSS-in-JS libraries as you delve deeper into your Next.js development journey.
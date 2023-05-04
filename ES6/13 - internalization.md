Internationalization, often abbreviated as i18n, is the process of adapting software to work in multiple languages and cultures. In ES6, the Intl object was introduced to provide a standardized way to perform internationalization in JavaScript.

The Intl object provides built-in objects for formatting dates, times, and numbers, as well as collation and comparison of strings in different languages and cultures. Here are some examples of how to use Intl:

Date formatting:

```javascript
const date = new Date();

const options = { 
  year: 'numeric', 
  month: 'long', 
  day: 'numeric' 
};

console.log(new Intl.DateTimeFormat('en-US', options).format(date));
// Output: "May 3, 2023"
console.log(new Intl.DateTimeFormat('fr-FR', options).format(date));
// Output: "3 mai 2023"
```

In this example, we're creating a new Date object and an options object to define the formatting options. We're then using Intl.DateTimeFormat to format the date in different languages and locales.

Number formatting:

```javascript
const number = 123456.789;

console.log(new Intl.NumberFormat('en-US').format(number));
// Output: "123,456.789"
console.log(new Intl.NumberFormat('de-DE').format(number));
// Output: "123.456,789"

```

In this example, we're using Intl.NumberFormat to format a number in different languages and locales.

String comparison:

```javascript
const strings = ['é', 'è', 'ê', 'a'];

console.log(strings.sort(new Intl.Collator('fr-FR').compare));
// Output: ["a", "è", "é", "ê"]
console.log(strings.sort(new Intl.Collator('en-US').compare));
// Output: ["a", "é", "è", "ê"]
```

In this example, we're using Intl.Collator to compare and sort an array of strings in different languages and locales.

These are just a few examples of how to use Intl to perform internationalization in JavaScript. The Intl object provides many other options and methods for working with dates, times, numbers, and strings in different languages and cultures.
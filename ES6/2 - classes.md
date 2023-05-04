Classes in ES6 are a new way to define and create objects in JavaScript. They provide a more convenient and structured way to write object-oriented code.

The class syntax in ES6 is built on top of the prototype-based model that JavaScript has always had. Here's an example of how to define a class in ES6:

```javascript
class Person {
  constructor(name, age) {
    this.name = name;
    this.age = age;
  }
  
  sayHello() {
    console.log(`Hello, my name is ${this.name} and I'm ${this.age} years old.`);
  }
}
```

In this example, we define a Person class with a constructor function that sets the name and age properties of a Person instance. We also define a sayHello method that logs a greeting to the console.

To create a new instance of the Person class, we can use the new keyword:

```javascript
const john = new Person('John', 25);
john.sayHello(); // logs "Hello, my name is John and I'm 25 years old."
```

Classes can also inherit from other classes using the extends keyword. Here's an example:

```javascript
class Student extends Person {
  constructor(name, age, grade) {
    super(name, age);
    this.grade = grade;
  }
  
  sayHello() {
    console.log(`Hello, my name is ${this.name}, I'm ${this.age} years old, and I'm in grade ${this.grade}.`);
  }
}

const jane = new Student('Jane', 16, 11);
jane.sayHello(); // logs "Hello, my name is Jane, I'm 16 years old, and I'm in grade 11."
```

In this example, we define a Student class that extends the Person class. We call the super function in the Student constructor to call the Person constructor and set the name and age properties. We also define a sayHello method for the Student class that includes the grade property.

Overall, classes in ES6 provide a more structured and familiar way to write object-oriented code in JavaScript. They allow for inheritance, encapsulation, and polymorphism, making it easier to write and maintain complex applications.
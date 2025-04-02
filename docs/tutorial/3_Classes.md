# JavaScript Classes

Classes in JavaScript are templates for creating objects. They encapsulate data and behavior into a single unit, making it easier to create multiple objects with the same structure and functionality. Classes provide a cleaner and more organized way to create objects compared to other methods.

## Constructor

The constructor is a special method that gets called when creating a new instance of a class. It's used to initialize object properties.

```javascript
class Person {
  constructor(name, age) {
    this.name = name;
    this.age = age;
  }
}
```

## The `this` Keyword

The `this` keyword refers to the current instance of the class (the object that gets created using the template). It's used to access and modify instance properties and methods.

```javascript
class Person {
  constructor(name) {
    this.name = name;
  }

  sayHello() {
    console.log(`Hello, my name is ${this.name}`);
  }
}
```

## Creating Instances

To create a new instance of a class, use the `new` keyword followed by the class name and any arguments for the constructor.

```javascript
const person = new Person("Chaim", 30);
console.log(person.name); // prints "Chaim"
person.sayHello(); // prints "Hello, my name is Chaim"
```

## Getters and Setters

Getters and setters are special methods that allow you to define how properties are accessed and modified.

### Getters

Getters are used to retrieve property values. They are defined using the `get` keyword.

```javascript
class Person {
  constructor(firstName, lastName) {
    this.firstName = firstName;
    this.lastName = lastName;
  }

  get fullName() {
    return `${this.firstName} ${this.lastName}`;
  }
}

const person = new Person("Yakov", "Weiss");
console.log(person.fullName); // prints "Yakov Weiss"
```

### Setters

Setters are used to modify property values. They are defined using the `set` keyword.

```javascript
class Person {
  constructor(age) {
    this._age = age; // Convention: prefix private properties with _
  }

  set age(value) {
    if (value >= 0) {
      this._age = value;
    } else {
      console.log("Age can't be negative");
    }
  }

  get age() {
    return this._age;
  }
}

const person = new Person(22);
person.age; // 22
person.age = 25;
person.age = 30; // will print "Age can't be negative", age will remain 25
```

### Using Getters and Setters

Getters and setters are accessed like regular properties, not methods:

```javascript
const person = new Person("John", "Doe");
console.log(person.fullName); // "John Doe"

const person2 = new Person(25);
person2.age = 30; // Using setter
console.log(person2.age); // 30 (using getter)
```

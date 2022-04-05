N.1

class Rectangle {
  constructor(length, width) {
    this.length = length;
    this.width = width;
  }
  get length() {
    return this._length;
  }
  set length(value) {
    if (value <= 0) {
      alert('Invalid input the value must be above 0');
      return;
    }
    this._length = value;
  }
  get width() {
    return this._width;
  }
  set width(value) {
    if (value <= 0) {
      alert('Invalid input the value must be above 0');
      return;
    }
    this._width = value;
  }
  getArea() {
    return this.length * this.width;
  }
  getPerimeter() {
    return 2 * this.length + 2 * this.width;
  }
  toString() {
    return JSON.stringify(this);
  }
}

N.2

class Employee {
  constructor ({id, firstName, lastName, position, salary, workingHours} = {}) {
    this._id = id;
    this.firstName = firstName;
    this.lastName = lastName;
    this.position = position;
    this.salary = salary;
    this.workingHours = workingHours;
  }
  get id() {
    return this._id;
  } 
  get firstName() {
    return this._firstName;
  }
  set firstName(value) {
    if (value.length < 2) {
      alert('Firstname is too short');
      return;
    }
    this._firstName = value;
  }
  get lastName() {
    return this._lastName;
  }
  set lastName(value) {
    if (value.length < 4) {
      alert('Lastname is too short');
      return;
    }
    this._lastName = value;
  }
  get position() {
    return this._position;
  }
  set position(value) {
    this._position = value;
  }
  get salary() {
    return this._salary;
  }
  set salary(value) {
    if (value < 0) {
      alert('Salery can`t be nagetive namber');
      return;
    }
    this._salary = value;
  }
  get workingHours() {
    return this._workingHours;
  }
  set workingHours(value) {
    if (value < 0) {
      alert('WorkingHours can`t be nagetive namber');
      return;
    }
    this._workingHours = value;
}
  getFullName() {
    return `${this.firstName} ${this.lastName}`;
  }
  getAnnularSalary() {
    return this.salary * 12;
  }
   raiseSalary(percent) {
    if (percent < 0) {
      alert('Percent can`t be nagetive namber');
      return;
   }
     this.salary += this.salary * percent / 100
     return this.salary;
}
  toString() {
    return JSON.stringify(this);
  }
}

N.3

class Author {
  constructor(name, email, gender) {
    this.name = name;
    this.email = email;
    this._gender = gender;
  }
  get name() {
    return this._name;
  }
  set name(value) {
    this._name = value;
  }
  get email() {
    return this._email;
  }
  set email(value) {
    this._email = value;
  }
  get gender() {
    return this._gender;
  }
  toString() {
    return JSON.stringify(this);
  }
}

class Book {
  constructor({title, author, price, quantity} = {}) {
    this.title = title;
    this.author = author;
    this.price = price;
    this.quantity = quantity;
  }
  get title() {
    return this._title;
  }
  set title(value) {
    this._title = value;
  }
  get author() {
    return this._author;
  }
  set author(value) {
    if (!(value instanceof Author)) {
      alert('Invalid author');
      return;
    }
    this._author = value;
  }
  get price() {
    return this._price;
  }
  set price(value) {
    if (value <= 0) {
      alert('The price must be above 0');
      return;
    }
    this._price = value;
  }
  get quantity() {
    return this._quantity;
  }
  set quantity(value) {
    if (value < 0) {
      alert('The quantity must be positiv integer');
      return;
    }
    this._quantity = value;
  }
  getProfit() {
    return this.price * this.quantity;
  }
  toString() {
    return JSON.stringify(this);
  }
}

N.4

class Account {
  constructor(id, name, balance) {
    this._id = id;
    this.name = name;
    this.balance = balance;
  }
  get id() {
    return this._id;
  }
  get name() {
    return this._name;
  }
  set name(value) {
    this._name = value;
  }
  get balance() {
    return this._balance;
  }
  set balance(value) {
    this._balance = value;
  }
  credit(amount) {
    this.balance += amount;
    return this.balance;
  }
  debit(amount) {
    if(amount > this.balance) {
      alert('Amount exceeded balance');
      return 'cancel';
    }
    this.balance -= amount;
    return this.balance;
  }
  transferTo(anotherAccount, amount) {
    if (!(this.debit(amount) === 'cancel')) {
      anotherAccount.credit(amount);
      return this.balance;
    }
  }
  static identifyAccounts(accountFirst, accountSecond) {
    for (let key in accountFirst) {
      if (!(accountSecond.hasOwnProperty(key) && accountFirst[key] === accountSecond[key])){
        alert('Not the same');
        return;
      }
    }
    alert('Same account');
  }
  toString() {
    return JSON.stringify(this);
  }
} 

N.5

class Person {
  constructor (firstName, lastName, gender, age) {
    this._firstName = firstName;
    this._lastName = lastName;
    this._gender = gender;
    this._age = age;
  }
  get firstName() {
    return this._firstName;
  }
  set firstName(value) {
    this._firstName = value;
  }
  get lastName() {
    return this._lastName;
  }
  set lastName(value) {
    this._lastName = value;
  }
  get gender() {
    return this._gender;
  }
  get age() {
    return this._age;
  }
  set age(value) {
    this._age = value;
  }
  toString() {
    return JSON.stringify(this);
  }
}

class Student extends Person {
  constructor (programs, year, fee, ...args) {
    super(...args);
    this._programs = programs;
    this._year = year;
    this._fee = fee;
    this.dataStor = {};
    programs.forEach((item) => this.dataStor[item] = 0);
    
  }
  get programs() {
    return this._programs;
  }
  set programs(value) {
   if (Array.isArray(value)) {
    this._programs = value;
    this.dataStor = {};
    this.programs.forEach((item) => this.dataStor[item] = 0);
    } else {
      alert('Programs should be array');
    }
  }
  get year() {
    return this._year;
  }
  set year(value) {
    this._year = value;
  }
  get fee() {
    return this._fee;
  }
  set fee(value) {
    this._fee = value;
  }

  passExam(program, grade) {
    if (this.programs.includes(program)) {
      this.dataStor[program] = grade;
      if(!Object.entries(this.dataStor).map((item) => item[1] < 50 ? true : false).includes(true)) this.year++;
    }
    }
  
  toString() {
    return JSON.stringify(this);
  }
}
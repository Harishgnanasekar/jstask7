#  JavaScript Practice Tasks 

---

##  SECTION 1 – Date Object Tasks

---

###  TASK 1 – Custom Digital Clock

```javascript
function digitalClock() {
  let now = new Date();

  let hours = now.getHours();
  let minutes = now.getMinutes();
  let seconds = now.getSeconds();

  // Add leading zero
  hours = hours < 10 ? "0" + hours : hours;
  minutes = minutes < 10 ? "0" + minutes : minutes;
  seconds = seconds < 10 ? "0" + seconds : seconds;

  console.log(`Current Time: ${hours} : ${minutes} : ${seconds}`);
}

setInterval(digitalClock, 1000);
```

---

###  TASK 2 – Find Current Day Name

```javascript
let today = new Date();
let dayNumber = today.getDay();

let days = ["Sunday","Monday","Tuesday","Wednesday","Thursday","Friday","Saturday"];

console.log("Today is " + days[dayNumber]);
```

---

###  TASK 3 – Age Calculator (Basic)

```javascript
let birthYear = 2003;
let currentYear = new Date().getFullYear();

let age = currentYear - birthYear;

console.log("Your age is " + age);
```

---

###  TASK 4 – Create Specific Date

```javascript
let customDate = new Date();

customDate.setFullYear(2020);
customDate.setMonth(7);     // August (0 based index)
customDate.setDate(15);
customDate.setHours(10);
customDate.setMinutes(30);
customDate.setSeconds(45);

console.log(customDate.toLocaleString());
```

---

##  SECTION 2 – setTimeout & setInterval

---

###  TASK 5 – Delayed Message

```javascript
setTimeout(() => {
  console.log("Welcome Naveen");
}, 3000);
```

---

###  TASK 6 – Stop Interval After 5 Seconds

```javascript
let count = 1;

let interval = setInterval(() => {
  console.log(count);
  count++;

  if (count > 5) {
    clearInterval(interval);
    console.log("Stopped");
  }
}, 1000);
```

---

##  SECTION 3 – Promise Practice

---

###  TASK 7 – Simple Promise

```javascript
let number = 15;

let checkNumber = new Promise((resolve, reject) => {
  if (number > 10) {
    resolve("Valid number");
  } else {
    reject("Invalid number");
  }
});

checkNumber
  .then(result => console.log(result))
  .catch(error => console.log(error))
  .finally(() => console.log("Promise completed"));
```

---

##  SECTION 4 – Fetch API Task

---

###  TASK 8 – Fetch Product Prices

```javascript
fetch("https://fakestoreapi.com/products")
  .then(response => response.json())
  .then(data => {
    data.forEach(product => {
      console.log("Product: " + product.title);
      console.log("Price: " + product.price);
      console.log("-----------------");
    });
  })
  .catch(error => console.log("Error:", error));
```

---

##  SECTION 5 – Execution Order Task

###  Code

```javascript
function one(){
  console.log("one");
}

function two(){
  console.log("two");
}

function three(){
  console.log("three");
}

one()
setTimeout(two,0)
three()
```

---

###  Output

```
one
three
two
```

---

###  Explanation

* `one()` runs immediately → prints **one**
* `setTimeout(two, 0)` goes to **Web API**, then **Callback Queue**
* `three()` runs immediately → prints **three**
* After call stack is empty → `two()` executes → prints **two**

This happens because of **JavaScript Event Loop**.

---



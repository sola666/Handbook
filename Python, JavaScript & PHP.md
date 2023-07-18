
# **Python, PHP, and JavaScript Equivalents**

This manual provides a reference for common tasks and functions in Python, PHP, and JavaScript.

# **Pt. 1 | The Basics**

| Task / Function | Python | PHP | JavaScript | Description |
|-----------------|--------|-----|------------|-------------|
| *Print to console* | `print("Hello, world!")` | `echo "Hello, world!";` | `console.log("Hello, world!");` | Print a string to the console. |
| Declare a variable | `x = 10` | `$x = 10;` | `let x = 10;` | Declare a variable and assign it a value. |
| If statement | `if x > 0: pass` | `if ($x > 0) { }` | `if (x > 0) { }` | Check if a condition is true. |
| For loop | `for i in range(10): pass` | `for ($i = 0; $i < 10; $i++) { }` | `for (let i = 0; i < 10; i++) { }` | Loop over a range of numbers. |
| While loop | `while x > 0: pass` | `while ($x > 0) { }` | `while (x > 0) { }` | Loop while a condition is true. |
| Define a function | `def hello(): pass` | `function hello() { }` | `function hello() { }` | Define a function. |
| Call a function | `hello()` | `hello();` | `hello();` | Call a function. |
| Arrays/Lists | `myList = [1, 2, 3]` | `$myArray = array(1, 2, 3);` | `let myArray = [1, 2, 3];` | Declare an array/list. |
| Add to Arrays/Lists | `myList.append(4)` | `array_push($myArray, 4);` | `myArray.push(4);` | Add an item to an array/list. |
| Length of Arrays/Lists | `len(myList)` | `count($myArray);` | `myArray.length;` | Get the number of items in an array/list. |
| String Concatenation | `s = "Hello" + "World"` | `$s = "Hello" . "World";` | `let s = "Hello" + "World";` | Concatenate two strings together. |

# **Pt 2. | Intermediate**

## **Error Handling**
---
### **Python**
 In Python, errors are handled with **`try/except`** blocks. An optional `finally` block can be added to execute code regardless of whether an exception was thrown or not.

```python
try:
    x = 1 / 0
except ZeroDivisionError:
    print("You can't divide by zero!")
finally:
    print("This is the end of the program.")
```

### **JavaScript**
 JavaScript uses **`try/catch`** blocks for error handling. An optional finally block can also be included. The key difference is that JavaScript doesn't have as many built-in exceptions as Python, and usually throws a generic **`Error`** object.

```javascript
try {
    let x = 1 / 0;
} catch (error) {
    console.log("An error occurred: " + error.message);
} finally {
    console.log("This is the end of the program.");
}
```

### **PHP**
 PHP uses **`try/catch`** blocks for error handling, very similar to JavaScript. Note that PHP will throw a **`DivisionByZeroError`** exception when attempting to divide by zero.

```php
try {
    $x = 1 / 0;
} catch (DivisionByZeroError $e) {
    echo "You can't divide by zero!";
} finally {
    echo "This is the end of the program.";
}
```

## **File I/O**
---
### **Python**
 In Python, you can open a file with **`open()`**, and it's common to use a **`with`** block, so the file gets closed automatically after the block of code is executed.

```python
with open('file.txt', 'r') as f:
    content = f.read()
print(content)
```

### **JavaScript**
 JavaScript is primarily a browser-based language, so it doesn't have built-in file I/O operations like Python or PHP. However, with Node.js, you can perform file I/O using the **`fs`** module.

```javascript
const fs = require('fs');

fs.readFile('file.txt', 'utf8', (err, data) => {
    if (err) {
        console.error(err);
        return;
    }
    console.log(data);
});
```

### **PHP**
 In PHP, the **`fopen()`** function can open a file. It's then common to use **`fread()`** to read the contents and **`fclose()`** to close the file.

```php
$file = fopen("file.txt", "r");
$content = fread($file, filesize("file.txt"));
fclose($file);
echo $content;
```


## **Regular Expressions**
---
### **Python**
 Python uses the **`re`** module for regular expressions. For example, to find all occurrences of "Python" in a string:

```python
import re

text = "Python is fun. I like Python!"
matches = re.findall("Python", text)
print(matches)  # Output: ['Python', 'Python']
```

### **JavaScript**
 JavaScript has built-in support for regular expressions. Similar to the Python example:

```javascript
let text = "JavaScript is fun. I like JavaScript!";
let matches = text.match(/JavaScript/g);
console.log(matches);  // Output: ['JavaScript', 'JavaScript']
```

### **PHP**
 PHP uses the **`preg_match_all()`** function to find all matches of a regular expression in a string.

```php
$text = "PHP is fun. I like PHP!";
preg_match_all("/PHP/", $text, $matches);
print_r($matches[0]);  // Output: Array ( [0] => PHP [1] => PHP )
```

## **Object-Oriented Programming (Classes and Objects)**
---
### **Python**
 Python supports object-oriented programming with classes and objects. Here is a basic example of a class with a constructor and a method.

```python
class MyClass:
    def __init__(self, name):
        self.name = name

    def say_hello(self):
        print(f"Hello, {self.name}!")

obj = MyClass("Python")
obj.say_hello()  # Output: Hello, Python!
```

### **JavaScript**
 JavaScript supports object-oriented programming with prototypes, but also has a **`class`** syntax that was added in ES6, which is more similar to the class syntax in other languages like Python and PHP.

```javascript
class MyClass {
    constructor(name) {
        this.name = name;
    }

    sayHello() {
        console.log(`Hello, ${this.name}!`);
    }
}

let obj = new MyClass("JavaScript");
obj.sayHello();  // Output: Hello, JavaScript!
```

### **PHP**
 PHP also supports object-oriented programming with classes and objects. Here is an example similar to the Python and JavaScript examples.

```php
class MyClass {
    public $name;

    function __construct($name) {
        $this->name = $name;
    }

    function sayHello() {
        echo "Hello, $this->name!";
    }
}

$obj = new MyClass("PHP");
$obj->sayHello();  // Output: Hello, PHP!
```


# **Pt 3. | Advanced**
## **Working with Databases**
---
Note that the Python example uses SQLite for simplicity, while the PHP and JavaScript examples use MySQL. This is because SQLite has limited support in PHP and JavaScript, while MySQL is widely supported.

**Python**
```python
import sqlite3

conn = sqlite3.connect('test.db')
c = conn.cursor()

c.execute('''CREATE TABLE stocks
             (date text, trans text, symbol text, qty real, price real)''')

c.execute("INSERT INTO stocks VALUES ('2020-01-05','BUY','RHAT',100,35.14)")

conn.commit()
conn.close()
```

**JavaScript** (*with Node.js and MySQL*):
```javascript
const mysql = require('mysql');

const connection = mysql.createConnection({
  host: 'localhost',
  user: 'me',
  password: 'secret',
  database: 'my_db'
});

connection.connect();

connection.query('CREATE TABLE stocks (date VARCHAR(10), trans VARCHAR(4), symbol VARCHAR(5), qty DECIMAL(10,2), price DECIMAL(10,2))', (err, rows) => {
    if(err) throw err;
});

connection.query("INSERT INTO stocks VALUES ('2020-01-05','BUY','RHAT',100,35.14)", (err, result) => {
    if(err) throw err;
});

connection.end();
```

**PHP** (*with MySQL*):
```php
$servername = "localhost";
$username = "username";
$password = "password";
$dbname = "myDB";

$conn = new mysqli($servername, $username, $password, $dbname);

if ($conn->connect_error) {
    die("Connection failed: " . $conn->connect_error);
}

$sql = "CREATE TABLE Stocks (
id INT(6) UNSIGNED AUTO_INCREMENT PRIMARY KEY,
date TEXT,
trans TEXT,
symbol TEXT,
qty FLOAT(10,2),
price FLOAT(10,2)
)";

$conn->query($sql);

$sql = "INSERT INTO Stocks (date, trans, symbol, qty, price)
VALUES ('2020-01-05', 'BUY', 'RHAT', 100, 35.14)";

$conn->query($sql);

$conn->close();
```

## **Asynchronous Programming**
---
### **Python**
 Python 3.5 introduced the **`async`** and **`await`** keywords for handling asynchronous code. Here's a basic example using the **`aiohttp`** library to make asynchronous HTTP requests:

```python
import aiohttp
import asyncio

async def get_page(session, url):
    async with session.get(url) as response:
        return await response.text()

async def main():
    async with aiohttp.ClientSession() as session:
        html = await get_page(session, 'http://python.org')
        print(html)

loop = asyncio.get_event_loop()
loop.run_until_complete(main())
```

**`JavaScript`**: JavaScript is inherently asynchronous, with many built-in features for handling asynchronous code. Here's an example using **`fetch`** to make asynchronous HTTP requests:

```javascript
async function get_page(url) {
    let response = await fetch(url);
    let text = await response.text();
    return text;
}

get_page('https://javascript.com').then(console.log);
```

### **PHP**
 PHP is not traditionally used for asynchronous programming, but extensions and libraries are available that can add this functionality. One such library is **`ReactPHP`**, but the syntax is considerably different than Python's **`asyncio`** or JavaScript's **`Promise`** model:

```php
require 'vendor/autoload.php';

$loop = React\EventLoop\Factory::create();

$client = new React\Http\Browser($loop);

$client->get('https://www.php.net')->then(function (Psr\Http\Message\ResponseInterface $response) {
    echo (string)$response->getBody();
});

$loop->run();
```

## **Working with APIs**
---
### **Python**
 Most APIs return data in JSON format. Python can parse JSON using the built-in **`json`** module. Here's an example using the **`requests`** library to get data from an API and parsing the JSON response:

```python
import requests
import json

response = requests.get('https://api.github.com/users/{your_username}')
data = json.loads(response.text)
print(data['name'])  # Prints: {your_username}
```

### **JavaScript**
 JavaScript can also parse JSON using the built-in **`JSON`** object. Here's a similar example that uses **`fetch`**:
    
```javascript
fetch('https://api.github.com/users/{your_username}')
    .then(response => response.json())
    .then(data => console.log(data.name));  // Prints: {your_username}
```

### **PHP**
 PHP can parse JSON using the built-in **`json_decode`** function. Here's a similar example that uses **`file_get_contents`** to get the data:

```php
$response = file_get_contents('https://api.github.com/users/{your_username}');
$data = json_decode($response, true);
echo $data['name'];  // Prints: {your_username}
```

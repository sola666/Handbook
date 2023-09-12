# **Python and Go (Golang) Equivalents**

This manual provides a reference for common tasks and functions in Python and Go (Golang).

---

# **Pt. 1 | The Basics**

| Task / Function | Python | Go | Description |
|-----------------|--------|----|-------------|
| *Print to console* | `print("Hello, world!")` | `fmt.Println("Hello, world!")` | Print a string to the console. |
| Declare a variable | `x = 10` | `var x int = 10` | Declare a variable and assign it a value. |
| If statement | `if x > 0: pass` | `if x > 0 { }` | Check if a condition is true. |
| For loop | `for i in range(10): pass` | `for i := 0; i < 10; i++ { }` | Loop over a range of numbers. |
| While loop | `while x > 0: pass` | `for x > 0 { }` | Loop while a condition is true. |
| Define a function | `def hello(): pass` | `func hello() { }` | Define a function. |
| Call a function | `hello()` | `hello()` | Call a function. |
| Arrays/Lists | `myList = [1, 2, 3]` | `myArray := []int{1, 2, 3}` | Declare an array/list. |
| Add to Arrays/Lists | `myList.append(4)` | `myArray = append(myArray, 4)` | Add an item to an array/list. |
| Length of Arrays/Lists | `len(myList)` | `len(myArray)` | Get the number of items in an array/list. |
| String Concatenation | `s = "Hello" + "World"` | `s := "Hello" + "World"` | Concatenate two strings together. |

---

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

### Go
In Go, errors are values that are returned from functions and then checked. There's no exception handling in the traditional sense.

```go
_, err := os.Open("non-existent-file")
if err != nil {
    fmt.Println("An error occurred:", err)
}
```

## File I/O
### Python
In Python, you can open a file with open(), and it's common to use a with block, so the file gets closed automatically after the block of code is executed.

```python
with open('file.txt', 'r') as f:
    content = f.read()
print(content)
```

### Go
In Go, the os and io/ioutil packages can be used for file I/O operations.

```go
content, err := ioutil.ReadFile("file.txt")
if err != nil {
    log.Fatal(err)
}
fmt.Println(string(content))
```

# Pt 3. | Advanced
## Working with APIs
### Python
Most APIs return data in JSON format. Python can parse JSON using the built-in json module. Here's an example using the requests library to get data from an API and parsing the JSON response:

```python
import requests
import json

response = requests.get('https://api.github.com/users/{your_username}')
data = json.loads(response.text)
print(data['name'])  # Prints: {your_username}
```

### Go
Go's standard library provides all the necessary utilities to work with JSON and make HTTP requests. Here's how to perform a similar operation in Go:

```go
package main

import (
	"encoding/json"
	"fmt"
	"net/http"
	"io/ioutil"
)

type User struct {
	Name string `json:"name"`
}

func main() {
	resp, err := http.Get("https://api.github.com/users/{your_username}")
	if err != nil {
		fmt.Println(err)
		return
	}
	defer resp.Body.Close()

	body, err := ioutil.ReadAll(resp.Body)
	if err != nil {
		fmt.Println(err)
		return
	}

	var user User
	json.Unmarshal(body, &user)

	fmt.Println("Name:", user.Name)
}
```

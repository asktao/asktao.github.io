---
title: "Go vs PHP Syntax Comparison"
date: 2021-10-09T10:35:50+08:00
draft: false
tags: [programming,PHP,Go]
---

**Data types**
PHP types:
```php
bool
string
int //Integer 
float
array
object
NULL
resource
```

Go types:
```go
string
bool
int int8  int16  int32  int64
uint uint8 uint16 uint32 uint64 uintptr
byte //uint8 
rune //int32
float32 float64
complex64 complex128
array
slices
map
struct
```

**Variables**
Variable declarations

Go | PHP
--------- | ---------
`var i int` | `$i = 0 // integer`
`var f float64` | `$f = 0.0 // float`
`var b bool` | `$b = false // boolean`
`var s string` | `$s = "" // string`
`var a [2]string` | `$a = [] // array`

Short variable declarations

Go | PHP
------ | ------
`i := 0` | `$i = 0 // integer`
`f := 0.0` | `$f = 0.0 // float`
`b := false` | `$b = false // boolean`
`s := ""` |  `$s = "" // string`
`a := [1]string{"hello"}` | `$a = [] // array`


**Type conversions**
Go
```go
i := 42             // Signed integer
f := float64(i)     // Float
u := uint(f)        // Unsigned integer
```
PHP
```php
$i = 1;
$f = (float) $i;    // 1.0
$b = (bool) $f      // true
$s = (string) $b    // "1"
```

**Arrays**
Go
```go
var a [2]string
a[0] = "Hello"
a[1] = "World"
// OR
a := [2]string{"hello", "world"}
```
PHP
```php
$a = [
    "hello",
    "world"
];
```

**Maps**
Go
```go
m := map[string]string{
    "first_name": "Foo",
    "last_name": "Bar",
}
```
PHP
```php
$m = [
    "first_name" => "Foo",
    "last_name" => "Bar"
];
```

**Objects**
Go
```go
package main
import "fmt"
type Person struct {
    Name string
    Address string
}
func main() {
    person := Person{"Foo bar", "Sydney, Australia"}
    fmt.Println(person.Name)
}
```
PHP
```php
$person = new stdClass;
$person->Name = "Foo bar";
$person->Address = "Sydney, Australia";
echo $person->Name;
// Or using type casting
$person = (object) [
    'Name' => "Foo bar",
    'Address' => "Sydney, Australia"
];
echo $person->Name;
```

**Functions**
Go
```go
package main
import "fmt"
func fullname(firstName string, lastName string) (string) {
    return firstName + " " + lastName
}
func main() {
    name := fullname("Foo", "Bar")
    fmt.Println(name)
}
```
PHP
```php
function fullname(string $firstName, string $lastName) : string {
    return $firstName . " " . $lastName;
}
$name = fullname("Foo", "Bar");
echo $name;
 ```

** Returning multiple results**
Go
```go
package main
import "fmt"
func swap(x, y string) (string, string) {
    return y, x
}
func main() {
    a, b := swap("hello", "world")
    fmt.Println(a, b)
}
```
PHP
Returning an array to get multiple results
```php
function swap(string $x, string $y): array {
    return [$y, $x];
}
[$a, $b] = swap('hello', 'world');
echo $a, $b;
```

** Control Statements**
**If-Else**
Go
```go
package main
import (
    "fmt"
)
func compare(a int, b int) {
    if a > b {
        fmt.Println("a is bigger than b")
    } else {
        fmt.Println("a is NOT greater than b")
    }
}
func main() {
    compare(12, 10);
}
```
PHP
```php
function compare(int $a, int $b) {
    if ($a > $b) {
        echo "a is bigger than b";
    } else {
        echo "a is NOT greater than b";
    }
}
compare(12, 10);
```

**Switch**
Go
```go
package main
import (
    "fmt"
    "runtime"
)
func main() {
    fmt.Print("Go runs on ")
     
    os := runtime.GOOS;
     
    switch os {
    case "darwin":
        fmt.Println("OS X.")
    case "linux":
        fmt.Println("Linux.")
    default:
        fmt.Printf("%s.\n", os)
    }
}
```
PHP
```php
echo "PHP runs on ";
         
switch (PHP_OS) {
    case "darwin":
        echo "OS X.";
        break;
    case "linux":
        echo "Linux.";
        break;
    default:
        echo PHP_OS;
}
```

**For loop**
Go
```go
package main
import "fmt"
func main() {
    sum := 0
     
    for i := 0; i < 10; i++ {
        sum += i
    }
     
    fmt.Println(sum)
}
```
PHP
```php
$sum = 0;
     
for ($i = 0; $i < 10; $i++) {
    $sum += $i;
}
echo $sum;
```

**While loop**
Go
```go
package main
import "fmt"
func main() {
    sum := 1
     
    for sum < 100 {
        sum += sum
    }
     
    fmt.Println(sum)
}
```
PHP
```php
$sum = 1;
while ($sum < 100) {
    $sum += $sum;
}
echo $sum;
```

**Foreach/Range**
Go
```go
package main
import "fmt"
func main() {
    colours := []string{"Maroon", "Red", "Green", "Blue"}
     
    for index, colour := range colours {
        fmt.Printf("index: %d, colour: %s\n", index, colour)
    }
}
```
PHP
```php
$colours = ["Maroon", "Red", "Green", "Blue"];
     
foreach($colours as $index => $colour) {
    echo "index: {$index}, colour: {$colour}\n";
}
```


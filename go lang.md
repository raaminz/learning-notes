[[programming-language]]
- Import
`import "fmt"`
```go
import (
	"fmt"
	"http"
```

- variable
	- `var`
		- `var i int = 10`
		- `var i = 10`
		- `i := 10`
			- colon ":" only when declaration
		- `var i byte = 10 //It's harder to guess byte`
```go
var i int
fmt.Println(i)
i = 20
fmt.Println(i)

//Output : 0 20
```

```go
i := 20
i = 10
//Output : Error "i declared and not used

```

- Numberic types

| type name | min value                                         | max value                  |
| --------- | ------------------------------------------------- | -------------------------- |
| int8      | -128                                              | 127                        |
| int16     | -32768                                            | 32767                      |
| int32     | -2,147,438,648                                    | 2,147,438,647              |
| int64     | −9,223,372,036,854,775,808                        | 9,223,372,036,854,775,807  |
| uint8     | 0                                                 | 255                        |
| uint16    | 0                                                 | 65535                      |
| uint32    | 0                                                 | 4,294,967,293              |
| uint64    | 0                                                 | 18,446,744,073,709,551,615 |
| float32   | 32 bit                                            | ~7 decimal                 |
| float64   | 64 bit                                            | ~15 decimal                |
| byte      | same as unit8                                     |                            |
| int       | same as int32 or int64 (based on architecture)    |                            |
| uint      | same as uint32 or uint64 (based on architecture)  |                            |




-  No automatic converting type in go
```go
var i int8 = 20
var f float32 = 5.6
fmt.Println(float32(i) + f)
fmt.Println(i + int8(f))
// int8(f) = 5
```

```go
var i int8 = 20
var j int32 = 40
fmt.Println(i + int8(j))
```

- Strings (can be utf-8)
`var s string`

`s := "Hello world \t\n\"world!\" with a backslash \\"`

```go
//concatanation
s := "Hello world"
s2 := "!"
s3 := s + " " + s2
```

```go
s := "Hello world"
b := s[0] //byte of index 0 (H)
b := s[4] //byte of index 4 (o)
fmt.Println(s, b, string(b), b2, string(b2))
// output : Hello world 72 H 111 o
```

```go
//substrings
s := "Hello world"
s2 := s[0:5]
s3 := s[7:12]
s4 := s[:5]
s5 := s[7:]
lenght := len(s2) //becareful about utf-8 characters
```

- Arrays

```go
var vals [3]int
vals[0] = 2
vals[1] = 4
vals[2] = 6
//var vals [4]int = vals // ERROR : cannot use vals type [3]int as [4] int
```

- if statement
```go
a := 10
if b := a / 2; b > 5 {
	
} else {
	//b is accecible
}
//b is not accepbile
```
- for loop
```go
for i := 0; i < 10; i++ {
	if i == 3 {
		continue
	}
	if i > 7 {
		break
	}
}
```

```go
i := 0
for i < 10 {
	i = i + 1
}
```

```go
i := 0
for {
	i = i + 1
	if i > 10 {
		break
	}
}

```

```go
i := 0
for {
	s := "Hello world!"
	if k, v := range s {
		fmt.Println(k, v, string(v))
	}
	//position , number of value , value
}

```
- Switch statement
	- unlike java or c, cases break by default
	- you can use any type
	- in cases you can use variables
```go
word := os.Args[1]

switch word {
case "hi":
//do something
fallthrough //continue to the below cases
case "hello", "hey":
// do something
default:
// (optional) do something
}

```

```go
	word := os.Args[1]
	c := "crackerjack"
	switch l := len(word); {
	case word == "hi":
		fmt.Println("Very informal!")
		fallthrough
	case word == "hello":
		fmt.Println("Hi yourself")
	case l == 1:
		fmt.Println("I don't know any one letter words")
	case 1 < l && l < 10, word == c:
		fmt.Println("This word is either", c, "or 2-9 characters long")
	default:
		fmt.Println("I don't know what you said but it was", l, "characters long.")
	}
```

- Functions
	- pass by value
	- multiple return
	- no overloading
	- can be assigned to a variable 
	- you can return a function

```go
func divAndRemainder(a int, b int) (int, int) {
	return a / b, a % b
}

func main() {
	div, remainder := divAndRemainder(2, 3)
	fmt.Println(div, remainder)

	//anonymous function (closure)
	//it has access to local variable
	myAddOne := func(a int) int {
			return a + 1
		}
	fmt.Println(myAddOne(1))

}
```

```go
func addOne(a int) int {
	return a + 1
}

func addTwo(a int) int {
	return a + 2
}

func printOperation(a int, f func(int) int) {
	fmt.Println(f(a))
}

func main() {
	printOperation(1, addOne
	printOperation(1, addTwo)
}
```

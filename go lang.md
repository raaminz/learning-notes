[[programming-language]]
- Installation
https://go.dev/doc/install
sudo apt install golang
sudo apt install golang-1.18-go 

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
	- `rune` is a keywork to point a code in utf-8
```go
var s string
s := "Hello world \t\n\"world!\" with a backslash \\"
s_rune := rune(s)
```

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
	printOperation(1, addOne)
	printOperation(1, addTwo)
}
```

- Pointers
```go
a := 10
b := &a
c := a
fmt.Println(a, b, *b, c)

a = 20
fmt.Println(a, b, *b, c)

*b = 30
fmt.Println(a, b, *b, c)

c = 40
fmt.Println(a, b, *b, c)
/*
10 0xc00001e108 10 10
20 0xc00001e108 20 10
30 0xc00001e108 30 10
30 0xc00001e108 30 40
*/
```

```go
b := new(int)

fmt.Println(b) // if var b *int , then <nil>
fmt.Println(*b) 
// if var b *int , then panic : runtime error: invalid memory address or nil pointer dereference

/*
0xc0000b4010
0
*/
```

```go
func setTo10(a *int) {
	*a = 10
}

func main() {
	a := 20
	fmt.Println(a)
	setTo10(&a)
	fmt.Println(a)
}
/*
20
10
*/
```

- packages
	- each directory is associated with a unique package
	- by importing the packege you can use everthing in that package
	- Some packages
		- utf8 package 
			- to work with utf8 runes
		- math
			- math function
			- math/rand
				- random functions
		- time 
	- golang.org/pkg
```go
fmt.Println
//fmt = package name
//Pritnln = function name
```

```go
import "unicode/utf8"
// utf8 package in unicode library
```

- Define package
 `package blahblah`
 
 You can define variables in package level
 `var default_value = ' '`
	 - it's publicly visible
	 - you cant use colon equal (:=) to declare them

Comment block before the funtions with signle line comments //

- Visibility
	- package access - name declaration lowercase
	- public acess - name declaration uppercase

- 3rd party packages
	1- first
	`go get github.com/rylans/getlang`
	then import it 
	2 - deb tool to manage dependencies
	golang.github.io/dep
	
	`dep init`
- Slice
	- A slice is a growable sequence of values of a single specific type
	- slices are reference type
	- for range works with slices and arrays
`s := make([]string, 0)` to create a slice , 0;initial capacity
`s = append(s , "hello")` to add something to the end of list
`len(s)` to get the eize
`s[0]` to get or set an index

```go
s2 := make([]string, 2)
fmt.Println("contents of s2[0]:", s2[0])
s2 = append(s2, "hello")
fmt.Println("contents of s2[0]:", s2[0])
fmt.Println("contents of s2[2]:", s2[2])
fmt.Println("length of s2:", len(s2))

/*contents of s2[0]: 
contents of s2[0]: 
contents of s2[2]: hello
length of s2: 3*/
var s5 []string //an empty slice
```

```go
s3 := []string{"a", "b", "c"}
s4 := s3[0:2] //start from 0 , take 2 -> "a" , "b"
s3[0] = "d" //s4[0] point to the same place
```

- map
```go
m := make(map[string]int)
m["hello"] = 300
h := m["hello"]

if v, ok := m["hello"]; ok {
	//if there's any value ok is true and v has the value
	fmt.Println("hello in m:", v)
}
```

```go
m2 := map[string]int{
	"a": 1,
	"b": 2,
	"c": 50,
}

for k, v := range m2 {
	fmt.Println(k, v)
}
```

```go
m := map[string]int{
	"a": 1,
	"b": 2,
}

var m3 map[string]int
m3 = m
m3["goodbye"] = 400 //adds an element
```

- Structs
```go
type Foo struct {
	A int
	b string
}

func main() {
	f := Foo{}
	g := Foo{10, "Hello"}
	h := Foo{
		b: "Goodbye",
	}
	h.A = 1000
}
```

```go
f := Foo{
	A: 20,
}
func main() {
	var f2 Foo
	f2 = f
	f2.A = 100
	
	fmt.Println(f2.A)
	fmt.Println(f.A)
	//Here f is cloned, f2.A = 100, f.A = 20
	
	var f3 *Foo = &f
	f3.A = 200
	fmt.Println(f3.A)
	fmt.Println(f.A)
	//Here f3 is pointing, so f3.A = 200, f.A = 200
}
```

```go
type Foo struct {
	A int
	b string
}


type Baz struct {
	D string
	Foo
	//this is called embedded struct
	//kind of delegation
}

func main() {
	f := Foo{A: 10, b: "Hello"}
	b2 := Baz{D: "Nancy", Foo: f}
	fmt.Println(b2.A)
	var f2 Foo = b2.Foo
	fmt.Println(f2)
}
```

```go
type Person struct {
	Name string `json:"name"`
	Age int `json:"age"`
	//struct tags
}

func main() {
	bob := `{ "name": "Bob", "age": 30}`
	var b Person	
	//import "encoding/json"
	json.Unmarshal([]byte(bob), &b)	
	fmt.Println(b)	
	bob2, _ := json.Marshal(b)	
	fmt.Println(string(bob2))
}
```

- Methods
	- add a functionality to a struct
	- no method overriding
```go
type Foo struct {
	A int
	B string
}

func (f Foo) String() string {
	return fmt.Sprintf("A: %d and B: %s", f.A, f.B)
}

func (f *Foo) Double() {
	f.A = f.A * 2
}
```

```go
func (f Foo) fieldCount() int {
	return 2
}
type Bar struct {
	C bool
	Foo
}
//b.Foo.fieldCount() is not overriding with this method
func (b Bar) fieldCount() int {
	return 3
}
```

- Interfaces
```go
type tester interface {
	test(int) bool
}

type rangeTest struct {
	min int
	max int
}

func (rt rangeTest) test(i int) bool {
	return rt.min <= i && i <= rt.max
}
```

```go
var i interface{}
//all the types is a kind of empty interface
i = "Hello"
j := i.(string) //.(string) is assertion

k , ok := i.(int) //assertion returns both value and result

m := i.(int) //not using result return , leads panic
```

```go
type testerFunc func(int) bool
//anonymous function
func (tf testerFunc) test(i int) bool {
	return tf(i)
}

```

```go
//using switch to check the type
func doStuff(i interface{}) {
	switch i := i.(type) {
		case int:
		fmt.Println("Double i is", i+i)
		case string:
		fmt.Println("i is", len(i), "characters long")
		default:
		fmt.Println("I don't know what to do with this")
	}
}
```

- errors
```go
func divAndMod(a int, b int) (int, int, error) {
	if b == 0 {
		return 0, 0, errors.New("Cannot divide by zero")
	}
	return a / b, a % b, nil
}
func main() {
	a, err := strconv.ParseInt(os.Args[1], 10, 64)
	if err != nil {
		fmt.Println(err)
		os.Exit(1)
	}
	div, mod, err := divAndMod(int(a), int(b))
	if err != nil {
		fmt.Println(err)
		os.Exit(1)
	}
}
```

- goroutines
	- concurrency in go
	- as opposed to threads , it's managing by go
`go runMe()`

```go
var wg sync.WaitGroup
wg.Add(1)

go func() {
	runMe()
	wg.Done()
}()

wg.Wait()
```

- Channels
	- a type for transferring data between goroutines
	- if we use two input at the same time without getting output program panics, then we need to use channel buffer or do input and output one by one
	- not closing the channels causes gorouting leak
```go
in := make(chan string)
out := make(chan string)

go func() {
	name := <-in
	out <- fmt.Sprintf("Hello, " + name)
}()

in <- "Bob"
close(in)
message := <-out
fmt.Println(message)
```
- select
- backpressure
- contexts
- reflection
- defer
- panic and recover
- complex numbers
- atomics and mutexes
- copy slices
- full slice expressions
- named return values
- init functions
- blank imports
- internal packages
- methods as functions

## Links
| description            | link                                     |
| ---------------------- | ---------------------------------------- |
| Go homepage            | https://golang.org                       |
| Language specification | https://golang.org/ref/spec              |
| Effective Go           | https://golang.org/doc/effective_go.html |
| Standard library       | https://golang.org/pkg                   |
| Standard tools         | https://golang.org/doc/cmd               | 

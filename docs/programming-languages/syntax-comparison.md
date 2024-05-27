---
sidebar_position: 1
---

import Tabs from '@theme/Tabs';
import TabItem from '@theme/TabItem';

# Syntax Comparison

## Entry point

```java title="Java" showLineNumbers
public class HelloWorld {
    public static void main(String[] args) {
        System.out.println("Hello World");
    }
}
```

```go title="Go" showLineNumbers
package main

import "fmt"

func main() {
   fmt.Println("Hello, World!")
}
```

## For loop

```java title="Java" showLineNumbers
// TODO
```

```go title="Go" showLineNumbers
package main

import "fmt"

func main() {
    // for initialization; condition; post statement
    for i := 0; i < 5; i++ {
        fmt.Println(i)

        // break and continue
        if i == 3 {
            continue
        }
        if i == 4 {
            break
        }
    }

    // initialization, condition, post statement are optional
    i := 0
    for ; i < 5; {
        fmt.Println(i)
        i++
    }

    // For Range Loop (Array/Slice)
    arr := []int{1, 2, 3, 4, 5}
    for i, v := range arr {
        fmt.Printf("Index: %d, Value: %d\n", i, v)
    }
    // Output:
    // Index: 0, Value: 1
    // ...
    // Index: 4, Value: 5

    // only index
    for i := range arr {
        fmt.Println("Index:", i)
    }
    // only value
    for _, v := range arr {
        fmt.Println("Value:", v)
    }
    // only iterate over the array without using index or value
    for range arr {
        fmt.Println("Iterating...")
    }

    // For Range Loop (Map)
    m := map[string]int{"a": 1, "b": 2}
    for k, v := range m {
        fmt.Printf("Key: %s, Value: %d\n", k, v)
    }
    // Output:
    // Key: a, Value: 1
    // Key: b, Value: 2

    // For Range Loop (String)
    s := "Hello"
    for i, r := range s {
        fmt.Printf("Index: %d, Rune: %c\n", i, r)
    }
    // Output:
    // Index: 0, Rune: H
    // ...
    // Index: 4, Rune: o

    // For Range Loop (Channel)
    ch := make(chan int, 2)
    ch <- 1
    ch <- 2
    close(ch)
    for v := range ch {
        fmt.Println(v)
    }
    // Output:
    // 1
    // 2

    // continue will iterate from the next i
    outer:
    for i := 0; i < 3; i++ {
        for j := 0; j < 3; j++ {
            if i == 1 && j == 1 {
                continue outer
            }
            fmt.Printf("i: %d, j: %d\n", i, j)
        }
    }

    // break will break the outer loop and jump to `fmt.Println("Loop exited")`
    outer:
    for i := 0; i < 3; i++ {
        for j := 0; j < 3; j++ {
            if i == 1 && j == 1 {
                break outer
            }
            fmt.Printf("i: %d, j: %d\n", i, j)
        }
    }
    fmt.Println("Loop exited")
}
```

## While loop

```java title="Java" showLineNumbers
// TODO
```

```go title="Go" showLineNumbers
package main

import "fmt"

func main() {
    // Go doesn't have while loop, use for loop with only condition
    i := 0
    for i < 5 {
        fmt.Println(i)
        i++
    }

    // Infinite loop
    for {
        fmt.Println("This will run forever")
        break // must use break to exit the loop
    }
}
```

## Enum

```java title="Java" showLineNumbers
// TODO
```

```go title="Go" showLineNumbers
// There is no built-in enum type in Go.
// Simulate enum using a new type and constants of that type.

package main

import "fmt"

type Color string

const (
    Red   Color = "red"
    Green Color = "green"
)

type Day int

const (
    Sunday Day = iota // iota simplyfies the initialization of the enum values
    Monday
)

func main() {
    var c Color = Red
    fmt.Println(c) // Output: red

    switch c {
    case Red:
        fmt.Println("Color is Red")
    case Green:
        fmt.Println("Color is Green")
    }

    var today Day = Sunday
    fmt.Println(today) // Output: 0

    switch today {
    case Sunday:
        fmt.Println("Today is Sunday")
    case Monday:
        fmt.Println("Today is Monday")
    }
}
```

<!-- <Tabs>
<TabItem value="java" label="Java">

```java showLineNumbers
public class HelloWorld {
    public static void main(String[] args) {
        System.out.println("Hello World");
    }
}
```

</TabItem>
<TabItem value="go" label="Go">

```go showLineNumbers
package main

import "fmt"

func main() {
   fmt.Println("Hello, World!")
}
```

</TabItem>
</Tabs> -->

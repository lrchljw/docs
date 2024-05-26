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

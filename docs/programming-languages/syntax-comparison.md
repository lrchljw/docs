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

## Loop

### For

```java title="Java" showLineNumbers
// for (initialization; condition; post statement)
for (int i = 0; i < 10; i++) {
    System.out.println(i);
}

// Infinite loop
for (;;) {
    System.out.println("Infinite loop");
}
```

```go title="Go" showLineNumbers
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

// Infinite loop
for {
    fmt.Println("This will run forever")
    break // must use break to exit the loop
}
```

### Labeled Break/Continue

```java title="Java" showLineNumbers
outerLoop:
for (int i = 0; i < 3; i++) {
    for (int j = 0; j < 3; j++) {
        if (i == 1 && j == 1) {
            break outerLoop; // Break out of the outer loop
        }
        System.out.println("i: " + i + ", j: " + j);
    }
}

System.out.println("End of labeled break example.");

outerLoop:
for (int i = 0; i < 3; i++) {
    for (int j = 0; j < 3; j++) {
        if (i == 1 && j == 1) {
            continue outerLoop; // Continue with the next iteration of the outer loop
        }
        System.out.println("i: " + i + ", j: " + j);
    }
}

System.out.println("End of labeled continue example.");
```

```go title="Go" showLineNumbers
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
```

### For Each

```java title="Java" showLineNumbers
// over Array
int[] arr = {1, 2, 3, 4, 5};
for (int num : arr) {
    System.out.println(num);
}

// over ArrayList
ArrayList<Integer> list = new ArrayList<>(Arrays.asList(1, 2, 3, 4, 5));
for (Integer num : list) {
    System.out.println(num);
}

// over Map
import java.util.HashMap;
import java.util.Map;

Map<String, Integer> map = new HashMap<>();
map.put("A", 1);
map.put("B", 2);
map.put("C", 3);
// over entrySet
for (Map.Entry<String, Integer> entry : map.entrySet()) {
    System.out.println("Key: " + entry.getKey() + ", Value: " + entry.getValue());
}
// over keySet
for (String key : map.keySet()) {
    System.out.println("Key: " + key);
}
// over values
for (Integer value : map.values()) {
    System.out.println("Value: " + value);
}
```

```go title="Go" showLineNumbers
// over Array/Slice
arr := []int{1, 2, 3, 4, 5}
for i, v := range arr {
    fmt.Printf("Index: %d, Value: %d\n", i, v)
}
// only index
for i := range arr {
    fmt.Println("Index:", i)
}
// only value
for _, v := range arr {
    fmt.Println("Value:", v)
}
// over the array without using index or value
for range arr {
    fmt.Println("Iterating...")
}

// over Map
m := map[string]int{"a": 1, "b": 2}
for k, v := range m {
    fmt.Printf("Key: %s, Value: %d\n", k, v)
}
// only key
for k := range m {
    fmt.Println("Key:", k)
}

// over String
s := "Hello"
for i, r := range s {
    fmt.Printf("Index: %d, Rune: %c\n", i, r)
}

// over Channel
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
```

### While loop

```java title="Java" showLineNumbers
import java.util.ArrayList;
import java.util.Arrays;
import java.util.Iterator;

ArrayList<String> list = new ArrayList<>(Arrays.asList("A", "B", "C"));
Iterator<String> iterator = list.iterator();

while (iterator.hasNext()) {
    String item = iterator.next();
    System.out.println(item);
}

int i = 10;
do {
    System.out.println(i);
    i--;
} while (i >= 0);
```

```go title="Go" showLineNumbers
// Go doesn't have while loop, use for loop with only condition
i := 0
for i < 5 {
    fmt.Println(i)
    i++
}

// Go doesn't have do-while loop.
```

## Statements

### Tenary Operator

```java title="Java" showLineNumbers
int a = 10, b = 20;
int max = (a > b) ? a : b;
System.out.println(max);
```

```go title="Go" showLineNumbers
a, b := 10, 20

// Go doesn't have ternary operator, use if-else statement instead.
max := a
if a < b {
    max = b
}

// Or use custom function to simulate ternary operator
func ternary(condition bool, trueVal, falseVal int) int {
    if condition {
        return trueVal
    }
    return falseVal
}
max = ternary(a > b, a, b)
```

## Data Types

### Enum

```java title="Java" showLineNumbers
// TODO
```

```go title="Go" showLineNumbers
// There is no built-in enum type in Go.
// Simulate enum using a new type and constants of that type.

// Below is an example of string enum.
type Color string

const (
    Red   Color = "red"
    Green Color = "green"
)

var c Color = Red
fmt.Println(c) // Output: red

switch c {
case Red:
    fmt.Println("Color is Red")
case Green:
    fmt.Println("Color is Green")
}

// Below is an example of int enum.
type Day int

const (
    Sunday Day = iota // iota simplyfies the initialization of the enum values
    Monday
)

var today Day = Sunday
fmt.Println(today) // Output: 0

switch today {
case Sunday:
    fmt.Println("Today is Sunday")
case Monday:
    fmt.Println("Today is Monday")
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

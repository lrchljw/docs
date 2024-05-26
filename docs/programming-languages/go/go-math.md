---
title: math
---

# math

## abs, min, max

```go
// abs returns the absolute value of the integer x
func abs(x int) int {
    if x < 0 {
        return -x
    }
    return
}

// min returns the smaller of the two integers x and y
func min(x, y int) int {
    if x < y {
        return x
    }
    return y
}

// max returns the larger of the two integers x and y
func max(x, y int) int {
    if x > y {
        return x
    }
    return y
}

// For Integers, have to use custom abs, min, max function
fmt.Println(abs(-1)) // 1
fmt.Println(min(1, 2)) // 1
fmt.Println(max(1, 2)) // 2

// For Floats, use math.Abs, math.Min, math.Max which accepts and returns float64
fmt.Println(math.Abs(-5.67)) // 5.67
fmt.Println(math.Min(5.67, 6.78)) // 5.67
fmt.Println(math.Max(5.67, 6.78)) // 6.78

```

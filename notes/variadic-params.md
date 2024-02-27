```go
package main

import "fmt"

func main() {
	Demo(1)
	Demo()
	fmt.Println(Demo(1, 2, 3))
	numbers := []int{4, 5, 6}
	fmt.Println(Demo(numbers...))
}

func Demo(numbers ...int) int {
	sum := 0
	for _, number := range numbers {
		sum += number
	}
	return sum
}
```

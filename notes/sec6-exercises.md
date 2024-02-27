# Exercises

## 1. Add a new static page to your app using the new pattern.

We won't need it, but just experiment a bit.


## 2. Experiment a bit with errors

We saw how `fmt.Errorf` allows us to wrap errors.

Explore the `errors` package and documentation to see if you can learn how to determine if a wrapped error is a specific type. Eg:

```go
package main

import (
	"errors"
	"fmt"
)

func main() {
	err := B()
  // TODO: Determine if the `err` variable is an `ErrNotFound`

}

// It is common for packages like database/sql to return
// an error that is predefined like this one.
var ErrNotFound = errors.New("not found")

func A() error {
	return ErrNotFound
}

func B() error {
	err := A()
	return fmt.Errorf("b: %w", err)
}
```

*Hint: Look at `errors.Is`*

As a followup, read about `errors.As` and see if you can use it or think of cases where it might be useful.

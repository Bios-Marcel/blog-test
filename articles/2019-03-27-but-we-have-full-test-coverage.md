---
layout: post
title: But we have full test coverage!
---

I often see people claiming that their tests are as good as they could
get, since they have full (100%) test coverage. And obviously 100% coverage
is as good as it could possibly get. Or is it not? You guessed it, coverage
isn't everything, The quality of the tests plays a big role as well.

Here is a little example of full test coverage that isn't very useful:

```go
package testme

var (
    someMapping = map[int]string(
        1: "Hello",
        2: "World"
    )

    OutOfBoundsError = errors.New("Out of bounds")
)

func Something(input int) (output string, err error) {
    if input > 0 {
        return someMapping[input], nil
    }

    return "", OutOfBoundsError
}
```

```go
package testme_test

func TestSomething(t *testing.T) {
    result, err := Something(1)
    if err != nil {
        t.Error("result should've been 'Hello', but an error was returned")
    }

    if result != "Hello" {
        t.Errorf("result should've been 'Hello', but was '%s'", result)
    }

    result, err = Something(2)
    if err != nil {
        t.Error("result should've been 'World', but an error was returned")
    }

    if result != "World" {
        t.Errorf("result should've been 'World', but was '%s'", result)
    }

    result, err = Somethng(0)
    if err != nil {
        t.Error("call should've returned an error, but it didn't")
    }
}
```

This code will test all statements, meaning that it will have full coverage.
But it won't test all theoretically possible cases. When calling `Something`
with `3`, we will get an empty string instead of the expected error, since
accessing a non-existent key in a map will return the types default value.

If you wanna test this out for yourself, go ahead and run this:

```go
package main

import "fmt"

func main() {
    wow := map[int]int{2: 4}
    fmt.Println(wow[1])
}
```        

So whenever you write a test, don't look at the code coverage first, instead
pay attention to whether you have tested all possible cases. However, if a
function doesn't have full coverage, that is probably an indicator for cases
that aren't handled or even useless code¹.

---
¹code that can never be called, no matter what happens

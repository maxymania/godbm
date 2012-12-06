godbm
=====

This repository is forked from: https://github.com/dchest/godbm
I had done this to
- Archive this version and to
- To add some improvements


An Example/Test
---------------

```go
package main
import (
	"godbm"
	"fmt"
)

func write() {
	db, err := godbm.Create("test.db", 10)
	if err != nil {
		fmt.Println("Error:", err)
		return
	}

	if err = db.Set([]byte("foo"), []byte("bar")); err != nil {
		fmt.Println("Error:", err)
		return
	}

	var data []byte
	if data, err = db.Get([]byte("foo")); err != nil {
		fmt.Println("Error:", err)
		return
	}
	fmt.Printf("Data: %s\n", data)
}

func read() {
	db, err := godbm.Read("test.db")
	if err != nil {
		fmt.Println("Error:", err)
		return
	}
	var data []byte
	if data, err = db.Get([]byte("foo")); err != nil {
		fmt.Println("Error:", err)
		return
	}
	fmt.Printf("Data: %s\n", data)
}

func appnd() { // append(..) is an build-in function, so don't use that name!
	db, err := godbm.Open("test.db")
	if err != nil {
		fmt.Println("Error:", err)
		return
	}

	if err = db.Set([]byte("hallo"), []byte("Welt!")); err != nil {
		fmt.Println("Error:", err)
		return
	}

	var data []byte
	if data, err = db.Get([]byte("hallo")); err != nil {
		fmt.Println("Error:", err)
		return
	}
	fmt.Printf("Data: %s\n", data)
}

func change() {
	db, err := godbm.Open("test.db")
	if err != nil {
		fmt.Println("Error:", err)
		return
	}

	if err = db.Set([]byte("foo"), []byte("Welt!")); err != nil {
		fmt.Println("Error:", err)
		return
	}

	var data []byte
	if data, err = db.Get([]byte("foo")); err != nil {
		fmt.Println("Error:", err)
		return
	}
	fmt.Printf("Data: %s\n", data)
}

func main() {
	// write()
	// appnd()
	change()
	// read()
}
```


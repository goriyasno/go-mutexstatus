# go-mutexstatus

Check is mutex locked

## Installation

```bash
go get -u github.com/goriyasno/go-mutexstatus
```

## Usage

```go
package main

import (
	"fmt"
	"github.com/goriyasno/go-mutexstatus"
	"sync"
)

func main() {
	var m sync.Mutex
	fmt.Println("Is locked: ", mutexstatus.IsLocked(&m))
	m.Lock()
	fmt.Println("Is locked: ", mutexstatus.IsLocked(&m))
	m.Unlock()
	fmt.Println("Is locked: ", mutexstatus.IsLocked(&m))

	var rw sync.RWMutex
	fmt.Println("Is write locked: ", mutexstatus.IsWriteLocked(&rw), ". Is read locked: ", mutexstatus.IsReadLocked(&rw))
	rw.Lock()
	fmt.Println("Is write locked: ", mutexstatus.IsWriteLocked(&rw), ". Is read locked: ", mutexstatus.IsReadLocked(&rw))
	rw.Unlock()
	fmt.Println("Is write locked: ", mutexstatus.IsWriteLocked(&rw), ". Is read locked: ", mutexstatus.IsReadLocked(&rw))
	rw.RLock()
	fmt.Println("Is write locked: ", mutexstatus.IsWriteLocked(&rw), " . Is read locked: ", mutexstatus.IsReadLocked(&rw))
	rw.RLock()
	fmt.Println("Is write locked: ", mutexstatus.IsWriteLocked(&rw), ". Is read locked: ", mutexstatus.IsReadLocked(&rw))
	rw.RUnlock()
	fmt.Println("Is write locked: ", mutexstatus.IsWriteLocked(&rw), ". Is read locked: ", mutexstatus.IsReadLocked(&rw))
	rw.RUnlock()
	fmt.Println("rIs write locked: ", mutexstatus.IsWriteLocked(&rw), ". Is read locked: ", mutexstatus.IsReadLocked(&rw))
}
```
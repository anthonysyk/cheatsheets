## Comment lancer les tests de manière séquentielle : 

`go test -p 1`

ou

```
var lockMutex sync.Mutex

func lock() func() {
	lockMutex.Lock()
	return func() {
		lockMutex.Unlock()
	}
}

func TestFoo(t *testing.T) {
	defer lock()()
	// Something
}

func TestBar(t *testing.T) {
	defer lock()()
	// Something
}
```

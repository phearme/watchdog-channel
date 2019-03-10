# watchdog-channel
A simple watchdog based on golang channels

## Installation
`go get github.com/phearme/watchdog-channel`

## Usage
```go
// kicks at interval on the GetKickChannel()
w := watchdog.NewWatchdog(time.Second * 3)
i := 0
for {
  select {
  case <-w.GetKickChannel():
    fmt.Println("kick!")
		i++
		if i == 3 {
			// stop the watchdog permanently
			w.Stop()
			return
		}
  }
}
```
Reset the watchdog timer:
```go
w.Reset()
```

## Online example
[Go Playground](https://play.golang.org/p/wLtW6V4k8k7)

# About

A watchdog timer (sometimes called a computer operating properly or COP timer, or simply a watchdog) is an electronic timer that is used to detect and recover from computer malfunctions. During normal operation, the computer regularly resets the watchdog timer to prevent it from elapsing, or "timing out". If, due to a hardware fault or program error, the computer fails to reset the watchdog, the timer will elapse and generate a timeout signal. The timeout signal is used to initiate corrective action or actions. The corrective actions typically include placing the computer system in a safe state and restoring normal system operation.


The library *belfinor/wdog* allows you to protect yourself from deadlocks and handle such situations.

# Install library

```
go get github.com/belfinor/wdog
```

# Usage

Import package to you code:

```go
import (
  "gihtub.com/belfinor/wdog"
)
```

Create watch dog object:

```go
func example() {

  wd := New(60, func() {
    panic("WatchDog")
  })


  for {
    <- time.After(time.Second)
    wd.Alive()
  }

}
```

In this example, we create watchdog object. Time until function call is 60 seconds (In function you can send notify to monitoring system, email for some people or kill application). If func is null, the object calls *os.Exit(1)* and the program will be terminated.

*Alive* call resets watchdog timer.


If watchdog is no longer required, call the *Close* method.

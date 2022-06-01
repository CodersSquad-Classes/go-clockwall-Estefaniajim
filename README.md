[![Open in Visual Studio Code](https://classroom.github.com/assets/open-in-vscode-c66648af7eb3fe8bc4f294546bfd86ef473780cde1dea487d3c4ff354943c9ae.svg)](https://classroom.github.com/online_ide?assignment_repo_id=7953071&assignment_repo_type=AssignmentRepo)
Lab - ClockWall
===============

Modify the [`clockServer.go`](./clockServer.go) to accept the `-port` parameter
and write a program [`clockWall.go`](clockWall.go) that acts as a client
of several clock servers at once.

It will read the times from each one and displaying the results in a
table. If you have access to geographically distributed computers,
run clock instances remotely; otherwise run local instances on different
ports with fake time zones.


How to run your program
-----------------------

In order to run your clock servers and client you will need to open different terminals.

- **Terminal 1** (Clock Server 1)
```
$ TZ=US/Eastern    go run clockServer.go -port 8010
```

- **Terminal 2** (Clock Server 2)
```
$ TZ=Asia/Tokyo    go run clockServer.go -port 8020
```

- **Terminal 3** (Clock Server 4)
```
$ TZ=Europe/London go run clockServer.go -port 8030
```

- **Terminal 4** (Single Clock Wall Client)
```
$ go run clockWall.go NewYork=localhost:8010 Tokyo=localhost:8020 London=localhost:8030
US/Eastern    : 12:00:00
Asia/Tokyo    : 17:00:00
Europe/London : 02:00:00
```

Please remember that your program should support any number of clock
servers, keep this in mind and perform some tests with more than the
suggested 3 clock servers.

General Requirements and Considerations
---------------------------------------
- Use the `clockServer.go` and `clockWall.go` files for your implementation.
- **You must use unbuffered and buffered channels**
- Follow the command-line arguments convention
- Don't forget to handle errors properly
- Coding best practices implementation will be also considered

Useful links
------------
- https://yourbasic.org/golang/time-change-convert-location-timezone/
- https://golang.org/pkg/flag/
- https://gobyexample.com/environment-variables


Test Suite
----------

Since it's a multi-process execution, it will be manually executed
with the steps provided in the [How to run your
program](#how-to-run-your-program) section.

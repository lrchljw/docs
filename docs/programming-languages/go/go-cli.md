---
title: cli
---

# cli

Frequently used commands for my reference.

## test

### Specific test in a file

Run only the tests that starts with `Example` in the file `example_test.go`.

```sh
go test -v -run Example ./example_test.go
```

### HTML coverage report

1. Run all tests and generate coverage report.

```sh
go test -coverprofile=coverage.out
```

2. Generate HTML coverage report base on the coverage.out file.

```sh
go tool cover -html=coverage.out -o coverage.html
```

## godoc

Generate documentation for the project, and open the documentation in the browser.\
e.g.: http://localhost:6060/pkg/github.com/ppc-games/ppcerrors/

```sh
godoc -http=:6060
```

## go mod tidy

Automatically tidy and update the dependency list of the project, ensuring that only the libraries actually needed by the project are present in the go.mod and go.sum files, and removing unused libraries.

```sh
go mod tidy
```

## publish

Refresh the module cache and publish the module to the proxy server.

```sh
GOPROXY=proxy.golang.org go list -m github.com/ppc-games/ppcerrors@v0.1.2
```

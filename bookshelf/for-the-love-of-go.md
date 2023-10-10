---
layout: default
title: For the Love of Go
---

## For the Love of Go

<img src="/photos/books/for-the-love-of-go.png" height ="300">

A nice book friendly towards complete beginners of programming. This is the book I used to learn Go with. I like it as does it with tests.

## Code

[https://github.com/xjpa/fortheloveofgo](https://github.com/xjpa/fortheloveofgo)

## Notes

- go organizes code through modules and each module needs a separate folder/directory with each having their own go module (go.mod) file
- to create a go module: `$ go mod init MODULE_NAME`
- test files in go are those that end with `_test.go` like `calculator_test.go`
- to run a test file for a go package: `$ go test`
- next thing to do is to make sure your Go code is formatted right using `gofmt`
- to do it, run: `$ gofmt -d NAME_OF_FILE.go`

<a href="/bookshelf">⬅️ back to bookshelf</a>

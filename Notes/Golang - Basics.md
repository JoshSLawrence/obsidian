---
tags:
  - Golang
---
# Basics

**Quick Links**
	[Official Getting Started Guide](https://go.dev/doc/#references)  
	[Official Database Start Guide](https://go.dev/doc/tutorial/database-access)  
	[Standard Library Reference](https://pkg.go.dev/std)  
	[Command Line Reference](https://go.dev/doc/cmd)  
	[Module Reference](https://go.dev/ref/mod)  

## Setup your project

in the root of your project directory, run the following command:

```bash
go mod init <path/module_name>
```

The path/module_name must be valid or you will run into problems later down the line. e.g. github.com/joshlawrence/myrepo/mymodule.
## Import Modules

External modules must be imported to leverage the functions in your own project.

A single import can be declared like so:

```Go
import "fmt"
```

Additionally, multiple imports can be declared with a single import statement:

```Go
import (
	"fmt"
	"rsc.io/quote"
)
```

Unused packages are viewed as compile-time errors. A format tool will often remove any imported package on-save if it has yet to be used. Be sure to add a line leveraging the package after adding an import, then save.

To install or remove packages declared/removed from an import declaration, run the following command:

```bash
go mod tidy
```

## Execute Go Code

To compile and execute a go program, run the following command:

```bash
go run .
# or
go run <path to .go file>
```

By default, `go run .` will look in the working directory to compile and execute your program starting from the file with `package main declared`. Alternatively, you can pass in a direct path.
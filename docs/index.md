## Go at the heart of Software Engineering

"Software engineering guided the design of Go. More than most general-purpose programming languages, Go was designed to address a set of software engineering problems we encountered while building large-scale server software." - Article [Go at Google: Language Design in the Service of Software Engineering](https://go.dev/talks/2012/splash.article)

Conceived in late 2007, Go is an open-source, compiled, concurrent, garbage-collected, and statically typed language developed by Google. Go was designed for the modern computing landscape, taking into account multicore processors, networked systems, massive computing clusters, and the web programming model. Its design strengths include:

- concurrency
- built-in garbage collection
- rigorous dependency management
- software architecture adaptability supporting growth
- component interfaces

Go is efficient, scalable, and productive, yet it can also be perceived as uninspired or boring—this is because Go was designed to solve software engineering problems, rather than to serve as an innovative research language. The problems Go was built to address include:

- slow builds
- uncontrolled dependencies
- programmers using different subsets of the language
- poor code comprehension (hard-to-read code, inadequate documentation, etc.)
- duplication of effort
- cost of updates
- version skew
- difficulty in writing automated tools
- cross-language builds

### Examples of Google problems solved by Go

One example of a design benefit in Go is the use of braces to delimit blocks, rather than relying on indentation spacing—which can lead to compilation failures and introduce invisible bugs, particularly when interpreted during a SWIG invocation.

```python
# Unlike in Python, in SWIG the second line will always execute,
# even though it appears to be part of the same 'if' block
if (x > 0)
  printf("positive\n");
  printf("greater than zero\n");
```

>💡SWIG (**Simplified Wrapper and Interface Generator**) is a tool that automatically generates integration code between C/C++ and other languages ​​(Python, Java, C#, etc.).

Another example of a challenge is the excessive compilation time required by C/C++ due to repeated file inclusions and re-reading of headers in every source file; at Google, compilation is impractical using just a single computer, and even with a distributed build system, compilation times have reached up to 45 minutes.

### Main Features

- Unused dependencies result in a compilation error, promoting accuracy in the dependency tree and reducing compilation time.

- Circular imports are disallowed to prevent large-scale issues (bloated binaries, slow startup, and difficulties with testing, refactoring, and deployment) and to increase compilation speed by avoiding simultaneous file processing.

- Dependencies are defined by a unique path, enabling decentralized management; note that while the path must be unique, the package name does not have to be—consumers using packages with the same name are responsible for renaming them internally for ease of use.

- Minimalist syntax with only 25 keywords, making it easier to write automation tools.

- Go deliberately does not support default values ​​for function arguments to avoid creating calls with numerous omitted arguments that are difficult to decipher.

- Exporting (public visibility) is determined by the first letter of the declaration: if uppercase, the declared entity can be used by other packages; otherwise, it is private to the package itself. This applies to variables, types, functions, methods, constants, fields, etc.

- A single type cannot have two methods with the same name (no method overloading), simplifying method invocation and compilation.

- Built-in concurrency support—unlike C++ and Java, which lack sufficient language-level concurrency support.

- Garbage collection automatically frees used memory, avoiding unnecessary complexity, effort, and errors in system design—especially when using concurrency—and allowing the design to focus on behavior rather than resource management. However, it provides programmers with tools to control garbage collector overhead.

- No inheritance; uses interface-based composition instead. They are more flexible (even *ad hoc*), organic, decoupled, independent, and therefore scalable. There is no `implements` declaration; any data type that implements the interface's methods satisfies the interface implicitly, a fact verified statically at compile time. This ensures uniform, orthogonal, and safe programming, avoiding behavioral changes in subclasses—whereas inheritance requires the system to be designed upfront and makes subsequent modification difficult, rendering it fragile to change (requiring initial over-engineering to anticipate every possible use case from the start). The way system components interact should adapt as the system grows, rather than being fixed at the outset.

- It does not incorporate exceptions or conventional error handling; it does not treat errors as exceptional cases but maintains a more direct programming flow, compelling the programmer to address them rather than simply propagating them up the call stack.

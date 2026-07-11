# Go at the heart of Software Engineering

Software engineering guided the design of Go. More than most general-purpose programming languages, Go was designed to address a set of software engineering problems we encountered while building large-scale server software.

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
``` ```

<aside>
💡

SWIG (**Simplified Wrapper and Interface Generator**) is a tool that automatically generates integration code between C/C++ and other languages ​​(Python, Java, C#, etc.).

</aside>

Another example of a challenge is the excessive compilation time required by C/C++ due to repeated file inclusions and re-reading of headers in every source file; at Google, compilation is impractical using just a single computer, and even with a distributed build system, compilation times have reached up to 45 minutes.

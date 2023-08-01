# Infinite, Reflective Tower of Interpreters

Just like how a program takes in data as input and produces data as output, a compiler (resp. interpreter) is a program that takes in source code as input and produces executable binaries (resp. result data) as output. From the compiler's perspective, the program's source code is just input data.

Programming macros can be thought of as code running in a meta-interpreter that takes the original source code as input data and produces modified source code as output data. This idea can be expanded into an infinite, reflective tower of interpreters, where code at meta level $n$ is treated as data (specifically an concrete syntax tree) for meta level $n + 1$ (where 'normal' user level code is at meta level $0$).

When running a program at meta level $n$ (here called the VM), code at meta level $n + 1$ (here called the host) can be used to perform interesting effects at runtime, such as:

* **VM Reflection**: Since the VM is running on the host's environment, the host can pause execution and inspect the contents of the VM. This can be used to:
  * evaluate snippets of code using the VM's environment
  * print a stack trace (or even more) when the VM enters a state where it cannot continue execution (see below)
* **Unbound variables in the VM**: Instead of crashing on an unbound variable, the VM can pause and wait for the host to provide the value of the unbound variable, then the VM can continue execution. While the VM is in its paused state, the host can also reflect on the contents of the VM (such as the current stack) instead of continuing execution, i.e. a stack trace.

## References/Links

* Nada Amin - '[Programming Should Eat Itself](https://www.youtube.com/watch?v=SrKj4hYic5A)', Strange Loop 2014.
  * Ken'ichi Asai - Black Programming Language, 1996.
* Nada Amin (2021 Aug 12). '[Reflective Towers of Interpreters](https://blog.sigplan.org/2021/08/12/reflective-towers-of-interpreters/)', SIGPLAN PL Perspectives.

## TODO: Ideas to incorporate

There appears to be a relationship between interpreter levels and escaping/quoting. Similar to how code at level $n$ appears as data at level $n + 1$ and "data-of-data" at level $n + 2$, data can be escaped mulitple times, e.g. `\\n` representing an escaped newline, `\\\\n` representing a doubly-escaped newline, etc.

There are two general methods for reverse-parsing (converting an AST into a string, the reverse of parsing):

* convert each node in the AST into a string, then compose the strings together
* use a string template, with positions in the string (e.g. `%s` for C's `printf`) to indicate places to inject values into to create the final string

Both these methods can be related to interpreter/escape levels:

* Composing strings requires quoting the strings that do not depend on the values in the AST, pushing them down one level, while strings based on values remain at the original level.
* Templating pushes the entire string down one escape level, only raising the escape level when a value is to be resolved.

```javascript
let x = 5;
let y = 3;

// Reverse-parsing using string composition
let str1 = "The sum of x and y is " + (x + y).toString() + ".";

// Reverse-parsing using string template
let str2 = `The sum of x and y is ${x + y}.`;

console.log(str1 === str2); // true
```

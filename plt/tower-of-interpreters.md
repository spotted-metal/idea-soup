# Infinite Tower of Interpreters

## Nada Amin - ['Programming Should Eat Itself'](https://www.youtube.com/watch?v=SrKj4hYic5A), Strange Loop 2014

Just like how a program takes in data as input and produces data as output, a compiler (resp. interpreter) is a program that takes in source code as input and produces executable binaries (resp. result data) as output. From the compiler's perspective, the program's source code is just input data.

Programming macros can be thought of as code running in a meta-interpreter that takes the original source code as input data and produces modified source code as output data. This idea can be expanded into an infinite tower of interpreters, where code at meta level $n$ is treated as data (specifically an abstract syntax tree) for meta level $n + 1$.

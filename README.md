# 🐚 Minishell

Minishell is a bash-like command-line interpreter written in C that replicates core Unix shell functionality. Developed as part of the 42 School curriculum with Kristin Schmitt ([@kristin32schmitt](https://github.com/kristin32schmitt)) and Aidar Sharafeev ([@asta24326](https://github.com/asta24326)), it focuses on low-level process execution, memory management, and signal handling.

## 🚀 Key Features

- **Pipeline Execution**: Chain multiple commands using pipes (`|`) with proper file descriptor management.
- **Redirections & Heredocs**: Complete support for input/output redirections (`<`, `>`, `>>`) and heredoc (`<<`).
- **Built-in Commands**: Custom implementations of `cd`, `echo` (with `-n`), `env`, `exit`, `export`, `pwd`, and `unset`.
- **Environment & Signals**: Dynamic variable expansion (`$VAR`, `$?`) and signal handling (`CTRL+C`, `CTRL+D`, `CTRL+\`).

## 📦 Built With

- `C`
- `GNU Readline`
- `GCC`
- `Make`
- `Valgrind`

## 📍 The Process

We approached the project by separating the shell lifecycle into two core stages: parsing and execution. The parsing module breaks user input into tokens, expands environment variables, handles quote scopes, and constructs an Abstract Syntax Tree (AST) / command table. The execution engine then walks through the structure, creating child processes via `fork()`, wiring file descriptors using `pipe()` and `dup2()`, and handling process signals without leaking system resources.

## 🧠 What We Learned & Overall Growth

- **Process & Memory Architecture**: Gained a deep understanding of process isolation, file descriptor tables, process groups, and rigorous memory tracking to ensure zero leaks under Valgrind.
- **Systems-Level Edge Cases**: Mastered complex edge-case handling around file permissions, non-existing environment variables, nested quotes, and signal interruptions during blocking operations.
- **Collaborative Engineering**: Enhanced pair-programming, codebase organization, and technical communication while dividing complex modules between team members.

## 💡 How It Can Be Improved

- **Job Control**: Add support for background (`&`) and foreground job management (`fg`, `bg`).
- **Advanced Wildcards**: Implement filename expansion using pattern matching (`*`).
- **Scripting Support**: Enable reading and executing shell script files directly.
- **Customization**: Support custom prompt formatting and `.minishellrc` configuration files.

# Installation and Setup

## Learning Objectives

- Identify the main parts of a Python development setup.
- Check whether Python is installed and which version is available.
- Understand the roles of the interpreter, terminal, editor, and IDE.
- Select the correct interpreter in an editor.
- Recognize PATH issues and why project environments are useful.

## 1. The Main Parts of a Python Setup

A practical setup usually includes:

- **Python implementation:** the program that runs Python code.
- **Terminal or shell:** a text interface for running commands.
- **Code editor or IDE:** an application for writing and managing code.
- **Project folder:** the directory containing the code and related files.
- **Optional project environment:** an isolated location for a project's packages.

These are different things. Installing an editor does not necessarily install Python, and having Python installed does not guarantee that an editor is using the same interpreter you expect.

## 2. Check the Installed Python Version

Open a terminal and try:

```bash
python --version
```

On some systems, the command is named `python3` instead:

```bash
python3 --version
```

On Windows, the Python launcher may also be available:

```powershell
py --version
```

Use the command that works on your system. The result should identify a Python 3 version. For a new project, use a version that is currently supported and compatible with the libraries you need. The newest version is not always supported immediately by every third-party package.

If a command is not found, Python may be absent, installed under another command name, or missing from the command search path. Check the official installation guidance for your operating system rather than downloading an installer from an unknown source.

## 3. Interpreter, Terminal, Editor, and IDE

The **interpreter/runtime** runs code. The **terminal** accepts shell commands. The **editor** lets you write source files. An **IDE** combines editing with features such as running, debugging, and project navigation.

Visual Studio Code is an editor that can provide Python-specific features through extensions. It still needs an available Python interpreter, and the selected interpreter matters.

When an editor reports a missing module or uses an unexpected version, check which interpreter is selected before reinstalling packages. A package installed for one Python environment may not be available in another.

## 4. PATH and Command Names

A shell searches configured locations to find commands. On many systems, this search uses an environment variable called `PATH`.

If `python` is not recognized, it does not always mean Python is uninstalled. The executable might have a different command name or might not be on PATH. Conversely, a working `python` command may point to a different installation than the one your editor uses.

Avoid changing system-wide Python settings blindly, especially on Linux, where system tools may rely on the distribution's Python packages. Prefer the operating system's documented setup and project-specific environments.

## 5. Project Environments

A **virtual environment** isolates a project's Python packages from other projects and from the system's packages. This helps projects use different dependency versions without unnecessarily interfering with one another.

A common command to create an environment is:

```bash
python3 -m venv .venv
```

The exact creation command may need to use `python` or `py` depending on the platform. After creating `.venv`, activation commands differ by operating system and shell.

On Linux or macOS using bash/zsh:

```bash
source .venv/bin/activate
```

On Windows PowerShell:

```powershell
.venv\Scripts\Activate.ps1
```

On Windows Command Prompt:

```bat
.venv\Scripts\activate.bat
```

When activation succeeds, the environment name often appears in the shell prompt. To leave the environment, run:

```bash
deactivate
```

Activation changes which environment's commands are found in that shell; it does not replace or uninstall the system Python. You can also use the environment's Python executable directly without activating it. If PowerShell blocks activation, read the official Python and PowerShell guidance rather than changing security settings blindly.

If creating an environment fails with a message that `venv` or `ensurepip` is unavailable, your operating system may package that support separately. Follow your distribution's official instructions and choose the package that matches the Python installation you are using. Avoid using `sudo pip` to modify the system Python environment.

A virtual environment does not install every library automatically, and it does not replace version control. It provides a separate environment in which project dependencies can be installed.

### Installing a third-party package

When you are ready to use an external package, activate the project's environment first, then use that environment's Python to run pip. For example, to check pip:

```bash
python -m pip --version
```

To install a package, replace `package-name` with the package's actual name:

```bash
python -m pip install package-name
```

These are command templates, not commands to run literally with the placeholder name. Use a project's official installation instructions and verify that the package supports your Python version. On Linux, avoid using `sudo pip` to install packages into the system Python. For projects that depend on third-party packages, keep a record of dependencies and follow the project's environment instructions.

## 6. A Sensible Setup Checklist

Before beginning a project, confirm:

- Python 3 is installed and its version is known.
- You can open a terminal in the intended project directory.
- Your editor is using the intended interpreter.
- A small script can run successfully.
- Project dependencies can be installed in an appropriate environment.
- You know where your source files are saved.

## Summary

A reliable setup depends on more than installing Python. Know which interpreter runs your code, which terminal and editor you use, and where project dependencies are installed. Keep project environments isolated when useful, and prefer official installation instructions.

## Exercises

1. Explain the difference between Python, a terminal, and a code editor.
2. Which command would you try first on a system where `python` is unavailable but Python may be installed?
3. Why might a package appear missing in VS Code even after you installed it in a terminal?
4. What problem does a virtual environment help solve?
5. Why should you be cautious about changing the system Python on Linux?

## Knowledge Check

You should be able to verify a Python version, identify the interpreter used by your editor, and describe the purpose of a project environment.

## References

- [Official Python downloads](https://www.python.org/downloads/)
- [Python 3 installation and usage](https://docs.python.org/3/using/index.html)
- [The `venv` module](https://docs.python.org/3/library/venv.html)
- [Python in Visual Studio Code](https://code.visualstudio.com/docs/languages/python)
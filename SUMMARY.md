# Summary of the course

## Python

Classes and Functions in Python are all first class obejcts!

### Creating modules

There are two things that are necessary to create a package. First, its location. Python looks only into certain places for packages. We can look at this places by typying `sys.path` on the python interpreter. P.S.: usually the first entry on `sys.path` is an *empty string*. An empty string stands for the **current directory**, despite the other paths. Second, the `__init__.py` file.

```python

```

### The __init__.py file

It can be used for a series of things. Among them:

1. Defining which modules are exported when the `*` is used to import a package by defining an `__all__` attribute. E.g.:

```python
# at __init__.py
__all__ = ['foo', 'bar', 'baz']
```

### Adding static files

It could be "anywhere" within our module, but it is always a good idea to create a dedicated folder for static files. If we want to add the static file to our package, it is desirable that the file be **READ ONLY**.

- Tips
  - We can use the `pkgutil.get_data()` function to retrieve data from a certain path. This function returns a byte object.

### Some guidelines

See [PEP8](https://www.python.org/dev/peps/pep-0008/).

### docstrings

See [PEP257](https://www.python.org/dev/peps/pep-0257/).

- Python documentation tools:
  - Sphinx

### Running packages as executable

Use the `-m` flag on the `python` command. Example: `python -m venv path/to/env`.

Python looks for `__MAIN__`, which should be the program entry point. That leads to a very common pattern:

```python
def main_function():
    print("Hello")

if __name__ == '__main__':
    main_function()
```

Which is to compared the module's name (assigned by the compiler) and if a module is given the name `__main__`, it means it is being ran as the main package.

- Reading arguments

Arguments can be read using some useful packages, like the standard package library called `argparse`.

```python
# Let's suppose the name of the package is apdemo
import argparse
parser = argparse.ArgumentParser(
    prog = 'python -m apdemo',
    description = 'a demo package'
)

# adding optional arguments
parser.add_argument('-p','--print', action='store_true', default=False)

parser.add_argument('name', nargs='+')
args = parser.parse_args()
```

### Using shell scripts to run our python programs

Bash files are always marked with `#!/bin/sh` on the first line of the file.
Bash files need to be marked as executable.

Example of a bash file to run our python programs.

```bash
#!/bin/sh
# cd to the env folder
cd /path/to/project/env
# activate env
source bin/activate
# run program with the python command
python -m projejct entry
```

Then, all we need to do is to run the bash file.

### Decorators

They only wrap a function inside another function that does something and then returns a function.

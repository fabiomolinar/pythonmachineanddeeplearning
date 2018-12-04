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
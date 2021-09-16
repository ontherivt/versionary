# Versionary

[![Build Status](https://travis-ci.org/wearespindle/versionary.svg?branch=develop)](https://travis-ci.org/wearespindle/versionary)

Package that allows to version code paths with the use of a decorator.

## Status

Currently actively used and watched.

## Usage

### Requirements

 * python 2.7
 * python 3.3, 3.4, 3.5

### Installation

```
pip install versionary
```

### Running

Usage 1.
```python

from versionary.decorators import versioned

@versioned()
def my_func():
    return 1

@versioned()
def my_func__v2:
    return 2

one = my_func.v1()
two = my_func.v2()
```

Usage 2.
```python
@versioned(1)
def my_func():
    return 1

@versioned(2)
def my_func:
    return 2

one = my_func.v1()
two = my_func.v2()
```

You can use the validate_module function from versionary.utils to
validate correct use of the decorator in the given module.

You can also call the `latest` method to always get the highest-numbered version:

```python
@versioned(1)
    class Foo:
        def __init__(self, passedin=None):
            self.local_thing = passedin

        def cls_mthd():
            return "Foo version 1"
        
        def rad(self):
            return f"dad: {self.local_thing}"

    @versioned(2)
    class Foo:
        def __init__(self, passedin=None):
            self.local_thing = passedin

        def cls_mthd():
            return "Foo version 2"

        def rad(self):
            return f"racer: {self.local_thing}"
    
Foo.v1("bod").rad() == "dad: bod"
Foo.v2("car").rad() == "racer: car"
Foo.latest("speed").rad() == "racer: speed"
```

If all you ever want is the latest version of a thing, you can simply invoke it directly:

```python
# use the Foo class from above...
Foo("car").rad() == "racer: car"
```

## Contributing

See the [CONTRIBUTING.md](https://github.com/wearespindle/versionary/blob/develop/CONTRIBUTING.md) file on how to contribute to this project.

## Contributors

See the [CONTRIBUTORS.md](https://github.com/wearespindle/versionary/blob/develop/CONTRIBUTORS.md) file for a list of contributors to the project.

## Roadmap

### Changelog

The changelog can be found in the [CHANGELOG.md](https://github.com/wearespindle/versionary/blob/develop/CHANGELOG.md) file.

### In progress

 * Minor improvements

### Future

 * Scoped versioning (Class methods)

## Get in touch with a developer

If you want to report an issue see the [CONTRIBUTING.md](https://github.com/wearespindle/versionary/blob/develop/CONTRIBUTING.md) file for more info.

We will be happy to answer your other questions at opensource@wearespindle.com

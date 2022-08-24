# In-built Python Libraries #

## inspect ##
The [inspect](https://docs.python.org/3/library/inspect.html) module provides several useful functions to help get information about live objects such as modules, classes, methods, functions, tracebacks, frame objects, and code objects. For example, it can help you examine the contents of a class, retrieve the source code of a method, extract and format the argument list for a function, or get all the information you need to display a detailed traceback.

There are four main kinds of services provided by this module: type checking, getting source code, inspecting classes and functions, and examining the interpreter stack.

The `getmembers()` function retrieves the members of an object such as a class or module.

`inspect.ismodule(object)`  
Return True if the object is a module.

`inspect.isclass(object)`  
Return True if the object is a class, whether built-in or created in Python code.

`inspect.ismethod(object)`  
Return True if the object is a bound method written in Python.

`inspect.isfunction(object)`  
Return True if the object is a Python function, which includes functions created by a lambda expression.

`inspect.getdoc(object)`  
Get the documentation string or docstring for an object

`inspect.cleandoc(doc)`  
Get cleaned docstring of an object

`inspect.signature(callable, *, follow_wrapped=True, globals=None, locals=None, eval_str=False)`  
Signature object represents the call signature of a callable object and its return annotation. Accepts a wide range of Python callables, from plain functions and classes to `functools.partial()` objects.

``` python
>>> from inspect import signature
>>> def foo(a, *, b:int, **kwargs):
...     pass

>>> sig = signature(foo)

>>> str(sig)
'(a, *, b:int, **kwargs)'

>>> str(sig.parameters['b'])
'b:int'

>>> sig.parameters['b'].annotation
<class 'int'>
```


Examples:
``` python
def fourspace(module_name):
    r''' Returns pass if used four spaces for each level of syntactically \
    significant indenting.'''
    lines = inspect.getsource(module_name)
    spaces = re.findall('\n(.+?)[a-zA-Z0-9@]', lines)
    for space in spaces:
        if len(space) % 4 > 0 and len(space) != 1: #1 in case new fn or cls start after \n
            print(space)
            return True
    return False

def function_name_had_cap_letter(module_name):
    functions = inspect.getmembers(module_name, inspect.isfunction)
    for function in functions:
        t = re.findall('([A-Z])', function[0])
        if t:
            return True
    return False

```
`Code source: theschoolofai`

## asyncio ##

## collections ##
     


# Python Libraries published on pypi #


# rust-cython-test
A rudimentary example of calling rust from cython

I've seen a number of examples of calling [Rust](http://www.rust-lang.org/) from python, including Dan Callahad's [talk
at PyCon](https://github.com/callahad/pycon2015-rust), this example from [J. Clifford Dyer](http://harkablog.com/calling-rust-from-c-and-python.html)
as well as in the official [Rust book](https://doc.rust-lang.org/nightly/book/rust-inside-other-languages.html). All of the examples
have used either the [ctypes](https://docs.python.org/2/library/ctypes.html) built-in module or [CFFI](http://cffi.readthedocs.org/).

Here is a simple example of calling a function defined in rust that doubles a `double` from within [Cython](http://cython.org/). 
The example basically relies on the formalism that one would use to call Rust from C. This involves writing a `.h` header file 
and linking to the dynamic library generated by rust via the `setup.py` file.

Basic instructions for running the example:

```
cargo build --release
python setup.py build_ext --inplace
```

Then launching IPython:

```python
In [1]: import cytest

In [2]: cytest.call_rust_double(10.0)
Out[2]: 20.0
```

This example is obviously not very useful, but I wanted to demonstrate the capability.

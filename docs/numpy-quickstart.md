# NumPy quickstart
## Prerequisites
You'll need to know a bit of python. For a refresher, see the [Python tutorial](https://docs.python.org/tutorial/). </br>

To work the examples, you'll need `matplotlib` installed in additional to NumPy.

**Learner profile**

This is a quick overview of arrays in NumPy. It demostrates how n-dimensional $(n >= 2)$ arrays are represented and can be manipulated. In particular, if you don't know how to apply common functions to n-dimensional arrays (without using for-loops), or if you want to understand axis and shape properties for n-dimensional arrays, this article might be of help. </br>

**Learning Objective**

After reading, you should be able to:

* Understand the difference between one-, two- and n-dimensional arrays in Numpy;
* Understand how to apply some linear algebra operations to n-dimensional arrays without using for-loops;
* Understand axis and shape for n-dimensional arrays.

## The Basics
NumPy's main object is the homogeneous multidimensional array. It is a table of elements (usually numbers), all of the same type, indexed by a tuple of non-negative integers. In NumPy dimensions are called *axes*.

For example, the array for the coordinates of a point in 3D space, `[1, 2, 1]`, has one axis. That axis has 3 elements in it, so we say it has a length of 3. In the example pictured below, the array has 2 axes. The first axis has a length of 2, second axis has a length of 3.

    [[1, 0, 0],
     [0, 1, 2]]

NumPy's array class is called `ndarray`. It is also known by the alias `array`. Note that `numpy.array` is not the same as the Standard Python Library class `array.array`, which only handles one-dimensional arrays and offers less funtionality. The more important attributes of an `ndarray` object are:

**ndarray.ndim**</br>
&ensp; &ensp; the number of axes (dimensions) of the array.

**ndarray.shape**</br>
&ensp; &ensp; the dimensions of the array. This is a tuple of integers indicating the size of the array in each dimension. For a matrix with *n* rows and *m* columns, `shape` will be `(n,m)`. The length of the `shape` tuples is therefore the number of axes, `ndim`.

**ndarray.dtype**</br>
&ensp; &ensp; an object describing the type of the elements in the array. One can create or specify dtype's using standard Python types. Additionally NumPy provides types of its own. numpy.int32, numpy.int16, and numpy.float64 are some examples.

**ndarray.itemsize**</br>
&ensp; &ensp; the size in bytes of each element of the array. For example, an array of elements of type `float64` has `itemsize` 8(=64/8), while one of type `complex32` has `itemsize` 4(32/8=4). It is equivalent to `ndarray.dtype.itemsize`.

**ndarray.data**</br>
&ensp; &ensp; the buffer containing the actual elements of the array. Normally, we won't need to use this attribute because we will access the elements in an array using indexing facilities.

    >>> import numpy as np
    >>> a = np.arange(15).reshape(3, 5)
    >>> a
    array([[ 0,  1,  2,  3,  4],
           [ 5,  6,  7,  8,  9],
            [10, 11, 12, 13, 14]])
    >>> a.shape
    (3, 5)
    >>> a.ndim
    2
    >>> a.dtype.name
    'int64'
    >>> a.itemsize
    8
    >>> a.size
    15
    >>> type(a)
    <class 'numpy.ndarray'>
    >>> b = np.array([6, 7, 8])
    >>> b
    array([6, 7, 8])
    >>> type(b)
    <class 'numpy.ndarray'>


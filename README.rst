========================================================================
cyordereddict: Cython implementation of Python's collections.OrderedDict
========================================================================

A drop-in replacement for the standard library's ``OrderedDict`` that is
2-3x faster. Currently only for Python 2.7.

Install:
    ``pip install cyordereddict``

Use:
    .. code-block:: python

        try:
            from cyordereddict import OrderedDict
        except ImportError:
            from collections import OrderedDict

Benchmarks:
    ==================  =================================  =========================
    Test                Code                                 Ratio (stdlib / cython)
    ==================  =================================  =========================
    ``__init__`` empty  ``OrderedDict()``                                        1.7
    ``__init__`` list   ``OrderedDict(list_data)``                               3.2
    ``__init__`` dict   ``OrderedDict(dict_data)``                               3.1
    ``__setitem__``     ``ordereddict[-1] = False``                              2.9
    ``__getitem__``     ``ordereddict[100]``                                     2.4
    ``update``          ``ordereddict.update(dict_data)``                        2.9
    ``__iter__``        ``list(ordereddict)``                                    5.7
    ``__contains__``    ``100 in ordereddict``                                   1.8
    ==================  =================================  =========================

    Numbers larger than 1 mean cyorderedict is faster. To run yourself, use
    ``cyordereddict.benchmark()``.

License:
    MIT. cyordereddict is largely adapted from the Python standard library,
    which is available under the Python Software Foundation License.
.. _data-types:

Data Types
==========

    Array API specification for supported data types.

A conforming implementation of the array API standard must provide and support the following data types.

bool
----

Boolean (``True`` or ``False``).

int8
----

An 8-bit signed integer whose values exist on the interval ``[-128, +127]``.

int16
-----

A 16-bit signed integer whose values exist on the interval ``[−32,767, +32,767]``.

int32
-----

A 32-bit signed integer whose values exist on the interval ``[−2,147,483,647, +2,147,483,647]``.

int64
-----

A 64-bit signed integer whose values exist on the interval ``[−9,223,372,036,854,775,807, +9,223,372,036,854,775,807]``.

uint8
-----

An 8-bit unsigned integer whose values exist on the interval ``[0, +255]``.

uint16
------

A 16-bit unsigned integer whose values exist on the interval ``[0, +65,535]``.

uint32
------

A 32-bit unsigned integer whose values exist on the interval ``[0, +4,294,967,295]``.

uint64
------

A 64-bit unsigned integer whose values exist on the interval ``[0, +18,446,744,073,709,551,615]``.

float32
-------

IEEE 754 single-precision (32-bit) binary floating-point number (see IEEE 754-2019).

float64
-------

IEEE 754 double-precision (64-bit) binary floating-point number (see IEEE 754-2019).

complex64
---------

Single-precision (64-bit) complex floating-point number whose real and imaginary components must be IEEE 754 single-precision (32-bit) binary floating-point numbers (see IEEE 754-2019).

complex128
----------

Double-precision (128-bit) complex floating-point number whose real and imaginary components must be IEEE 754 double-precision (64-bit) binary floating-point numbers (see IEEE 754-2019).

.. note::
   IEEE 754-2019 requires support for subnormal (a.k.a., denormal) numbers, which are useful for supporting gradual underflow. However, hardware support for subnormal numbers is not universal, and many platforms (e.g., accelerators) and compilers support toggling denormals-are-zero (DAZ) and/or flush-to-zero (FTZ) behavior to increase performance and to guard against timing attacks.

   Accordingly, subnormal behavior is left unspecified and, thus, implementation-defined. Conforming implementations may vary in their support for subnormal numbers.

.. note::
   A conforming implementation of the array API standard may provide and support additional data types beyond those described in this specification.

.. _data-type-objects:

Data Type Objects
-----------------

Data types ("dtypes") are objects which are used as ``dtype`` specifiers in functions and methods (e.g., ``zeros((2, 3), dtype=float32)``).

.. note::
   A conforming implementation may add additional methods or attributes to data type objects beyond those described in this specification.

.. note::
   Implementations may provide other ways to specify data types (e.g., ``zeros((2, 3), dtype='f4')``) which are not described in this specification; however, in order to ensure portability, array library consumers are recommended to use data type objects as provided by specification conforming array libraries.

A conforming implementation of the array API standard must provide and support data type objects having the following attributes and methods.

Methods
~~~~~~~

..
  NOTE: please keep the functions in alphabetical order

.. currentmodule:: array_api.data_types

.. autosummary::
   :toctree: generated
   :template: method.rst

   __eq__


.. _data-type-defaults:

Default Data Types
------------------

A conforming implementation of the array API standard must define the following default data types.

-   a default real-valued floating-point data type (either ``float32`` or ``float64``).
-   a default complex floating-point data type (either ``complex64`` or ``complex128``).
-   a default integer data type (either ``int32`` or ``int64``).
-   a default array index data type (either ``int32`` or ``int64``).

The default real-valued floating-point and complex floating-point data types must be the same across platforms.

The default complex floating-point point data type should match the default real-valued floating-point data type. For example, if the default real-valued floating-point data type is ``float32``, the default complex floating-point data type must be ``complex64``. If the default real-valued floating-point data type is ``float64``, the default complex floating-point data type must be ``complex128``.

The default integer data type should be the same across platforms, but the default may vary depending on whether Python is 32-bit or 64-bit.

The default array index data type may be ``int32`` on 32-bit platforms, but the default should be ``int64`` otherwise.

.. note::
   The default data types should be clearly defined in a conforming library's documentation.

.. _data-type-categories:

Data Type Categories
--------------------

For the purpose of organizing functions within this specification, the following data type categories are defined.

.. note::
   Conforming libraries are not required to organize data types according to these categories. These categories are only intended for use within this specification.


Numeric Data Types
~~~~~~~~~~~~~~~~~~

``int8``, ``int16``, ``int32``, ``int64``, ``uint8``, ``uint16``, ``uint32``, ``uint64``, ``float32``, ``float64``, ``complex64``, and ``complex128``.

Real-valued Data Types
~~~~~~~~~~~~~~~~~~~~~~

``int8``, ``int16``, ``int32``, ``int64``, ``uint8``, ``uint16``, ``uint32``, ``uint64``, ``float32``, and ``float64``.

Integer Data Types
~~~~~~~~~~~~~~~~~~

``int8``, ``int16``, ``int32``, ``int64``, ``uint8``, ``uint16``, ``uint32``, and ``uint64``.

Floating-point Data Types
~~~~~~~~~~~~~~~~~~~~~~~~~

``float32``, ``float64``, ``complex64``, and ``complex128``.

Real-valued Floating-point Data Types
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

``float32`` and ``float64``.

Complex Floating-point Data Types
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

``complex64`` and ``complex128``.

Boolean Data Types
~~~~~~~~~~~~~~~~~~

``bool``.

=====================================
Clang 3.4 (In-Progress) Release Notes
=====================================

.. contents::
   :local:
   :depth: 2

Written by the `LLVM Team <http://llvm.org/>`_

.. warning::

   These are in-progress notes for the upcoming Clang 3.4 release. You may
   prefer the `Clang 3.3 Release Notes
   <http://llvm.org/releases/3.3/tools/clang/docs/ReleaseNotes.html>`_.

Introduction
============

This document contains the release notes for the Clang C/C++/Objective-C
frontend, part of the LLVM Compiler Infrastructure, release 3.4. Here we
describe the status of Clang in some detail, including major
improvements from the previous release and new feature work. For the
general LLVM release notes, see `the LLVM
documentation <http://llvm.org/docs/ReleaseNotes.html>`_. All LLVM
releases may be downloaded from the `LLVM releases web
site <http://llvm.org/releases/>`_.

For more information about Clang or LLVM, including information about
the latest release, please check out the main please see the `Clang Web
Site <http://clang.llvm.org>`_ or the `LLVM Web
Site <http://llvm.org>`_.

Note that if you are reading this file from a Subversion checkout or the
main Clang web page, this document applies to the *next* release, not
the current one. To see the release notes for a specific release, please
see the `releases page <http://llvm.org/releases/>`_.

What's New in Clang 3.4?
========================

Some of the major new features and improvements to Clang are listed
here. Generic improvements to Clang as a whole or to its underlying
infrastructure are described first, followed by language-specific
sections with improvements to Clang's support for those languages.

Last release which will build as C++98
--------------------------------------

This is expected to be the last release of Clang which compiles using a C++98
toolchain. We expect to start using some C++11 features in Clang starting after
this release. That said, we are committed to supporting a reasonable set of
modern C++ toolchains as the host compiler on all of the platforms. This will
at least include Visual Studio 2012 on Windows, and Clang 3.1 or GCC 4.7.x on
Mac and Linux. The final set of compilers (and the C++11 features they support)
is not set in stone, but we wanted users of Clang to have a heads up that the
next release will involve a substantial change in the host toolchain
requirements.

Note that this change is part of a change for the entire LLVM project, not just
Clang.

Major New Features
------------------

Improvements to Clang's diagnostics
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Clang's diagnostics are constantly being improved to catch more issues,
explain them more clearly, and provide more accurate source information
about them. The improvements since the 3.3 release include:

-  ...

New Compiler Flags
------------------

- Clang no longer special cases -O4 to enable lto. Explicitly pass -flto to
  enable it.
- Command line "clang -O3 -flto a.c -c" and "clang -emit-llvm a.c -c" 
  are no longer equivalent.
- Clang now errors on unknown -m flags (``-munknown-to-clang``),
  unknown -f flags (``-funknown-to-clang``) and unknown
  options (``-what-is-this``).

C Language Changes in Clang
---------------------------

- Added new checked arithmetic builtins for security critical applications.

C11 Feature Support
^^^^^^^^^^^^^^^^^^^

...

C++ Language Changes in Clang
-----------------------------

- Fixed an ABI regression, introduced in Clang 3.2, which affected
  member offsets for classes inheriting from certain classes with tail padding.
  See PR16537.

- ...

C++11 Feature Support
^^^^^^^^^^^^^^^^^^^^^

...

Objective-C Language Changes in Clang
-------------------------------------

...

OpenCL C Language Changes in Clang
----------------------------------

- OpenCL C "long" now always has a size of 64 bit, and all OpenCL C
  types are aligned as specified in the OpenCL C standard. Also,
  "char" is now always signed.

Internal API Changes
--------------------

These are major API changes that have happened since the 3.3 release of
Clang. If upgrading an external codebase that uses Clang as a library,
this section should help get you past the largest hurdles of upgrading.

Wide Character Types
^^^^^^^^^^^^^^^^^^^^

The ASTContext class now keeps track of two different types for wide character
types: WCharTy and WideCharTy. WCharTy represents the built-in wchar_t type
available in C++. WideCharTy is the type used for wide character literals; in
C++ it is the same as WCharTy, but in C99, where wchar_t is a typedef, it is an
integer type.

...

libclang
--------

...

Static Analyzer
---------------

The static analyzer (which contains additional code checking beyond compiler
warnings) has improved significantly in both in the core analysis engine and 
also in the kinds of issues it can find.

Core Analysis Improvements
==========================

- ...

New Issues Found
================

- ...

Python Binding Changes
----------------------

The following methods have been added:

-  ...

Significant Known Problems
==========================

Additional Information
======================

A wide variety of additional information is available on the `Clang web
page <http://clang.llvm.org/>`_. The web page contains versions of the
API documentation which are up-to-date with the Subversion version of
the source code. You can access versions of these documents specific to
this release by going into the "``clang/docs/``" directory in the Clang
tree.

If you have any questions or comments about Clang, please feel free to
contact us via the `mailing
list <http://lists.cs.uiuc.edu/mailman/listinfo/cfe-dev>`_.

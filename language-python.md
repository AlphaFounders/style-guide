# Python Style Guideline

This style guideline is based on [PEP-8][PEP-8] and [PEP-257][PEP-257]. But removed some **optional** part to make it more clear.

Except these coding style, a few other best practice we should follow. See [python guide][1] and it's [code style][2] part for more infomation.

[PEP-8]: https://www.python.org/dev/peps/pep-0008
[PEP-257]: https://www.python.org/dev/peps/pep-0257/
[1]: http://docs.python-guide.org/en/latest/
[2]: http://docs.python-guide.org/en/latest/writing/style/

----

## Code lay-out

### Indentation

Use 4 spaces per indentation level.

Continuation lines should align wrapped elements either vertically using Python's implicit line joining inside parentheses, brackets and braces, or using a hanging indent [5] . When using a hanging indent the following considerations should be applied; there should be no arguments on the first line and further indentation should be used to clearly distinguish itself as a continuation line.

Yes:

```python
# Aligned with opening delimiter.
foo = long_function_name(var_one, var_two,
                         var_three, var_four)

# More indentation included to distinguish this from the rest.
def long_function_name(
        var_one, var_two, var_three,
        var_four):
    print(var_one)

# Hanging indents should add a level.
foo = long_function_name(
    var_one, var_two,
    var_three, var_four)
```

No:

```python
# Arguments on first line forbidden when not using vertical alignment.
foo = long_function_name(var_one, var_two,
    var_three, var_four)

# Further indentation required as indentation is not distinguishable.
def long_function_name(
    var_one, var_two, var_three,
    var_four):
    print(var_one)
```

When the conditional part of an if -statement is long enough to require that it be written across multiple lines, it's worth noting that the combination of a two character keyword (i.e. if ), plus a single space, plus an opening parenthesis creates a natural 4-space indent for the subsequent lines of the multiline conditional. This can produce a visual conflict with the indented suite of code nested inside the if -statement, which would also naturally be indented to 4 spaces. This PEP takes no explicit position on how (or whether) to further visually distinguish such conditional lines from the nested suite inside the if -statement. Acceptable options in this situation include, but are not limited to:

```python
# No extra indentation.
if (this_is_one_thing and
    that_is_another_thing):
    do_something()

# Add some extra indentation on the conditional continuation line.
if (this_is_one_thing
        and that_is_another_thing
        and the_third_thing):
    do_something()

# Add a comment, which will provide some distinction in editors
# supporting syntax highlighting.
if (this_is_one_thing and
    that_is_another_thing):
    # Since both conditions are true, we can frobnicate.
    do_something()
```

The closing brace/bracket/parenthesis on multi-line constructs may either line up under the first character of the line that starts the multi-line construct, as in:

```python
my_list = [
    1, 2, 3,
    4, 5, 6,
]
result = some_function_that_takes_arguments(
    'a', 'b', 'c',
    'd', 'e', 'f',
)
```

### Maximum Line Length

Limit all lines to a maximum of 79 characters.

The preferred way of wrapping long lines is by using Python's implied line continuation inside parentheses, brackets and braces. Long lines can be broken over multiple lines by wrapping expressions in parentheses. These should be used in preference to using a backslash for line continuation.

Backslashes may still be appropriate at times. For example, long, multiple with -statements cannot use implicit continuation, so backslashes are acceptable:

```python
with open('/path/to/some/file/you/want/to/read') as file_1, \
     open('/path/to/some/file/being/written', 'w') as file_2:
    file_2.write(file_1.read())
```

Another such case is with assert statements.

Make sure to indent the continued line appropriately. The preferred place to break around a binary operator is after the operator, not before it. Some examples:

```python
class Rectangle(Blob):

    def __init__(self, width, height,
                 color='black', emphasis=None, highlight=0):
        if (width == 0 and height == 0 and
                color == 'red' and emphasis == 'strong' or
                highlight > 100):
            raise ValueError("sorry, you lose")
        if width == 0 and height == 0 and (color == 'red' or
                                           emphasis is None):
            raise ValueError("I don't think so -- values are %s, %s" %
                             (width, height))
        Blob.__init__(self, width, height,
                      color, emphasis, highlight)
```

### Blank Lines

Separate top-level function and class definitions with two blank lines.

Method definitions inside a class are separated by a single blank line.

Extra blank lines may be used (sparingly) to separate groups of related functions. Blank lines may be omitted between a bunch of related one-liners (e.g. a set of dummy implementations).

Use blank lines in functions, sparingly, to indicate logical sections.

Python accepts the control-L (i.e. ^L) form feed character as whitespace; Many tools treat these characters as page separators, so you may use them to separate pages of related sections of your file. Note, some editors and web-based code viewers may not recognize control-L as a form feed and will show another glyph in its place.

### Source File Encoding

Code in the core Python distribution should always use UTF-8 (or ASCII in Python 2).

Files using ASCII (in Python 2) or UTF-8 (in Python 3) should not have an encoding declaration.

In the standard library, non-default encodings should be used only for test purposes or when a comment or docstring needs to mention an author name that contains non-ASCII characters; otherwise, using \x , \u , \U , or \N escapes is the preferred way to include non-ASCII data in string literals.

For Python 3.0 and beyond, the following policy is prescribed for the standard library (see PEP 3131 ): All identifiers in the Python standard library MUST use ASCII-only identifiers, and SHOULD use English words wherever feasible (in many cases, abbreviations and technical terms are used which aren't English). In addition, string literals and comments must also be in ASCII. The only exceptions are (a) test cases testing the non-ASCII features, and (b) names of authors. Authors whose names are not based on the latin alphabet MUST provide a latin transliteration of their names.

Open source projects with a global audience are encouraged to adopt a similar policy.

### Imports

+ Imports should usually be on separate lines, e.g.:
    ```python
    Yes: import os
         import sys
    
    No:  import sys, os
    ```
+ It's okay to say this though:
    ```python
    from subprocess import Popen, PIPE
    ```
+ Imports are always put at the top of the file, just after any module comments and docstrings, and before module globals and constants.
    Imports should be grouped in the following order:

    standard library imports 
    related third party imports
    local application/library specific imports
    You should put a blank line between each group of imports.

    Put any relevant `__all__` specification after the imports
+ Absolute imports are RECOMMENDED, as they are usually more readable and tend to be better behaved. But we can use explicit relative import to import module in the same level, ONLY when the path is too deep:
    ```python
    from myclass import MyClass
    from foo.bar.yourclass import YourClass
    ```

    ```python
    from first.second.third.fourth.fifth import sixth
    # you can use this instead
    import .sixth
    ```
+ Wildcard imports ( from <module> import * ) should be avoided, as they make it unclear which names are present in the namespace, confusing both readers and many automated tools. There is one defensible use case for a wildcard import, which is to republish an internal interface as part of a public API (for example, overwriting a pure Python implementation of an interface with the definitions from an optional accelerator module and exactly which definitions will be overwritten isn't known in advance).

    When republishing names this way, the guidelines below regarding public and internal interfaces still apply.

## Whitespace in Expressions and Statements

### Pet Peeves

Avoid extraneous whitespace in the following situations:

+ Immediately inside parentheses, brackets or braces.
    ```python
    Yes: spam(ham[1], {eggs: 2})
    No:  spam( ham[ 1 ], { eggs: 2 } )
    ```
+ Immediately before a comma, semicolon, or colon:
    ```python
    Yes: if x == 4: print x, y; x, y = y, x
    No:  if x == 4 : print x , y ; x , y = y , x
    ```
+ However, in a slice the colon acts like a binary operator, and should have equal amounts on either side (treating it as the operator with the lowest priority). In an extended slice, both colons must have the same amount of spacing applied. Exception: when a slice parameter is omitted, the space is omitted.
    ```python
    # Yes:
    ham[1:9], ham[1:9:3], ham[:9:3], ham[1::3], ham[1:9:]
    ham[lower:upper], ham[lower:upper:], ham[lower::step]
    ham[lower+offset : upper+offset]
    ham[: upper_fn(x) : step_fn(x)], ham[:: step_fn(x)]
    ham[lower + offset : upper + offset]

    # No:
    ham[lower + offset:upper + offset]
    ham[1: 9], ham[1 :9], ham[1:9 :3]
    ham[lower : : upper]
    ham[ : upper]
    ```
+ Immediately before the open parenthesis that starts the argument list of a function call:
    ```python
    Yes: spam(1)
    No:  spam (1)
    ```
+ Immediately before the open parenthesis that starts an indexing or slicing:
    ```python
    Yes: dct['key'] = lst[index]
    No:  dct ['key'] = lst [index]
    ```
+ More than one space around an assignment (or other) operator to align it with another.

```python
# Yes:
x = 1
y = 2
long_variable = 3

# No: 
x             = 1
y             = 2
long_variable = 3
```

### Other Recommendations

+ Always surround these binary operators with a single space on either side: assignment ( = ), augmented assignment ( += , -= etc.), comparisons ( == , < , > , != , <> , <= , >= , in , not in , is , is not ), Booleans ( and , or , not ).
+ If operators with different priorities are used, consider adding whitespace around the operators with the lowest priority(ies). Use your own judgment; however, never use more than one space, and always have the same amount of whitespace on both sides of a binary operator.

```python
# Yes:
i = i + 1
submitted += 1
x = x*2 - 1
hypot2 = x*x + y*y
c = (a+b) * (a-b)

# No:
i=i+1
submitted +=1
x = x * 2 - 1
hypot2 = x * x + y * y
c = (a + b) * (a - b)
```

+ Don't use spaces around the = sign when used to indicate a keyword argument or a default parameter value.

```python
# Yes:
def complex(real, imag=0.0):
    return magic(r=real, i=imag)

# No:
def complex(real, imag = 0.0):
    return magic(r = real, i = imag)
```

+ While sometimes it's okay to put an if/for/while with a small body on the same line, never do this for multi-clause statements. Also avoid folding such long lines!

```python
# Yes: 
if foo == 'blah':
    do_blah_thing()
else:
    do_non_blah_thing()

try:
    something()
finally:
    cleanup()

do_one()
do_two()
do_three(long, argument,
         list, like, this)

# No:
if foo == 'blah': do_blah_thing()
else: do_non_blah_thing()

try: something()
finally: cleanup()

do_one(); do_two(); do_three(long, argument,
                             list, like, this)

```

## Comments

### Block Comments

Block comments generally apply to some (or all) code that follows them, and are indented to the same level as that code. Each line of a block comment starts with a # and a single space (unless it is indented text inside the comment).

Paragraphs inside a block comment are separated by a line containing a single # .

### Inline Comments

DON'T use inline comments!

Inline comments are unnecessary and in fact distracting if they state the obvious. 

No:

```python
x = x + 1                 # Increment x
```

## Docstrings

### One-line Docstrings

One-liners are for really obvious cases. They should really fit on one line. For example:

```python
def kos_root():
    """Return the pathname of the KOS root directory."""
    global _kos_root
    if _kos_root: return _kos_root
    ...
```

Notes:

+ Triple quotes are used even though the string fits on one line. This makes it easy to later expand it.
+ The closing quotes are on the same line as the opening quotes. This looks better for one-liners.
+ There's no blank line either before or after the docstring.

### Multi-line Docstrings

Multi-line docstrings consist of a summary line just like a one-line docstring, followed by a blank line, followed by a more elaborate description. The summary line may be used by automatic indexing tools; it is important that it fits on one line and is separated from the rest of the docstring by a blank line. The summary line may be on the same line as the opening quotes or on the next line. The entire docstring is indented the same as the quotes at its first line (see example below).

Insert a blank line after all docstrings (one-line or multi-line) that document a class -- generally speaking, the class's methods are separated from each other by a single blank line, and the docstring needs to be offset from the first method by a blank line.

```python
class Foo:
  """Simple docstrings"""

  def complex(real=0.0, imag=0.0):
      """Form a complex number.

      Keyword arguments:
      real -- the real part (default 0.0)
      imag -- the imaginary part (default 0.0)
      """
      if imag == 0.0 and real == 0.0:
          return complex_zero
      ...
```

## Naming Conventions

### Names to Avoid

Never use the characters 'l' (lowercase letter el), 'O' (uppercase letter oh), or 'I' (uppercase letter eye) as single character variable names.

In some fonts, these characters are indistinguishable from the numerals one and zero. When tempted to use 'l', use 'L' instead.

### Package and Module Names

Modules should have short, all-lowercase names. Underscores can be used in the module name if it improves readability. Python packages should also have short, all-lowercase names, although the use of underscores is discouraged.

### Class Names

Class names should normally use the CapWords convention. 

Note some exceptions like `HTTPClient`, but NOT `HttpClient`.

### Function and Method Names

Function and method names should be `lowercase_with_underscores`.

Use one leading underscore only for non-public methods and instance variables.


### Function and Method Arguments

Always use `self` for the first argument to instance methods.

Always use `cls` for the first argument to class methods.

If a function argument's name clashes with a reserved keyword, it is generally better to append a single trailing underscore rather than use an abbreviation or spelling corruption. Thus class_ is better than clss . (Perhaps better is to avoid such clashes by using a synonym.)

### Constants

Constants are usually defined on a module level and written in all capital letters with underscores separating words. Examples include `MAX_OVERFLOW` and `TOTAL` .

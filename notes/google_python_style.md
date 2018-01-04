# Google Python Style Guide
[https://google.github.io/styleguide/pyguide.html](https://google.github.io/styleguide/pyguide.html)
- Run pylint
- Never use catch-all exception catching
- Keep try blocks as small as possible
- List comprehensions are okay for simple cases (don't make crazy ones that are hard to grok)
- Lambdas only for one-liners, they're hard to debug otherwise
- Be aware of default argument quirks (like how they're loaded once, see def foo(a=[]) issues)
- `x = property(__get_method, __set_method, doc="hi")` is cool. @property is cooler, and you can do setters now: `@property def x(self)`, `@x.setter def x(self, value)`
- Avoid power features when possible (reflection, metaclasses, etc.)
- Line length 80, DO NOT use backslash \ continuation
- Docstrings:
```python
      def fetch_bigtable_rows(big_table, keys, other_silly_variable=None):
            """Fetches rows from a Bigtable.
        
            Retrieves rows pertaining to the given keys from the Table instance
            represented by big_table.  Silly things may happen if
            other_silly_variable is not None.
        
            Args:
                big_table: An open Bigtable Table instance.
                keys: A sequence of strings representing the key of each table row
                    to fetch.
                other_silly_variable: Another optional variable, that has a much
                    longer name than the other args, and which does nothing.
        
            Returns:
                A dict mapping keys to the corresponding table row data
                fetched. Each row is represented as a tuple of strings. For
                example:
        
                {'Serak': ('Rigel VII', 'Preparer'),
                 'Zim': ('Irk', 'Invader'),
                 'Lrrr': ('Omicron Persei 8', 'Emperor')}
        
                If a key from the keys argument is missing from the dictionary,
                then that row was not found in the table.
        
            Raises:
                IOError: An error occurred accessing the bigtable.Table object.
            """
            pass
```
- TODO(cpoll) for temp code or 'good-enough' code, always use your name
- One statement per line, but `if foo: bar()` is okay
- Trivial accessors can just be properties
- Naming: _ for protected, __ for private, CamelCase classes/exceptions, allcaps global/class constants, lower_pothole for everything else
- BE CONSISTENT (when editing code, look around. It's worse to have a hodgepodge in a file than to break convention)

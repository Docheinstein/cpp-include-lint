# cpp-include-lint

Since I was tired of having a messy bunch of `#include` at the top of my C++ 
sources I decided to do a script that sorts the `#include` lines of C/C++ files 
with a fair criterion.

The sorting precedence between `#include` lines is the following:
1. header with the same name as this source file
2. headers between square brackets (<>), alphabetically
3. headers between quotes (""), alphabetically

e.g. 

`database.cpp`
```cpp
#include "database.h"
#include <iostream>
#include <string>
#include <unordered_set>
#include <vector>
#include "arguments.h"
#include "logger.h"
#include "manager.h"
#include "timer.h"
```

## INSTALLATION
```
pip install cpp-include-lint
```

## USAGE

```
usage: cpp-include-lint [-h] [-r] [-d] [-f REGEX] [-q] input [output]

Sort #include directives of C/C++ files.

positional arguments:
  input                 input path
  output                output path

optional arguments:
  -h, --help            show this help message and exit
  -r, -R, --recursive   lint all the files in the input folder recursively
  -d, --dry-run         just print the files that would have been linted
  -f REGEX, --filter REGEX
                        filter files to lint using the given regular expression. 
                        The default one is: ".*\.(h|hpp|c|cpp|tpp)"
  -q, --quiet           suppress information messages

```

## EXAMPLES

* Lint a single source file in place
```
cpp-include-lint main.cpp
```

* Lint a single source file writing to another file
```
cpp-include-lint main.cpp /tmp/main.cpp
```

* Lint an entire directory recursively in place
```
cpp-include-lint /home/user/develop/project/src -R
```

* Lint an entire directory recursively to another directory
```
cpp-include-lint /home/user/develop/project/src /tmp/src -R
```


* Lint an entire directory recursively in place using a different file filter
```
cpp-include-lint /home/user/develop/project/src -R -f ".*\.(hxx|cxx)"
```

# YAMA 0005 - fncall token macros

- Author(s): Bhathiya Perera
- Status   : Draft

<!-- different languages for code blocks are used to get maximum syntax matching for free, please ignore -->

## Problem

Macros allow for runtime code generation. Yaksha already supports multiple ways of exposing and defining `C` macros.
However, `C` macros are not easy to use and they are not Yaksha-like.

### Proposed syntax

```python

@macro("fncall")
def printf(t: Array[Token]) -> Array[Token]:
    if len(t) < 1:
        macro_fail("Must have at least 1 token")
        return t
    format_str: Token = t[0]
    if format_str.type != T_STR or format_str.type != T_TRIPLE_STR:
        macro_fail("First token must be a string")
        return t
    # more logic goes here
    return x
      
def main() -> int:
    printf("$ nice $\n", "Hello", "World")
    return 0
```

```python
def main() -> int:
    print("Hello")
    print(" nice ")
    print("World")
    print("\n")
    return 0
```

### Proposed execution
1. Read all files
2. Tokenize
4. Block Analyzer
5. Parse
6. Def/Struct Visitor
7. Apply macros (10000 iterations? or so maybe until files are macro free)
8. Parse
9. Def/Struct Visitor
10. Rest of the steps

### Use case 1 


### Use case 2


## Conclusion



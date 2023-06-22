# YAMA 0008 - Sugar methods

- Author(s): Bhathiya Perera
- Status   : Draft

## Idea 01 - Arrow

```python
@onstack
class Banana:
    color: int
    origin: int
    
def display(b: Ptr[Banana]) -> None:
    return

def main() -> int:
    b: Banana = ...
    b->display()
    return 0
```

## Idea 02 - Dot ✅

```python
@onstack
class Banana:
    color: int
    origin: int
    
def display(b: Ptr[Banana]) -> None:
    return

def main() -> int:
    b: Banana = ...
    b.display()
    return 0
```

if not `@onstack` then it can just use the data type, otherwise it is Ptr.

Going with `.` as it is already valid AST. Additionally, we can find the method during `type checking` and desugar it.

```python
display(getref(b))
```
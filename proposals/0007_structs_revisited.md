# YAMA 0007 - Additional features for structs

- Author(s): Bhathiya Perera
- Status   : Draft

Structures are at the moment can be created as follows

```python
@onstack
class Banana:
    color: int
    origin: int

# Orange is a heap allocated class
class Orange:
    color: int
    origin: int
```

## Item 1 - Allocate single object on heap

```python
a: Ptr[Banana] = make("Banana")

b: Orange = make("Orange")
```

## Item 2 - Create structures or classes

```python
a: Banana = {color: YELLOW, origin: SRI_LANKA} Banana
```

```c
struct Banana a = (struct Banana){.color = YELLOW, .origin = SRI_LANKA};
```

```python
b: Orange = {color: ORANGE, origin: SOUTH_AFRICA} Orange
```

```c
struct Orange* _temp = calloc(1, sizeof(struct Orange));
_temp->color  = ORANGE;
_temp->origin = SOUTH_AFRICA

struct Orange* b = _temp;
```

## Item 3 - Introduce `struct` keyword, desugar to `@onstack class`

```python
struct Banana:
    color: int
    origin: int
```
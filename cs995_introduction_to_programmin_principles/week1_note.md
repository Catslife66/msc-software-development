# Mutable vs Immutable Types

In Python, the data type of an object dictates whether its internal memory can be modified after creation.

## Mutable

Can be altered in place without changing memory address (id).

e.g:

```
nums = [1, 2, 3]
print(id(nums))  # e.g., 4392817280

nums.append(4)  # Modifies the list in-place
print(id(nums))  # Still 4392817280! (Same object in memory)


a = [1, 2, 3]
b = a  # 'b' points to the exact same list object in memory
b.append(99)  # In-place change

print(a)  # [1, 2, 3, 99] — 'a' was modified too!
```

Built-in Types:

- list
- dict
- set

Modifying Behaviour:

Changes happen directly inside the object.

## Immutable

Content cannot change once created.

e.g:

```
text = "hello"
print(id(text))  # 4398123400

# String methods do NOT modify in-place; they return a brand-new string
uppercase_text = text.upper()
print(uppercase_text)  # "HELLO"
print(text)  # "hello" (original is completely unchanged)

# Even reassignment creates a new object:
text = text + " world"
print(id(text))  # 4398129999 (Different ID! The old string was discarded)
```

Built-in Types:

- int
- float
- bool
- str
- tuple

Modifying Behaviour:

Any "update" constructs an entirely new object with a new id.

## Core python conventions

Modify the existing object - in-place operation

```
arr.sort()
```

Before:

```
arr ──→ [5, 2, 8, 1]
```

After:

```
arr ──→ [1, 2, 5, 8]
```

Same list object; changed contents.

Product a new object

```
arr = [5, 2, 8, 1]

new_arr = sorted(arr)
```

Now:

```
arr     ──→ [5, 2, 8, 1]

new_arr ──→ [1, 2, 5, 8]
```

`sorted()` doesn't modify arr. It produces a new sorted list and returns it.

Therefore this works:

```
print(sorted(arr))
```

because `sorted(arr)` actually returns the new list.

The extraction exception:

Compare:

```
arr.append(5)       # modifies arr, returns None
arr.sort()          # modifies arr, returns None
arr.reverse()       # modifies arr, returns None

arr.pop()           # modifies arr AND returns removed value

sorted(arr)         # doesn't modify arr; returns new list
len(arr)            # doesn't modify arr; returns integer
```

So the deeper question whenever you're using an operation is:

> Does this operation modify the existing object, return a new object/value, or both?

## Mental Model

Mutability asks whether the state of an existing object can change.

```
MUTABLE
list / dict / set
       ↓
the existing object's contents can change


IMMUTABLE
int / float / bool / str / tuple
       ↓
the existing object's contents cannot change
       ↓
an apparent "change" normally means producing/referencing another object
```

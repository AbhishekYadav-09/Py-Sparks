👉 Reference

In Python, variables are references to objects in memory, not actual objects.
a = [1, 2, 3]
b = a  # no new copy, just a new reference

Both a and b point to the same list object in memory.
Agar tum b.append(4) karoge → a bhi change ho jayega, kyunki dono same object ko refer kar rahe hain.

👉 Shallow Copy
import copy
a = [1, 2, [3, 4]]
b = copy.copy(a)  # shallow copy

b ek naya outer list banata hai, but inner objects (like [3, 4]) abhi bhi shared reference hain.
b[2].append(5) → ye change a me bhi reflect hoga.

👉 Deep Copy
import copy
a = [1, 2, [3, 4]]
b = copy.deepcopy(a)

Completely independent object create hota hai.
Ab b[2].append(5) sirf b ko affect karega, a ko nahi.



2. Reference Count (Memory Management)
Python uses reference counting + garbage collection.
Har object ke paas ek refcount hota hai (kitne variables us object ko point kar rahe hain).
Jab refcount = 0 ho jata hai → object garbage collector ke through free kar diya jata hai.

👉 Example with sys.getrefcount():
import sys
x = [1, 2, 3]
print(sys.getrefcount(x))  # at least 2 (x + function arg)
ab x delete ho jata hai (del x), aur koi reference nahi bachta, object free ho jata hai.

CPython me internally ek PyObject struct hota hai:
typedef struct _object {
    int ob_refcnt;   // reference count
    struct _typeobject *ob_type; // type info
} PyObject;


3. Slicing & Copying in Python

👉 String slicing (Immutable)
s = "hello"
print(s[1:4])  # "ell"
Naya string object banta hai, kyunki string immutable hai.

👉 List slicing (Mutable)
lst = [1, 2, 3, 4]
sub = lst[1:3]  # [2, 3]

Ye ek shallow copy banata hai.
Matlab sub ek naya list hai, lekin agar elements mutable hain (e.g. list of lists), toh unka reference hi copy hota hai.

a = [[1, 2], [3, 4]]
b = a[:]
b[0].append(99)
print(a)  # [[1, 2, 99], [3, 4]]

Quick Recap
Reference: Variable just points to the same object.
Shallow Copy: New outer object, inner elements still referenced.
Deep Copy: Fully independent object.
Reference Count: Python frees memory when no references exist.
Slicing: Creates shallow copies for lists, new objects for strings.
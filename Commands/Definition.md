# Definition Command

The `def` command creates a new top level definition consisting of a name,
a type, and a body.

A definition begins with an optional set of qualifiers (detailed in ...) followed
by the keyword `def`, a definition name, a set of parameters, and a return type.

A simple example is using a definition as a top-level variable, where we have no qualifiers
or parameters.

```lean
def x : int := 0
```

The definition command has many syntactic features which are elaborated away by Lean, its
primary feature is supporting the definition of functions by a set of recursive equations.

# Parameters

A definition may have zero or more parameters, which appear directly after its name, and before its
type as below.

```lean
def add (m : nat) : nat -> nat
| nat.zero := m
| (nat.succ n) := nat.succ (add n)
```

The parameters are fixed for all recursive calls to the definition, this design may initially seem strange,
but it is actually quite useful in dependent type theory. A common example is fixing types in a
polymorphic definition.

```lean
def map {A B : Type} (f : A -> B) : list A -> list B
| [] := []
| (x :: xs) := f x :: map xs
```

For example in `map` we do not need to supply any of the parameters to the recursive call including the function
which should be invariant over all calls to `map`.

# Pattern Matching

# Dependent Pattern Matching

# Universe Parameters
... TODO ...


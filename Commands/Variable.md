# Variable Command

The `variable` command creates a new top level definition consisting of a name and a type, but no body definition.

As an example, we can create a type variable T:

```lean
variable T : Type
```

Now, when a later definition refers to T, it will be automatically added as a parameter of that definition:

```lean
def identity (x : T) : T := x

#check f -- identity : Π (T : Type), T → T
```

For `variable` this parameter addition happens immediately, so in the future to use function `identity` you must supply a value for T:

```lean
def identityt' (x : T) : T := identity T x
def identitynat (x : nat) : nat := identity nat x
```

We also could have made our type variable implicit:

```lean
variable {T: Type}

def identity (x : T) : T := x

#check identity -- identity : ?M_1 → ?M_1

def identityt' (x : T) : T := identity x
def identitynat (x : nat) : nat := identity x
```

When multiple variables are used in the same definition they appear as arguments in the order they are _defined_.

```lean
variable a : nat
variable T : Type
variable b : bool
variable t : T
variable f : T -> T

def useall := ((a = 0) || b, t)

#check useall -- useall : ℕ → Π (T : Type), bool → T → bool × T
```

If you wish to use a variable whose _type_ has type `Prop`, you must `include` that variable before using it:

```lean
variables x y : nat
variable xy : x = y
include xy 

lemma xyeq : x = y :=
begin
 assumption
end
```

Within the context of the proof, you will be able to see xy only if you use the `include` statement. Similarly, you must include typclass instances if you wish typeclass inference to discover them. Alternately, a typeclass instance will automatically be included if it isn't given a name:

```lean
variable T : Type
variable [has_zero T]

variable T2 : Type
variable [T2z : has_zero T2]
include T2z

def zero := @has_zero.zero T
def zero2 := @has_zero.zero T2
```


#Simp Attributes

User attributes can be defined for use with [simp](../Tactics/simp). This allows definitions to be grouped together such that they can all be simplified with a single application

The following statement introduces the name of a new simp attribute

```lean
run_cmd mk_simp_attr `mysimp
```

Now new (or old) definitions can be given this attribute:

```lean
@[mysimp]
def myadd (a b :nat) : nat := a + b
attribute [mysimp] nat.add
```

Then the simp attribute can be passed to the `simp` tactic using the `with` keyword:

```lean
lemma add11 : myadd 1 1 = 2 :=
begin
simp with mysimp
end
```
# Parameter Command

A parameter is similar to a [Variable](Variable.md), but it is required to occur within a [Section](TODO). Parameters are automatically applied to definitions that use them until the section is closed. From the outside of a section, a `parameter` behaves exactly like a variable. 

```lean
section

parameter T : Type

def identity (x : T) : T := x

#check identity -- identity : T → T

def identityt' (x : T) : T := identity x

#check _root_.identity --identity : Π (T : Type), T → T

def identitynat (x : nat) : nat := _root_.identity nat x

end
```

Any definitions that use a `parameter` can be accessed prior to automatic application to there argument by qualifying their name with `_root_.`

Defnitions that are automatically applied are not valid simplification levels, so the `_root_.` form should be used instead:

```lean
lemma identity_identity : forall x, identity x = x :=
begin
simp [_root_.identity]
end
```
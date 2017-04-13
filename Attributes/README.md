# Attributes

Lean has a generic mechanism for attaching metadata to declarations in the environment, these
are known as `attribute`s.

An attribute allows us to communicate information to the theorem prover, tactics,compilers,
or users.

The set of standard attributes exposed by Lean and its standard library are detailed below.

Attributes can either be `local` or `global`, a local attribute is only visible in the file
local environment, while a global attribute is visible in all files.

You can attach a global attribute to a name using the command `attribute [attr] name`, a
local attribute can be declared by prefixing the command with `local`, `local attribute [attr] name`.

Lean also supports attribute shorthand for attaching attributes to definitions at their declaration
site.

```lean
@[attr] def name : T := ...
```

It is possible for users to declare their own attributes ... elaborate here ...

list attributes here? can we auto generate this?

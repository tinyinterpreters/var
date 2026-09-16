# VAR

VAR extends [IF](https://github.com/tinyinterpreters/if) with variable expressions:

```txt
x
```

A variable has a name, but its value comes from the environment in which it is evaluated.

VAR starts with this environment:

```txt
x ↦ VNumber 10
v ↦ VNumber 5
i ↦ VNumber 1
```

Variables can also appear anywhere an expression is expected:

```txt
if zero?(-(5, v)) then i else v
```

VAR lets programs refer to predefined names, but they cannot introduce new names themselves yet.

For a closer look, read [VAR: Variables and Environments](https://blog.tinyinterpreters.dev/posts/var/).

To try it, you'll need [Nix](https://zero-to-nix.com/start/install/) with flakes enabled.

```bash
nix develop
elm repl
```

Then:

```elm
import VAR.Interpreter as I

I.run "x"
-- Ok (VNumber 10)

I.run "y"
-- Err (RuntimeError (IdentifierNotFound "y"))

I.run "if zero?(-(5, v)) then i else v"
-- Ok (VNumber 1)
```

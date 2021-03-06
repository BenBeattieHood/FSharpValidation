# FSharpResult

General validation functions and monad

Usage:
```
open Result

let getUser id =
    DB.getUser id
    |> Validation.ofOption "Cannot load user"

    
let displayNameResult =
    result {
        let! user = getUser 32

        return sprintf "%s %s" user.firstName user.lastName
    }


match displayNameResult with
| Ok displayName ->
    displayName
    |> sprintf "Hi %s!"

| Error error ->
    error
    |> sprintf "Error: %s"

|> System.Console.WriteLine
```

Huge thanks to the FSharpx validated code, which this is really just a rehash of, minus some bits I didn't agree with (Choice), plus some helpful things around options and sequences.

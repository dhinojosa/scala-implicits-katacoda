`implicit`s are there for us to use for whatever use-case.  But `implicit`s are also already in use in the language.  In this scenario, we discover meaningful ways in which `implicit`s are in use:

1. The Arrow (`->`) Wrapper
2. Rich Primitive Wrappers
3. `BigInt` Conversions
4. `BigInt` Wrappers
5. Converting Java to Scala Collections
6. Ordering a `List`

Knowing some of the ways that Scala makes use of these wrappers enforces understanding how to use some of your own `implicit`s

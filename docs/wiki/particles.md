# lbuilder:particle
## lbuilder:particle:literal (l)
Matches the string passed literally. Use `lbuilder.l` to create one.
```lua
-- Anonymous literal
local literal = lbuilder.l "Hello"
-- Named literal
local namedLiteral = lbuilder.l ("example:hello", "Hello")
```
> Since 1.1, this will escape all magic characters

## lbuilder:particle:normal (n)
Matches the string passed as a pattern. Use `lbuilder.n` to create one.

## lbuilder:particle:set (s)
Creates a set of characters, supports ranges. Use `lbuilder.s` to create one.
```lua
-- Anonymous sets
local vowels   = lbuilder.s "aeiou"
local alphabet = lbuilder.s "a-z"
-- Named sets
local _alphabet = lbuilder.s ("alphabet", "a-z")
-- Negated sets
local notAlphabet = lbuilder.s "a-z" (true)
```

## lbuilder:particle:capture (c)
Creates a capture, supports ranges. Use `lbuilder.c` to create one.
```lua
-- Anonymous captures
local cvowels = lbuilder.c (vowels)
-- Named captures
local calphabet = lbuilder.c ("alphabet", alphabet)
```

# Operators
## `+` operator
### l + l
Joins two literals or normals.
`l+l => ll`
### s + s
Joins two sets.
`s+s => [ss]`

## `/` operator
### p/n
Repeats the particle n times.
`p/3 => ppp`
### p/-n
Repeats the literal no more than n times.
`p/-3 => ppp[^p]`
### p/'+'
Match the set once or more, as much as possible.
`p/'+' => p+`
> Only works for literals and sets.
### p/'-'
Match the set zero or more, as less as possible.
`p/'-' => p-`
> Only works for literals and sets.
### p/'?'
Optionally match the set.
`p/'?' => p?`
> Only works for literals and sets.

### p/'`*`'
Match the set zero or more, as much as possible.
`p/'*' => p*`
> Only works for literals and sets

## `-` operator
### -s
Negates a set.
`-s => [^s]`

## `#` operator
### #l
Creates a pattern from the literal.
`#l => P (l)`

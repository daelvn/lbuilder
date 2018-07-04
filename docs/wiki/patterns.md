# lbuilder:pattern
You can create a pattern using `lbuilder.P`. You can create named patterns as well in the manner of particles.

## `+` operator
Joins two patterns.
`P/pp+/ + P/[p]/ => P/pp+[p]/`
## `..` operator
Joins two patterns and turns them into captures.
`P/pp+/ .. P/[p]/ => P/(pp+)([p])/`
## `%` operator
Tests the pattern.
`P % str => bool`
## `<=` operator
Creates a capture table with the matches.
`P <= str => {}`
## `/` operator
Matches the occurences of the pattern in string and replaces them with another.
`P /str/rep/n => str`
`P /str/fn/n => str`
`P /str/rep/bool => str`
`P /str/fn/bool => str`

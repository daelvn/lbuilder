# Examples
In the following examples, we don't know the actual string from code.
## Example 1
String: `:str :ee :oo`  
Desired result: `"str" "ee" "oo"`  
Conditions: Must print `str`, `ee`, `oo` to screen.
### Without lbuilder
```lua
for m in str:gmatch ":([a-z]+)" do
  print (m)
  str = str:gsub (":"..m, '"%1"')
end
-- OR --
str = str:gsub (":"..m, function (cap)
  print (cap)
  return '"'..cap..'"'
)
```
### With lbuilder
```lua
str = P ( l ":" + c (s "a-z"\'+') ) /str/function (cap)
  print (cap)
  return '"'..cap..'"'
end/true
```

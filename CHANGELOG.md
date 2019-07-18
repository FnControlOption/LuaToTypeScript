## Version 0.0.3

Top level return statements transform into `export = ...`.

```lua
local x = 0
function func()
    return 5
end
return x
```

```ts
let x = 0;
function func() {
    return 5;
}
export = 0;
```

And `@classmod` generates a TypeScript class.

All function declarations that are added to a table are considered functions.

```lua
-- @classmod
local MyClass = {}

function MyClass:method() end

return MyClass
```

This transforms into:

```ts
class MyClass {
    method(): number { }
}
export = myclass;
```

Other than that, bug-fixes regarding how tags are obtained.

## Version 0.0.2

First NPM release!

Can be installed with:

```sh
yarn global add lua-to-typescript
# or
npm install -g lua-to-typescript
```

Can then you can use the following command on Lua files to transform them to TypeScript code:

```sh
ltts main.lua module.lua
# Creates main.ts and module.ts
```

Type annotations are also considered when transpiling functions.

```lua
-- @tparam number x
-- @tparam number y
-- @treturn number
-- @treturn number
function xy(x, y)
    return x + 1, y + 2
end

-- @type number
local x = 0
```
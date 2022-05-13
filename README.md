## Usage Example

```lua
local switch, case, default = require(LuaSwitch).getFunctions()
local myUnknownPet = if math.random(1, 2) == 1 then "dog" else "cat"

switch (myUnknownPet) {
    case "dog" (function(stop)
        warn("My pet is a dog!")
        stop() -- skip default and stop to check the other cases, but doesn't stop the execution of the function
    end)

    case "cat" (function(stop)
        warn("My pet is a cat!")
        stop() 
    end)

    default(function()
        print("I don't know what my pet is :(")
    end)
}
```

### Case Stacking
```lua
local switch, case, default = require(LuaSwitch).getFunctions()
local value = 0

switch("B") {
	case "A", -- Will execute case C
	case "B", -- Will execute case C
	case "C" (function()
		value = 2
	end),

	default (function()
		value -= 1
	end)
}
```
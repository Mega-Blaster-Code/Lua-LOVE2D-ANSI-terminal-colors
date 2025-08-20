local module = {}

module.keys = {
    reset = 0, -- reset

    -- misc
    bright = 1,
    dim = 2,
    underline = 4,
    blink = 5,
    reverse = 7,
    hidden = 8,

    -- fg colors
    black = 30,
    red = 31,
    green = 32,
    yellow = 33,
    blue = 34,
    magenta = 35,
    cyan = 36,
    white = 37,

    -- bg colors
    blackbg   = 40,
    redbg     = 41,
    greenbg   = 42,
    yellowbg  = 43,
    bluebg    = 44,
    magentabg = 45,
    cyanbg    = 46,
    whitebg   = 47
}

local specialChar = "\27"

function module.getSC(name)
    if not module.keys[name] then
        return ""
    end
    return specialChar .. "[" .. module.keys[name] .. "m"
end

function module.color(input)
    input = input:gsub("%${(.-)}", function(content)
        content = content:split(",")
        local result = ""

        for i, str in ipairs(content) do
            str = str:strip()
            result = result .. module.getSC(str)
        end

        return result
    end)

    return input .. specialChar .. "[0m"
end

return module.color

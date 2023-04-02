if game:GetService("Workspace").Island:FindFirstChild("Legacy Island1") or game:GetService("Workspace").Island:FindFirstChild("Legacy Island2") or game:GetService("Workspace").Island:FindFirstChild("Legacy Island3") or game:GetService("Workspace").Island:FindFirstChild("Legacy Island4") or game:GetService("Workspace").Island:FindFirstChild("Sea King Thunder") or game:GetService("Workspace").Island:FindFirstChild("Sea King Lava") or game:GetService("Workspace").Island:FindFirstChild("Sea King Water") or game:GetService("Workspace").GhostMonster:FindFirstChild("Ghost Ship") then
    


  
 local date = os.date("*t")
 local hour = (date.hour) % 24
 local ampm = hour < 12 and "AM" or "PM"
 local timezone = os.date("%X")
local Moon;
local Job = game.JobId
local PlayerCount = #game.Players:GetPlayers()

if game:GetService("Workspace").SeaMonster:FindFirstChild("SeaKing").Humanoid.Health > 0  then
    Sk = "Seaking Not die"
elseif  game:GetService("Workspace").Island:FindFirstChild("Legacy Island1") then
    Sk = ""..game:GetService("Workspace").Island["Legacy Island1"].ClockTime.SurfaceGui.Countdown.Text
    elseif  game:GetService("Workspace").Island:FindFirstChild("Legacy Island2") then
    Sk = ""..game:GetService("Workspace").Island["Legacy Island2"].ClockTime.SurfaceGui.Countdown.Text
    elseif  game:GetService("Workspace").Island:FindFirstChild("Legacy Island3") then
    Sk = ""..game:GetService("Workspace").Island["Legacy Island3"].ClockTime.SurfaceGui.Countdown.Text
    elseif  game:GetService("Workspace").Island:FindFirstChild("Legacy Island4") then
    Sk = ""..game:GetService("Workspace").Island["Legacy Island4"].ClockTime.SurfaceGui.Countdown.Text
end
    
  
    if  game:GetService("Workspace").Island:FindFirstChild("Legacy Island1") or game:GetService("Workspace").Island:FindFirstChild("Legacy Island2") or game:GetService("Workspace").Island:FindFirstChild("Legacy Island3") or game:GetService("Workspace").Island:FindFirstChild("Legacy Island4") then
    Mirage = "🟢 เกิด"

else
    Mirage = "🔴 ไม่เกิด"
end
if game:GetService("Workspace").Island:FindFirstChild("Sea King Thunder") or game:GetService("Workspace").Island:FindFirstChild("Sea King Lava") or game:GetService("Workspace").Island:FindFirstChild("Sea King Water") then
              HydraIsland = "🟢 เกิด"
                else
                    HydraIsland = "🔴 ไม่เกิด"
                    end

if game:GetService("Workspace").GhostMonster:FindFirstChild("Ghost Ship") then
              GhostShip ="🟢 เกิด"   
                else
                    GhostShip = "🔴 ไม่เกิด"
                end

Infomation = game:GetService("MarketplaceService"):GetProductInfo(game.PlaceId)
NameGames = Infomation.Name
_G.wephook = "https://discordapp.com/api/webhooks/1091685226146709575/m8tj56CjgMNs3jjX9HkAvhYjAT7gJjGQpcJJnsvpJhL2zEqwWlkdMUWDMDMXGSG6PzNN"
        if _G.wephook ~= "" then
            pcall(function()
                local url =
                _G.wephook
                local data = {
                  ["content"] = "@everyone",
                  ["embeds"] = {
                      {   
                          ["author"] = {
                              ["name"] = "Web Hook King Legazy"
                          },
                          ["type"] = "rich",
                          ["title"] = "ถ้ามีอย่างไดอย่างนึงเกิด = ส่ง",
                          ["color"] = tonumber(0x13da),
                          ["fields"] = {
                              {
                                  ["name"] = "Time Status ⌚",
                                  ["value"] = "```Time : "..timezone.."```"
                              },
                          {
                                  ["name"] = "SeaKing 💩:",
                             ["value"] = "```SeaKing is : "..Mirage.."```"
                              },
                                  
                              {
                                  ["name"] = "Time SeaKing ?:",
                                  ["value"] = "```Time SeaKing is : "..Sk.."```"
                              },
                          {
                                  ["name"] = "Hydra 👾:",
                                  ["value"] = "```Hydra is : "..HydraIsland.."```"
                              },
                          
                          {
                                  ["name"] = "GhostShip 🚢:",
                                  ["value"] = "```GhostShip is : "..GhostShip.."```"
                              },
                              {
                                  ["name"] = "Players In Server 👨‍👨‍👧‍👧",
                                  ["value"] = "```Player : "..PlayerCount.."/12".."```"
                              },
                              {
                                  ["name"] = "Job Id:",
                                  ["value"] = "```"..game.JobId.."```"
                              },
                          }
                      }
                  }
               }
               local newdata = game:GetService("HttpService"):JSONEncode(data)
               
               local headers = {
                  ["content-type"] = "application/json"
               }
               request = http_request or request or HttpPost or syn.request
               local abcdef = {Url = url, Body = newdata, Method = "POST", Headers = headers}
               request(abcdef)
            end)
            else
                print("Invaild Url")
        end
       end
   function Hop()
        local PlaceID = game.PlaceId
        local AllIDs = {}
        local foundAnything = ""
        local actualHour = os.date("!*t").hour
        local Deleted = false
        function TPReturner()
            local Site;
            if foundAnything == "" then
                Site = game.HttpService:JSONDecode(game:HttpGet('https://games.roblox.com/v1/games/' .. PlaceID .. '/servers/Public?sortOrder=Asc&limit=100'))
            else
                Site = game.HttpService:JSONDecode(game:HttpGet('https://games.roblox.com/v1/games/' .. PlaceID .. '/servers/Public?sortOrder=Asc&limit=100&cursor=' .. foundAnything))
            end
            local ID = ""
            if Site.nextPageCursor and Site.nextPageCursor ~= "null" and Site.nextPageCursor ~= nil then
                foundAnything = Site.nextPageCursor
            end
            local num = 0;
            for i,v in pairs(Site.data) do
                local Possible = true
                ID = tostring(v.id)
                if tonumber(v.maxPlayers) > tonumber(v.playing) then
                    for _,Existing in pairs(AllIDs) do
                        if num ~= 0 then
                            if ID == tostring(Existing) then
                                Possible = false
                            end
                        else
                            if tonumber(actualHour) ~= tonumber(Existing) then
                                local delFile = pcall(function()
                                    AllIDs = {}
                                    table.insert(AllIDs, actualHour)
                                end)
                            end
                        end
                        num = num + 1
                    end
                    if Possible == true then
                        table.insert(AllIDs, ID)
                        wait()
                        pcall(function()
                            wait()
                            game:GetService("TeleportService"):TeleportToPlaceInstance(PlaceID, ID, game.Players.LocalPlayer)
                        end)
                        wait(4)
                    end
                end
            end
        end
        function Teleport() 
            while wait() do
                pcall(function()
                    TPReturner()
                    if foundAnything ~= "" then
                        TPReturner()
                    end
                end)
            end
        end
        Teleport()
    end
    Hop()

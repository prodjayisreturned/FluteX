 Rayfield = loadstring(game:HttpGet('https://sirius.menu/rayfield'))()

-- Create the main window
local Window = Rayfield:CreateWindow({
   Name = "Main",
   Icon = 0,
   LoadingTitle = "Made By prodjay",
   LoadingSubtitle = "FluteX Hub is cool",
   Theme = "Default",
   DisableRayfieldPrompts = false,
   DisableBuildWarnings = false,
   ConfigurationSaving =-- Load Rayfield UI Library
local {
      Enabled = true,
      FolderName = nil,
      FileName = "Big Hub"
   },
   Discord = {
      Enabled = false,
      Invite = "noinvitelink",
      RememberJoins = true
   },
   KeySystem = false,
   KeySettings = {
      Title = "FluteX Hub",
      Subtitle = "Key System",
      Note = "No method of obtaining the key is provided",
      FileName = "Key",
      SaveKey = true,
      GrabKeyFromSite = false,
      Key = {"Hello"}
   }
})

-- Create the main tab
local MainTab = Window:CreateTab("Main", 4483362458)

-- Infinite Yield Button
MainTab:CreateButton({
   Name = "Infinite yield",
   Callback = function()
      loadstring(game:HttpGet("https://raw.githubusercontent.com/EdgeIY/infiniteyield/master/source"))()
   end,
})

-- Infinite Jump Toggle
MainTab:CreateToggle({
   Name = "Infinite jump (T to enable/disable inf jump and F to enable/disable anti-jump bypass)",
   CurrentValue = false,
   Flag = "Toggle1",
   Callback = function()
      -- Infinite Jump and Anti-Jump Bypass Logic goes here
   end,
})

-- Walkspeed Slider
MainTab:CreateSlider({
   Name = "Walkspeed",
   Range = {16, 1000},
   Increment = 10,
   Suffix = "Walkspeed",
   CurrentValue = 16,
   Flag = "WalkspeedSlider",
   Callback = function(v)
      game.Players.LocalPlayer.Character.Humanoid.WalkSpeed = v
   end,
})

-- JumpPower Slider
MainTab:CreateSlider({
   Name = "JumpPower",
   Range = {50, 500},
   Increment = 10,
   Suffix = "JumpPower",
   CurrentValue = 50,
   Flag = "JumpPowerSlider",
   Callback = function(v)
      game.Players.LocalPlayer.Character.Humanoid.JumpPower = v
   end,
})

-- Game-Specific Script Hub Tab
local GameTab = Window:CreateTab("Games", 4483362458)

-- Game Hubs based on PlaceId
local PlaceId = game.PlaceId
local GameHubs = {
   [142823291] = { -- Murder Mystery 2
      Name = "Murder Mystery 2",
      Hubs = {
         {Name = "Eclipse", Url = "https://raw.githubusercontent.com/Ethanoj1/EclipseMM2/master/Script"},
         {Name = "Xhub", Url = "https://raw.githubusercontent.com/Au0yX/Community/main/XhubMM2"},
         {Name = "Vynixu", Url = "https://raw.githubusercontent.com/Vynixu/Utilities/main/MM2.lua"}
      }
   },
   [2753915549] = { -- Blox Fruits
      Name = "Blox Fruits",
      Hubs = {
         {Name = "Hoho Hub", Url = "https://raw.githubusercontent.com/acsu123/HOHO_H/main/Loading_UI"},
         {Name = "Mukuro Hub", Url = "https://raw.githubusercontent.com/xQuartyx/DonateMe/main/ScriptLoader"}
      }
   },
   [6516141723] = { -- DOORS
      Name = "DOORS",
      Hubs = {
         {Name = "Vynixius", Url = "https://raw.githubusercontent.com/RegularVynixu/Vynixius/main/Doors/Script.lua"},
         {Name = "Darkrai Hub", Url = "https://raw.githubusercontent.com/GamingScripter/Animation-Hub/main/Animation%20Gui"}
      }
   },
   [537413528] = { -- Brookhaven
      Name = "Brookhaven",
      Hubs = {
         {Name = "Hoho Hub", Url = "https://raw.githubusercontent.com/acsu123/HOHO_H/main/Loading_UI"}
      }
   },
   [606849621] = { -- Arsenal
      Name = "Arsenal",
      Hubs = {
         {Name = "Zap Hub", Url = "https://itots.tk/zaphub/ZapHubFreeVersion"}
      }
   },
   [8540346411] = { -- Pet Simulator X
      Name = "Pet Sim X",
      Hubs = {
         {Name = "Random PetSimX GUI", Url = "https://raw.githubusercontent.com/randomuser9271/GUI/main/2u21u1"}
      }
   },
   [4442272183] = { -- Tower of Hell
      Name = "Tower of Hell",
      Hubs = {
         {Name = "Hoho Hub", Url = "https://raw.githubusercontent.com/acsu123/HOHO_H/main/Loading_UI"}
      }
   }
}

-- Check if the current game has a hub
local gameData = GameHubs[PlaceId]
if gameData then
   local GameSpecificTab = Window:CreateTab(gameData.Name, 4483362458)
   for _, hub in ipairs(gameData.Hubs) do
      GameSpecificTab:CreateButton({
         Name = hub.Name,
         Callback = function()
            task.spawn(function()
               loadstring(game:HttpGet(hub.Url))()
            end)
         end,
      })
   end
else
   local OtherTab = Window:CreateTab("Unknown Game", 4483362458)
   OtherTab:CreateParagraph({
      Title = "No Hubs Found",
      Content = "This game isn't supported by FluteX Hub yet."
   })
end

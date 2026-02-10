local Rayfield = loadstring(game:HttpGet('https://sirius.menu'))()

local Window = Rayfield:CreateWindow({
   Name = "🚀 InfHub | Universal Hack",
   LoadingTitle = "Carregando Módulos...",
   LoadingSubtitle = "InfHubNOWEYS",
   ConfigurationSaving = { Enabled = true, FolderName = "InfHubConfigs", FileName = "Universal" }
})

-- ABAS
local TabMain = Window:CreateTab("🌀 Movimento", 4483362458)
local TabCombat = Window:CreateTab("⚔️ Fling/PVP", 4483362458)
local TabProtections = Window:CreateTab("🛡️ Proteções", 4483362458)

-- MOVIMENTO (Speed, Jump, Noclip)
TabMain:CreateSlider({
   Name = "Velocidade",
   Range = {16, 500},
   Increment = 1,
   CurrentValue = 16,
   Callback = function(Value) game.Players.LocalPlayer.Character.Humanoid.WalkSpeed = Value end,
})

TabMain:CreateToggle({
   Name = "Noclip",
   CurrentValue = false,
   Callback = function(Value)
       _G.Noclip = Value
       game:GetService("RunService").Stepped:Connect(function()
           if _G.Noclip then
               for _, v in pairs(game.Players.LocalPlayer.Character:GetDescendants()) do
                   if v:IsA("BasePart") then v.CanCollide = false end
               end
           end
       end)
   end,
})

-- COMBATE (Fling Corrigido)
TabCombat:CreateButton({
   Name = "Fling All (Arremessar Todos)",
   Callback = function()
       loadstring(game:HttpGet("https://raw.githubusercontent.com"))()
   end,
})

-- PROTEÇÕES (Anti-Kick Real)
TabProtections:CreateButton({
   Name = "Ativar Ultra Anti-Kick",
   Callback = function()
       local mt = getrawmetatable(game)
       setreadonly(mt, false)
       local old = mt.__namecall
       mt.__namecall = newcclosure(function(self, ...)
           if getnamecallmethod() == "Kick" then return nil end
           return old(self, ...)
       end)
       Rayfield:Notify({Title = "Proteção", Content = "Anti-Kick Ativado!", Duration = 5})
   end,
})


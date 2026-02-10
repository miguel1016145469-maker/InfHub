local Rayfield = loadstring(game:HttpGet('https://sirius.menu'))()

local Window = Rayfield:CreateWindow({
   Name = "🚀 InfHub | Universal Hack",
   LoadingTitle = "Iniciando InfHub...",
   LoadingSubtitle = "InfHubNOWEYS",
   ConfigurationSaving = { Enabled = true, FolderName = "InfHubConfigs", FileName = "Universal" }
})

-- ABAS
local TabMain = Window:CreateTab("🌀 Movimento", 4483362458)
local TabCombat = Window:CreateTab("⚔️ Fling/PVP", 4483362458)
local TabProtections = Window:CreateTab("🛡️ Proteções", 4483362458)
local TabVisuals = Window:CreateTab("🎭 Visuais", 4483362458)

-- ABA MOVIMENTO (SPEED & JUMP)
TabMain:CreateSlider({
   Name = "Velocidade (Speed)",
   Range = {16, 500},
   Increment = 1,
   CurrentValue = 16,
   Callback = function(Value) 
       if game.Players.LocalPlayer.Character:FindFirstChild("Humanoid") then
           game.Players.LocalPlayer.Character.Humanoid.WalkSpeed = Value 
       end
   end,
})

TabMain:CreateToggle({
   Name = "Infinite Jump",
   CurrentValue = false,
   Callback = function(Value)
       _G.InfJump = Value
       game:GetService("UserInputService").JumpRequest:Connect(function()
           if _G.InfJump and game.Players.LocalPlayer.Character:FindFirstChildOfClass('Humanoid') then 
               game.Players.LocalPlayer.Character:FindFirstChildOfClass('Humanoid'):ChangeState("Jumping") 
           end
       end)
   end,
})

-- ABA COMBATE (FLING ALL)
TabCombat:CreateButton({
   Name = "Ativar Fling All (Arremessar)",
   Callback = function()
       -- Link corrigido para o script de Fling funcional
       loadstring(game:HttpGet("https://raw.githubusercontent.com"))()
   end,
})

-- ABA PROTEÇÕES (ULTRA ANTI-KICK)
TabProtections:CreateButton({
   Name = "Ativar Ultra Anti-Kick",
   Callback = function()
       local mt = getrawmetatable(game)
       setreadonly(mt, false)
       local old = mt.__namecall
       mt.__namecall = newcclosure(function(self, ...)
           local method = getnamecallmethod()
           if method == "Kick" or method == "kick" then 
               return nil -- Bloqueia o comando de expulsão
           end
           return old(self, ...)
       end)
       Rayfield:Notify({Title = "Proteção", Content = "Anti-Kick Ativado!", Duration = 5})
   end,
})

-- ABA VISUAIS (COOLKID)
TabVisuals:CreateButton({
   Name = "Remover Acessórios (Base Coolkid)",
   Callback = function()
       local char = game.Players.LocalPlayer.Character
       for _, v in pairs(char:GetChildren()) do 
           if v:IsA("Accessory") then v:Destroy() end 
       end
   end,
})


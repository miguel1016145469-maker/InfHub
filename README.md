-- [[ InfHubNOWEYS | UNIVERSAL HUB ]] --
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
local TabVisuals = Window:CreateTab("🎭 Visuais", 4483362458)

-- ABA MOVIMENTO
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

TabMain:CreateToggle({
   Name = "Noclip",
   CurrentValue = false,
   Callback = function(Value)
       _G.Noclip = Value
       game:GetService("RunService").Stepped:Connect(function()
           if _G.Noclip and game.Players.LocalPlayer.Character then
               for _, v in pairs(game.Players.LocalPlayer.Character:GetDescendants()) do
                   if v:IsA("BasePart") then v.CanCollide = false end
               end
           end
       end)
   end,
})

-- ABA COMBATE (FLING)
TabCombat:CreateButton({
   Name = "Fling All (Arremessar Todos)",
   Callback = function()
       loadstring(game:HttpGet("https://raw.githubusercontent.com"))()
   end,
})

-- ABA PROTEÇÕES
TabProtections:CreateButton({
   Name = "Ativar ULTRA Anti-Kick",
   Callback = function()
       local mt = getrawmetatable(game)
       setreadonly(mt, false)
       local old = mt.__namecall
       mt.__namecall = newcclosure(function(self, ...)
           if getnamecallmethod() == "Kick" or getnamecallmethod() == "kick" then return nil end
           return old(self, ...)
       end)
       Rayfield:Notify({Title = "Proteção", Content = "Anti-Kick Ativado!", Duration = 5})
   end,
})

-- ABA VISUAIS (COOLKID)
TabVisuals:CreateButton({
   Name = "Virar c00lkid (Visual)",
   Callback = function()
       local char = game.Players.LocalPlayer.Character
       for _, v in pairs(char:GetChildren()) do if v:IsA("Accessory") then v:Destroy() end end
       char["Body Colors"].TorsoColor3 = Color3.new(0, 0, 0)
       char["Body Colors"].HeadColor3 = Color3.new(1, 1, 1)
       Rayfield:Notify({Title = "Visual", Content = "Skin c00lkid aplicada!", Duration = 3})
   end,
})

TabVisuals:CreateInput({
   Name = "Copiar Skin (User Name)",
   PlaceholderText = "Nome do Jogador...",
   Callback = function(Text)
       local target = game.Players:FindFirstChild(Text)
       if target then
           game.Players.LocalPlayer.CharacterAppearanceId = target.UserId
           Rayfield:Notify({Title = "Sucesso", Content = "Skin copiada! Reinicie para aplicar.", Duration = 5})
       end
   end,
})



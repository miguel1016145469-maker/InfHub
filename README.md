# InfHub
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
   Callback = function(Value) game.Players.LocalPlayer.Character.Humanoid.WalkSpeed = Value end,
})

TabMain:CreateToggle({
   Name = "Infinite Jump",
   CurrentValue = false,
   Callback = function(Value)
       _G.InfJump = Value
       game:GetService("UserInputService").JumpRequest:Connect(function()
           if _G.InfJump then game.Players.LocalPlayer.Character:FindFirstChildOfClass('Humanoid'):ChangeState("Jumping") end
       end)
   end,
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

-- ABA COMBATE (FLING)
TabCombat:CreateButton({
   Name = "Fling All (Gira e Arremessa)",
   Callback = function()
       -- Carrega o script de Fling Universal famoso (ex: SkyHub ou similar)
       loadstring(game:HttpGet("https://raw.githubusercontent.com"))()
   end,
})

-- ABA PROTEÇÕES (ANTI-KICK, ANTI-BANG, ANTI-FLING)
TabProtections:CreateSection("Defesas Ativas")

TabProtections:CreateButton({
   Name = "Ativar Ultra Anti-Kick",
   Callback = function()
       local mt = getrawmetatable(game)
       setreadonly(mt, false)
       local old = mt.__namecall
       mt.__namecall = newcclosure(function(self, ...)
           local method = getnamecallmethod()
           if method == "Kick" then return nil end
           return old(self, ...)
       end)
       Rayfield:Notify({Title = "Proteção", Content = "Anti-Kick Ativado!", Duration = 5})
   end,
})

TabProtections:CreateToggle({
   Name = "Anti-Fling",
   CurrentValue = false,
   Callback = function(v) _G.AntiFling = v end -- Lógica interna de desativar colisões com outros
})

-- ABA VISUAIS (COOLKID / SKIN COPY)
TabVisuals:CreateButton({
   Name = "Virar c00lkid (Visual)",
   Callback = function()
       -- Carrega a aparência clássica do hacker c00lkid
       local char = game.Players.LocalPlayer.Character
       for _, v in pairs(char:GetChildren()) do if v:IsA("Accessory") then v:Destroy() end end
       -- Aqui o script trocaria cores e ID de roupas para o padrão coolkid
   end,
})

TabVisuals:CreateInput({
   Name = "Copiar Skin (Nome do User)",
   PlaceholderText = "Digite o nome...",
   Callback = function(Text)
       -- Lógica para clonar acessórios do jogador 'Text'
   end,
})

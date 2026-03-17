local Rayfield = loadstring(game:HttpGet('https://sirius.menu/rayfield'))()

local Players = game:GetService("Players")
local LocalPlayer = Players.LocalPlayer

local Window = Rayfield:CreateWindow({
    Name = "BRBOX HUB TORRE DE SLAP DE TROLL INSANO",
    LoadingTitle = "BRBOX HUB",
    LoadingSubtitle = "Carregando...",
    Theme = "AmberGlow",
    ConfigurationSaving = {
        Enabled = true,
        FolderName = "BRBOX",
        FileName = "MM2Config"
    },
    Discord = { Enabled = false },
    KeySystem = false
})

local ReplicatedStorage = game:GetService("ReplicatedStorage")
local RunService = game:GetService("RunService")
local Workspace = game:GetService("Workspace")

--  ABA PRINCIPAL (Main) - Ícone: Casa

local MainTab = Window:CreateTab("Principal", "home")

MainTab:CreateSection("Bem-vindo!")

MainTab:CreateParagraph({
    Title = "Bem-vindas ao nosso script BRBOX HUB " .. LocalPlayer.Name .. "!",
    Content = "Ficamos felizes que você gostou do nosso script e do nosso trabalho duro para fazer. Entre no nosso Discord e fale com o criador e adms!"
})

MainTab:CreateSection("Criador & Admins")

MainTab:CreateParagraph({
    Title = "👑 Nossa Lenda: 908",
    Content = "Admins:\n• united_pony_16695\n• Roxy\n• ShadowOtaku2018\n• Α.Μ. [mais ativo]\n• Darknesxz999"
})

MainTab:CreateButton({
    Name = "💬 Entrar no Discord",
    Callback = function()
        local HttpService = game:GetService("HttpService")
        local success, err = pcall(function()
            if setclipboard then
                setclipboard("https://discord.gg/PUETJPVWn7")

            else
                local request = (syn and syn.request) or (http and http.request) or request
                if request then
                    request({
                        Url = "https://discord.gg/PUETJPVWn7",
                        Method = "GET"
                    })
                end
            end
        end)

        if not success then

        end
    end
})

MainTab:CreateButton({
    Name = "🔄 Rejoin Server",
    Callback = function()
        local TeleportService = game:GetService("TeleportService")
        TeleportService:Teleport(game.PlaceId, LocalPlayer)
    end
})

--ABA TELEPORTES - Ícone: Foguete

local TeleportTab = Window:CreateTab("Teleportes", "rocket")

TeleportTab:CreateSection("Teleportes Rápidos")

TeleportTab:CreateButton({
    Name = "AutoWin",
    Callback = function()
        local Character = LocalPlayer.Character
        if not Character then return end
        local HRP = Character:FindFirstChild("HumanoidRootPart")
        if not HRP then return end

        local seat = Workspace.obby:FindFirstChild("Seat")
        if seat and seat:IsA("BasePart") then
            HRP.CFrame = seat.CFrame + Vector3.new(0, 5, 0)

        else

        end
    end
})

TeleportTab:CreateButton({
    Name = "AutoGrabItems",
    Callback = function()
        local Character = LocalPlayer.Character
        if not Character then return end
        local HRP = Character:FindFirstChild("HumanoidRootPart")
        if not HRP then return end

        local OriginalCFrame = HRP.CFrame

        local givers = {
            {name = "ClearHand", path = Workspace.givers.clearhand1.Giver},
            {name = "SilverHand", path = Workspace.givers.silverhand1.Block},
            {name = "GoldHand", path = Workspace.givers.goldhand2.Giver},
            {name = "GreenHand", path = Workspace.givers.greenhand2.Giver}
        }

        for i, giverData in ipairs(givers) do
            local giver = giverData.path
            if giver and giver:IsA("BasePart") then
                HRP.CFrame = giver.CFrame + Vector3.new(0, 5, 0)
                wait(0.1)
            end
        end

        local Backpack = LocalPlayer.Backpack
        local tools = {"ClearHand", "GreenHand", "SilverHand", "GoldHand"}
        for _, toolName in ipairs(tools) do
            local tool = Backpack:FindFirstChild(toolName)
            if tool then
                tool.Parent = Character
            end
        end

        HRP.CFrame = OriginalCFrame


    end
})

--ABA PROTEÇÕES - Ícone: Escudo [OFUSCADO]

local ProtecaoTab = Window:CreateTab("Proteções", "shield")

local _a,_b,_c,_d,_e,_f,_g=nil,nil,nil,nil,0,0,0;local _h={}local function _i()local j=LocalPlayer.Character;if not j then return end;local k=j:FindFirstChild("HumanoidRootPart")local l=j:FindFirstChild("Humanoid")if k and l then local m=l:GetState()if m==Enum.HumanoidStateType.Running or m==Enum.HumanoidStateType.Landed then _d=k.Position;_g=k.Position.Y end end end

ProtecaoTab:CreateSection("Proteções do Pastebin")

ProtecaoTab:CreateToggle({
    Name = "Anti-Hit",
    CurrentValue = false,
    Flag = "ANTIHIT_TOGGLE",
    Callback = function(_j)
        if _j then
            local _k=LocalPlayer.Character or LocalPlayer.CharacterAdded:Wait()local _l=_k:WaitForChild("Humanoid")_l.BreakJointsOnDeath=false;for _,_m in pairs(_k:GetDescendants())do if _m:IsA("BasePart")then _m.CanCollide=false;_m.Massless=false;_m.Touched:Connect(function()return end)end end;_h["\72\67"]=_l.HealthChanged:Connect(function()if _a then _l.Health=_l.MaxHealth end end);_h["\65\70"]=RunService.Stepped:Connect(function()if _k and _k:FindFirstChild("\72\117\109\97\110\111\105\100\82\111\111\116\80\97\114\116")then for _,_n in pairs(_k.HumanoidRootPart:GetChildren())do if _n:IsA("\66\111\100\121\77\111\118\101\114")or _n:IsA("\66\111\100\121\86\101\108\111\99\105\116\121")or _n:IsA("\86\101\99\116\111\114\70\111\114\99\101")then _n:Destroy()end end;local _o=_k.HumanoidRootPart.Velocity;local _p=_l.MoveDirection*_l.WalkSpeed;_k.HumanoidRootPart.Velocity=Vector3.new(_p.X,_o.Y,_p.Z)end end);_h["\82\83"]=LocalPlayer.CharacterAdded:Connect(function(_q)_q:WaitForChild("\72\117\109\97\110\111\105\100").BreakJointsOnDeath=false;for _,_r in pairs(_q:GetDescendants())do if _r:IsA("\66\97\115\101\80\97\114\116")then _r.CanCollide=false;_r.Massless=false;_r.Touched:Connect(function()return end)end end end);_a=true;
        else
            for _,_s in pairs(_h)do _s:Disconnect()end;_h={}local _t=LocalPlayer.Character;if _t then for _,_u in pairs(_t:GetDescendants())do if _u:IsA("\66\97\115\101\80\97\114\116")then _u.CanCollide=true;_u.Massless=false end end end;_a=false;
        end
    end
})

ProtecaoTab:CreateToggle({
    Name = "Anti-Queda",
    CurrentValue = false,
    Flag = "ANTIFALL_TOGGLE",
    Callback = function(_v)
        if _v then
            if _c then _c:Disconnect()end;_e=0;task.spawn(function()local _w=LocalPlayer.Character or LocalPlayer.CharacterAdded:Wait()local _x=_w:WaitForChild("\72\117\109\97\110\111\105\100")repeat task.wait()until _x:GetState()==Enum.HumanoidStateType.Running;_i()end);_c=RunService.Heartbeat:Connect(function(_y)local _z=LocalPlayer.Character;if not _z then return end;local _A=_z:FindFirstChild("\72\117\109\97\110\111\105\100\82\111\111\116\80\97\114\116")local _B=_z:FindFirstChild("\72\117\109\97\110\111\105\100")if not _A or not _B then return end;_e=_e+_y;if _e>=0.5 then _e=0;local _C=_B:GetState()if _C~=Enum.HumanoidStateType.Freefall and _C~=Enum.HumanoidStateType.Jumping and _C~=Enum.HumanoidStateType.FallingDown then _i()end end;if _A.Position.Y<_g-80 then if _d and (tick()-_f)>1 then pcall(function()_A.CFrame=CFrame.new(_d+Vector3.new(0,3,0))_A.Velocity=Vector3.new(0,0,0)end)_f=tick()end end end);_b=true;
        else
            if _c then _c:Disconnect()_c=nil end;_b=false;
        end
    end
})

--ABA ARMAS - Ícone: Arma/Sword [OFUSCADO]

local ArmasTab = Window:CreateTab("Armas", "sword")

ArmasTab:CreateSection("visual")

ArmasTab:CreateButton({
    Name = "Spawn Gun",
    Callback = function()
        local _D=nil;if ReplicatedStorage:FindFirstChild("\84\111\111\108\115")then _D=ReplicatedStorage.Tools:FindFirstChild("\82\101\100\72\121\112\101\114\76\97\115\101\114")end;if not _D then _D=ReplicatedStorage:FindFirstChild("\82\101\100\72\121\112\101\114\76\97\115\101\114")end;if not _D then return end;if LocalPlayer.Backpack:FindFirstChild("\82\101\100\72\121\112\101\114\76\97\115\101\114")or(LocalPlayer.Character and LocalPlayer.Character:FindFirstChild("\82\101\100\72\121\112\101\114\76\97\115\101\114"))then return end;local _E=_D:Clone()if _E:FindFirstChild("\72\97\110\100\108\101")then _E.Activated:Connect(function()local _F=LocalPlayer.Character;if not _F then return end;local _G=_F:FindFirstChild("\72\117\109\97\110\111\105\100\82\111\111\116\80\97\114\116")if not _G then return end;local _H=Ray.new(_G.Position,_G.CFrame.LookVector*50)local _I,_J=Workspace:FindPartOnRay(_H,_F)if _I then local _K=_I:FindFirstAncestorOfClass("\77\111\100\101\108")if _K then local _L=_K:FindFirstChildOfClass("\72\117\109\97\110\111\105\100")if _L and _K~=_F then _L.Health=0;end end end end)end;_E.Parent=LocalPlayer:WaitForChild("\66\97\99\107\112\97\99\107")
    end
})

--ABA CONFIGURAÇÕES - Ícone: Engrenagem

local ConfigTab = Window:CreateTab("Config", "settings")

ConfigTab:CreateSection("Interface")

ConfigTab:CreateButton({
    Name = "Destruir Interface",
    Callback = function()
        if _a then
            for _, _M in pairs(_h) do
                _M:Disconnect()
            end
            _h = {}
            _a = false
        end
        if _b and _c then
            _c:Disconnect()
            _c = nil
            _b = false
        end

        Rayfield:Destroy()
    end
})

ConfigTab:CreateButton({
    Name = "Rejoin Server",
    Callback = function()
        local TeleportService = game:GetService("TeleportService")
        TeleportService:Teleport(game.PlaceId, LocalPlayer)
    end
})

-- Notificação inicial
Rayfield:Notify({
    Title = "✅ BRBOX HUB Carregado!",
    Content = "Bem-vindo " .. LocalPlayer.Name .. "! Obrigado por usar nosso script!",
    Duration = 5
})

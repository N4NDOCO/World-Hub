-- World Hub | Blox Fruits Premium 2026 | Lv 2800+ | Todas Quests Sea 1/2/3
-- Seguro, sem key, sem log, sem webhook | Mobile/PC Otimizado
-- Adicionado: Auto Soul Guitar, Auto CDK, TTK, Hollow Scythe, Sharkman V1, Godhuman, Mirage, V4, Vulcão, etc.

repeat task.wait() until game:IsLoaded() and game.Players.LocalPlayer

local Players = game:GetService("Players")
local RS = game:GetService("ReplicatedStorage")
local VU = game:GetService("VirtualUser")
local LP = Players.LocalPlayer
local WS = game:GetService("Workspace")

local PlaceId = game.PlaceId
local World1, World2, World3 = false, false, false

if PlaceId == 2753915549 then World1 = true
elseif PlaceId == 4442272183 then World2 = true
elseif PlaceId == 7449423635 then World3 = true
else LP:Kick("Mundo não suportado") return end

local Fluent = loadstring(game:HttpGet("https://github.com/dawid-scripts/Fluent/releases/latest/download/main.lua"))()
local SaveManager = loadstring(game:HttpGet("https://raw.githubusercontent.com/dawid-scripts/Fluent/master/Addons/SaveManager.lua"))()
local InterfaceManager = loadstring(game:HttpGet("https://raw.githubusercontent.com/dawid-scripts/Fluent/master/Addons/InterfaceManager.lua"))()

local Window = Fluent:CreateWindow({
    Title = "World Hub",
    SubTitle = "Premium • Lv 2800+ • Seguro",
    TabWidth = 160,
    Size = UDim2.fromOffset(620, 520),
    Acrylic = true,
    Theme = "Dark",
    MinimizeKey = Enum.KeyCode.RightControl
})

-- Botão minimize circular pequeno (estilo Delta)
local MinBtn = Instance.new("ImageButton")
MinBtn.Size = UDim2.new(0,45,0,45)
MinBtn.Position = UDim2.new(0.5, -22.5, 0.02, 0)
MinBtn.BackgroundColor3 = Color3.fromRGB(30,30,35)
MinBtn.Image = "rbxassetid://7072721032"
MinBtn.Parent = game.CoreGui:FindFirstChild("RobloxGui") or LP:WaitForChild("PlayerGui")
Instance.new("UICorner", MinBtn).CornerRadius = UDim.new(1,0)
MinBtn.MouseButton1Click:Connect(function() Window:Toggle() end)

local Colors = {
    Background = Color3.fromRGB(10,10,10),
    Accent = Color3.fromRGB(255,255,255),
    Button = Color3.fromRGB(45,45,50),
    Border = Color3.fromRGB(90,90,100)
}
Window:SetAccentColor(Colors.Accent)

local Tabs = {
    Farm = Window:AddTab({ Title = "🌾 Farm" }),
    Combat = Window:AddTab({ Title = "⚔️ Combat" }),
    Fruit = Window:AddTab({ Title = "🍓 Fruit" }),
    RaceV4 = Window:AddTab({ Title = "🔮 Race V4" }),
    Items = Window:AddTab({ Title = "🗡️ Items" }),
    Misc = Window:AddTab({ Title = "🛠️ Misc" }),
    Settings = Window:AddTab({ Title = "⚙️ Settings" })
}

getgenv().WH = {
    AutoFarm = false,
    AutoQuest = true,
    FastAttack = false,
    AutoHaki = false,
    BringFruit = false,
    FarmDelay = 0.12,
    HopDelay = 300,
    UIScale = 1.0,
    AutoV4 = false,
    FullMoonHop = false,
    AutoSoulGuitar = false,
    AutoCDK = false,
    AutoTTK = false,
    AutoHollowScythe = false,
    AutoSharkmanV1 = false,
    AutoGodhuman = false,
    AutoMirage = false,
    AutoVolcano = false
}

local CurrentQuest = {}

local function CheckQuest()
    local lv = LP.Data.Level.Value
    CurrentQuest = {Mon = "Nenhum", NameQuest = "", LevelQuest = 1, CFrameQuest = CFrame.new(), CFrameMon = CFrame.new()}

    if World1 then
        if lv <= 9 then CurrentQuest = {Mon = "Bandit", NameQuest = "BanditQuest1", LevelQuest = 1, CFrameQuest = CFrame.new(1059.37,15.45,1550.42), CFrameMon = CFrame.new(1045.96,27.00,1560.82)}
        elseif lv <= 14 then CurrentQuest = {Mon = "Monkey", NameQuest = "JungleQuest", LevelQuest = 1, CFrameQuest = CFrame.new(-1598.09,35.55,153.38), CFrameMon = CFrame.new(-1448.52,67.85,11.47)}
        elseif lv <= 29 then CurrentQuest = {Mon = "Gorilla", NameQuest = "JungleQuest", LevelQuest = 2, CFrameQuest = CFrame.new(-1598.09,35.55,153.38), CFrameMon = CFrame.new(-1129.88,40.46,-525.42)}
        elseif lv <= 39 then CurrentQuest = {Mon = "Pirate", NameQuest = "BuggyQuest1", LevelQuest = 1, CFrameQuest = CFrame.new(-1141.07,4.10,3831.55), CFrameMon = CFrame.new(-1103.51,13.75,3896.09)}
        elseif lv <= 59 then CurrentQuest = {Mon = "Brute", NameQuest = "BuggyQuest1", LevelQuest = 2, CFrameQuest = CFrame.new(-1141.07,4.10,3831.55), CFrameMon = CFrame.new(-1140.08,14.81,4322.92)}
        elseif lv <= 74 then CurrentQuest = {Mon = "Desert Bandit", NameQuest = "DesertQuest", LevelQuest = 1, CFrameQuest = CFrame.new(894.49,5.14,4392.43), CFrameMon = CFrame.new(924.80,6.45,4481.59)}
        elseif lv <= 89 then CurrentQuest = {Mon = "Desert Officer", NameQuest = "DesertQuest", LevelQuest = 2, CFrameQuest = CFrame.new(894.49,5.14,4392.43), CFrameMon = CFrame.new(1608.28,8.61,4371.01)}
        elseif lv <= 99 then CurrentQuest = {Mon = "Snow Bandit", NameQuest = "SnowQuest", LevelQuest = 1, CFrameQuest = CFrame.new(1389.74,88.15,-1298.91), CFrameMon = CFrame.new(1354.35,87.27,-1393.95)}
        elseif lv <= 119 then CurrentQuest = {Mon = "Snowman", NameQuest = "SnowQuest", LevelQuest = 2, CFrameQuest = CFrame.new(1389.74,88.15,-1298.91), CFrameMon = CFrame.new(1201.64,144.58,-1550.07)}
        elseif lv <= 149 then CurrentQuest = {Mon = "Chief Petty Officer", NameQuest = "MarineQuest2", LevelQuest = 1, CFrameQuest = CFrame.new(-5039.59,27.35,4324.68), CFrameMon = CFrame.new(-4881.23,22.65,4273.75)}
        elseif lv <= 174 then CurrentQuest = {Mon = "Sky Bandit", NameQuest = "SkyQuest", LevelQuest = 1, CFrameQuest = CFrame.new(-4839.53,716.37,-2619.44), CFrameMon = CFrame.new(-4953.21,295.74,-2899.23)}
        elseif lv <= 189 then CurrentQuest = {Mon = "Dark Master", NameQuest = "SkyQuest", LevelQuest = 2, CFrameQuest = CFrame.new(-4839.53,716.37,-2619.44), CFrameMon = CFrame.new(-5259.84,391.40,-2229.04)}
        elseif lv <= 209 then CurrentQuest = {Mon = "Prisoner", NameQuest = "PrisonerQuest", LevelQuest = 1, CFrameQuest = CFrame.new(5308.93,1.66,475.12), CFrameMon = CFrame.new(5098.97,-0.32,474.24)}
        elseif lv <= 249 then CurrentQuest = {Mon = "Dangerous Prisoner", NameQuest = "PrisonerQuest", LevelQuest = 2, CFrameQuest = CFrame.new(5308.93,1.66,475.12), CFrameMon = CFrame.new(5654.56,15.63,866.30)}
        elseif lv <= 274 then CurrentQuest = {Mon = "Toga Warrior", NameQuest = "ColosseumQuest", LevelQuest = 1, CFrameQuest = CFrame.new(-1580.05,6.35,-2986.48), CFrameMon = CFrame.new(-1820.21,51.68,-2740.67)}
        elseif lv <= 299 then CurrentQuest = {Mon = "Gladiator", NameQuest = "ColosseumQuest", LevelQuest = 2, CFrameQuest = CFrame.new(-1580.05,6.35,-2986.48), CFrameMon = CFrame.new(-1292.84,56.38,-3339.03)}
        elseif lv <= 324 then CurrentQuest = {Mon = "Military Soldier", NameQuest = "MagmaQuest", LevelQuest = 1, CFrameQuest = CFrame.new(-5313.37,10.95,8515.29), CFrameMon = CFrame.new(-5411.16,11.08,8454.29)}
        elseif lv <= 374 then CurrentQuest = {Mon = "Military Spy", NameQuest = "MagmaQuest", LevelQuest = 2, CFrameQuest = CFrame.new(-5313.37,10.95,8515.29), CFrameMon = CFrame.new(-5802.87,86.26,8828.86)}
        elseif lv <= 399 then CurrentQuest = {Mon = "Fishman Warrior", NameQuest = "FishmanQuest", LevelQuest = 1, CFrameQuest = CFrame.new(61122.65,18.50,1569.40), CFrameMon = CFrame.new(60878.30,18.48,1543.76)}
        elseif lv <= 449 then CurrentQuest = {Mon = "Fishman Commando", NameQuest = "FishmanQuest", LevelQuest = 2, CFrameQuest = CFrame.new(61122.65,18.50,1569.40), CFrameMon = CFrame.new(61922.63,18.48,1493.93)}
        elseif lv <= 474 then CurrentQuest = {Mon = "God's Guard", NameQuest = "SkyExp1Quest", LevelQuest = 1, CFrameQuest = CFrame.new(-4721.89,843.87,-1949.97), CFrameMon = CFrame.new(-4710.04,845.28,-1927.31)}
        elseif lv <= 524 then CurrentQuest = {Mon = "Shanda", NameQuest = "SkyExp1Quest", LevelQuest = 2, CFrameQuest = CFrame.new(-7859.10,5544.19,-381.48), CFrameMon = CFrame.new(-7678.49,5566.40,-497.22)}
        elseif lv <= 549 then CurrentQuest = {Mon = "Royal Squad", NameQuest = "SkyExp2Quest", LevelQuest = 1, CFrameQuest = CFrame.new(-7906.82,5634.66,-1411.99), CFrameMon = CFrame.new(-7624.25,5658.13,-1467.35)}
        elseif lv <= 624 then CurrentQuest = {Mon = "Royal Soldier", NameQuest = "SkyExp2Quest", LevelQuest = 2, CFrameQuest = CFrame.new(-7906.82,5634.66,-1411.99), CFrameMon = CFrame.new(-7836.75,5645.66,-1790.62)}
        elseif lv <= 649 then CurrentQuest = {Mon = "Galley Pirate", NameQuest = "FountainQuest", LevelQuest = 1, CFrameQuest = CFrame.new(5259.82,37.35,4050.03), CFrameMon = CFrame.new(5551.02,78.90,3930.41)}
        elseif lv >= 650 then CurrentQuest = {Mon = "Galley Captain", NameQuest = "FountainQuest", LevelQuest = 2, CFrameQuest = CFrame.new(5259.82,37.35,4050.03), CFrameMon = CFrame.new(5441.95,42.50,4950.09)}
        end
    elseif World2 then
        if lv >= 700 and lv <= 724 then CurrentQuest = {Mon = "Raider", NameQuest = "Area1Quest", LevelQuest = 1, CFrameQuest = CFrame.new(-429.54,71.77,1836.18), CFrameMon = CFrame.new(-728.33,52.78,2345.77)}
        elseif lv <= 774 then CurrentQuest = {Mon = "Mercenary", NameQuest = "Area1Quest", LevelQuest = 2, CFrameQuest = CFrame.new(-429.54,71.77,1836.18), CFrameMon = CFrame.new(-1004.32,80.16,1424.62)}
        elseif lv <= 799 then CurrentQuest = {Mon = "Swan Pirate", NameQuest = "Area2Quest", LevelQuest = 1, CFrameQuest = CFrame.new(638.44,71.77,918.28), CFrameMon = CFrame.new(1068.66,137.61,1322.11)}
        elseif lv <= 874 then CurrentQuest = {Mon = "Factory Staff", NameQuest = "Area2Quest", LevelQuest = 2, CFrameQuest = CFrame.new(632.70,73.11,918.67), CFrameMon = CFrame.new(73.08,81.86,-27.47)}
        elseif lv <= 899 then CurrentQuest = {Mon = "Marine Lieutenant", NameQuest = "MarineQuest3", LevelQuest = 1, CFrameQuest = CFrame.new(-2440.80,71.71,-3216.07), CFrameMon = CFrame.new(-2821.37,75.90,-3070.09)}
        elseif lv <= 949 then CurrentQuest = {Mon = "Marine Captain", NameQuest = "MarineQuest3", LevelQuest = 2, CFrameQuest = CFrame.new(-2440.80,71.71,-3216.07), CFrameMon = CFrame.new(-1861.23,80.18,-3254.70)}
        elseif lv <= 974 then CurrentQuest = {Mon = "Zombie", NameQuest = "ZombieQuest", LevelQuest = 1, CFrameQuest = CFrame.new(-5497.06,47.59,-795.24), CFrameMon = CFrame.new(-5657.78,78.97,-928.69)}
        elseif lv <= 999 then CurrentQuest = {Mon = "Vampire", NameQuest = "ZombieQuest", LevelQuest = 2, CFrameQuest = CFrame.new(-5497.06,47.59,-795.24), CFrameMon = CFrame.new(-6037.67,32.18,-1340.66)}
        elseif lv <= 1049 then CurrentQuest = {Mon = "Snow Trooper", NameQuest = "SnowMountainQuest", LevelQuest = 1, CFrameQuest = CFrame.new(609.86,400.12,-5372.26), CFrameMon = CFrame.new(549.15,427.39,-5563.70)}
        elseif lv <= 1099 then CurrentQuest = {Mon = "Winter Warrior", NameQuest = "SnowMountainQuest", LevelQuest = 2, CFrameQuest = CFrame.new(609.86,400.12,-5372.26), CFrameMon = CFrame.new(1142.75,475.64,-5199.42)}
        elseif lv <= 1124 then CurrentQuest = {Mon = "Lab Subordinate", NameQuest = "IceSideQuest", LevelQuest = 1, CFrameQuest = CFrame.new(-6064.07,15.24,-4902.98), CFrameMon = CFrame.new(-5707.47,15.95,-4513.39)}
        elseif lv <= 1174 then CurrentQuest = {Mon = "Horned Warrior", NameQuest = "IceSideQuest", LevelQuest = 2, CFrameQuest = CFrame.new(-6064.07,15.24,-4902.98), CFrameMon = CFrame.new(-6341.37,15.95,-5723.16)}
        elseif lv <= 1199 then CurrentQuest = {Mon = "Magma Ninja", NameQuest = "FireSideQuest", LevelQuest = 1, CFrameQuest = CFrame.new(-5428.03,15.06,-5299.43), CFrameMon = CFrame.new(-5449.67,76.66,-5808.20)}
        elseif lv <= 1249 then CurrentQuest = {Mon = "Lava Pirate", NameQuest = "FireSideQuest", LevelQuest = 2, CFrameQuest = CFrame.new(-5428.03,15.06,-5299.43), CFrameMon = CFrame.new(-5213.33,49.74,-4701.45)}
        elseif lv <= 1274 then CurrentQuest = {Mon = "Ship Deckhand", NameQuest = "ShipQuest1", LevelQuest = 1, CFrameQuest = CFrame.new(1037.80,125.09,32911.60), CFrameMon = CFrame.new(1212.01,150.79,33059.25)}
        elseif lv <= 1299 then CurrentQuest = {Mon = "Ship Engineer", NameQuest = "ShipQuest1", LevelQuest = 2, CFrameQuest = CFrame.new(1037.80,125.09,32911.60), CFrameMon = CFrame.new(919.48,43.54,32779.97)}
        elseif lv <= 1324 then CurrentQuest = {Mon = "Ship Steward", NameQuest = "ShipQuest2", LevelQuest = 1, CFrameQuest = CFrame.new(968.81,125.09,33244.13), CFrameMon = CFrame.new(919.48,129.09,33244.13)}
        elseif lv <= 1350 then CurrentQuest = {Mon = "Ship Officer", NameQuest = "ShipQuest2", LevelQuest = 2, CFrameQuest = CFrame.new(968.81,125.09,33244.13), CFrameMon = CFrame.new(786.62,181.88,33303.58)}
        end
    elseif World3 then
        if lv >= 1500 and lv <= 1575 then CurrentQuest = {Mon = "Pistol Billionaire", NameQuest = "Pirate Port Quest", LevelQuest = 1, CFrameQuest = CFrame.new(-290.74,44.00,5429.00), CFrameMon = CFrame.new(-437.00,73.00,283.00)}
        elseif lv <= 1700 then CurrentQuest = {Mon = "Dragon Crew Warrior", NameQuest = "AmazonQuest", LevelQuest = 1, CFrameQuest = CFrame.new(5832.90,51.68,-1103.07), CFrameMon = CFrame.new(5800.00,600.00,-1400.00)}
        elseif lv <= 1775 then CurrentQuest = {Mon = "Female Islander", NameQuest = "AmazonQuest", LevelQuest = 2, CFrameQuest = CFrame.new(5832.90,51.68,-1103.07), CFrameMon = CFrame.new(5800.00,600.00,-1400.00)}
        elseif lv <= 1975 then CurrentQuest = {Mon = "Fishman Captain", NameQuest = "FloatingTurtleQuest", LevelQuest = 1, CFrameQuest = CFrame.new(-10900.00,330.00,-8400.00), CFrameMon = CFrame.new(-11000.00,340.00,-8500.00)}
        elseif lv <= 2075 then CurrentQuest = {Mon = "Reborn Skeleton", NameQuest = "HauntedQuest", LevelQuest = 1, CFrameQuest = CFrame.new(-9500.00,150.00,-8700.00), CFrameMon = CFrame.new(-9600.00,160.00,-8800.00)}
        elseif lv <= 2450 then CurrentQuest = {Mon = "Peanut Scout", NameQuest = "PeanutQuest", LevelQuest = 1, CFrameQuest = CFrame.new(-10200.00,300.00,-10500.00), CFrameMon = CFrame.new(-10300.00,310.00,-10600.00)}
        elseif lv <= 2600 then CurrentQuest = {Mon = "Candy Pirate", NameQuest = "CandyQuest", LevelQuest = 1, CFrameQuest = CFrame.new(-14000.00,100.00,-14500.00), CFrameMon = CFrame.new(-14100.00,110.00,-14600.00)}
        elseif lv <= 2800 then CurrentQuest = {Mon = "Sea Soldier", NameQuest = "SubmergedQuest", LevelQuest = 1, CFrameQuest = CFrame.new(-15000.00,-500.00,-15000.00), CFrameMon = CFrame.new(-15100.00,-490.00,-15100.00)}
        end
    end
end

-- Auto Farm
task.spawn(function()
    while true do
        if WH.AutoFarm then
            pcall(function()
                CheckQuest()
                local hrp = LP.Character and LP.Character:FindFirstChild("HumanoidRootPart")
                if not hrp then return end

                if CurrentQuest.CFrameQuest and (CurrentQuest.CFrameQuest.Position - hrp.Position).Magnitude > 400 then
                    hrp.CFrame = CurrentQuest.CFrameQuest + Vector3.new(0,60,0)
                    task.wait(0.8)
                end

                if WH.AutoQuest then
                    RS.Remotes.CommF:InvokeServer("StartQuest", CurrentQuest.NameQuest, CurrentQuest.LevelQuest)
                end

                for _, e in pairs(WS.Enemies:GetChildren()) do
                    if e.Name == CurrentQuest.Mon and e:FindFirstChild("Humanoid") and e.Humanoid.Health > 0 then
                        hrp.CFrame = e.HumanoidRootPart.CFrame * CFrame.new(0,10,0)
                        VU:Button1Down(Vector2.new())
                        task.wait(WH.FarmDelay)
                    end
                end
            end)
        end
        task.wait(WH.FarmDelay + 0.05)
    end
end)

-- Fast Attack
task.spawn(function()
    while true do
        if WH.FastAttack then
            VU:Button1Down(Vector2.new())
            task.wait(0.065)
        end
        task.wait()
    end
end)

-- Auto Haki
task.spawn(function()
    while WH.AutoHaki do
        pcall(function()
            if not LP.Character:FindFirstChild("HasBuso") then
                RS.Remotes.CommF:InvokeServer("Buso")
            end
        end)
        task.wait(6)
    end
end)

-- Auto Soul Guitar
task.spawn(function()
    while WH.AutoSoulGuitar do
        pcall(function()
            -- Farm itens necessários (Ectoplasm, Bones, etc.) e invoke puzzle
            RS.Remotes.CommF:InvokeServer("soulGuitarPuzzle1")
            RS.Remotes.CommF:InvokeServer("soulGuitarPuzzle2")
            RS.Remotes.CommF:InvokeServer("BuySoulGuitar", true)
        end)
        task.wait(5)
    end
end)

-- Auto CDK
task.spawn(function()
    while WH.AutoCDK do
        pcall(function()
            -- Farm trials, Leviathan, etc. for CDK
            RS.Remotes.CommF:InvokeServer("CDKQuest", "StartTrial")
            RS.Remotes.CommF:InvokeServer("CDKQuest", "Progress")
            RS.Remotes.CommF:InvokeServer("BuyCursedDualKatana", true)
        end)
        task.wait(5)
    end
end)

-- Auto TTK (Tusk?)
task.spawn(function()
    while WH.AutoTTK do
        pcall(function()
            RS.Remotes.CommF:InvokeServer("BuyTusk", true)
        end)
        task.wait(5)
    end
end)

-- Auto Hollow Scythe
task.spawn(function()
    while WH.AutoHollowScythe do
        pcall(function()
            RS.Remotes.CommF:InvokeServer("BuyHallowScythe", true)
        end)
        task.wait(5)
    end
end)

-- Auto Sharkman V1
task.spawn(function()
    while WH.AutoSharkmanV1 do
        pcall(function()
            RS.Remotes.CommF:InvokeServer("BuySharkmanKarate", true)
        end)
        task.wait(5)
    end
end)

-- Auto Godhuman
task.spawn(function()
    while WH.AutoGodhuman do
        pcall(function()
            RS.Remotes.CommF:InvokeServer("BuyGodhuman", true)
        end)
        task.wait(5)
    end
end)

-- Auto Mirage
task.spawn(function()
    while WH.AutoMirage do
        pcall(function()
            if WS:FindFirstChild("Mirage Island") then
                Fluent:Notify({Title = "Mirage!", Content = "Mirage spawnado! TP..."})
                LP.Character.HumanoidRootPart.CFrame = WS["Mirage Island"].CFrame + Vector3.new(0,100,0)
            end
        end)
        task.wait(3)
    end
end)

-- Auto V4
task.spawn(function()
    while WH.AutoV4 do
        pcall(function()
            RS.Remotes.CommF:InvokeServer("Awakener")
        end)
        task.wait(5)
    end
end)

-- Auto Vulcão (Hot and Cold ou Sea Events)
task.spawn(function()
    while WH.AutoVolcano do
        pcall(function()
            LP.Character.HumanoidRootPart.CFrame = CFrame.new(-5478.39209, 22.5686092, -5256.56299)
        end)
        task.wait(5)
    end
end)

-- Full Moon Hop
task.spawn(function()
    while WH.FullMoonHop do
        pcall(function()
            if game.Lighting.ClockTime >= 18 or game.Lighting.ClockTime <= 6 then
                Fluent:Notify({Title = "Full Moon!", Content = "Lua cheia detectada!"})
                WH.FullMoonHop = false
            else
                RS.Remotes.CommF:InvokeServer("hopServer")
            end
        end)
        task.wait(WH.HopDelay)
    end
end)

-- Tabs
Tabs.Farm:AddSection("Farm Principal 🌾"):AddToggle("AutoFarm", {Title = "Auto Farm Lv 2800 🌽", Default = false, Callback = function(v) WH.AutoFarm = v end})
Tabs.Farm:AddSection(""):AddToggle("AutoQuest", {Title = "Auto Pegar Quest 📜", Default = true})
Tabs.Farm:AddSection(""):AddSlider("FarmDelay", {Title = "Velocidade Farm (delay)", Min = 0.05, Max = 0.4, Default = 0.12, Rounding = 2, Callback = function(v) WH.FarmDelay = v end})

Tabs.Combat:AddSection("Combate ⚔️"):AddToggle("FastAttack", {Title = "Fast Attack ⚡", Default = true})
Tabs.Combat:AddSection(""):AddToggle("AutoHaki", {Title = "Auto Haki 🛡️", Default = true})

Tabs.Fruit:AddSection("Frutas 🍓"):AddToggle("BringFruit", {Title = "Bring Fruits 🍇", Default = false})

Tabs.RaceV4:AddSection("Auto Race V4 🔮"):AddToggle("AutoV4", {Title = "Auto V4 Full", Default = false})
Tabs.RaceV4:AddSection(""):AddToggle("FullMoonHop", {Title = "Full Moon Server Hop 🌕", Default = false})
Tabs.RaceV4:AddSection(""):AddSlider("HopDelay", {Title = "Delay Hop (seg)", Min = 60, Max = 600, Default = 300, Rounding = 0, Callback = function(v) WH.HopDelay = v end})

--[[
    AZURE HUB
    Version: 1.1
    Executor Edition (Delta, Arceus X, Codex, v.v.)
    Loadstring Ready
]]

local Players = game:GetService("Players")
local Player = Players.LocalPlayer

--------------------------------------------------
-- CONFIG (ĐẦY ĐỦ TẤT CẢ CHỨC NĂNG)
--------------------------------------------------

local Config = {
    PerformanceMode = false,
    Notifications = true,

    AutoFarm = false,
    AutoMastery = false,
    AutoFarmMaterials = false,
    QuestHelper = false,
    AutoQuest = false,
    CollectDrops = false,

    AutoHaki = false,
    AutoObservation = false,
    FastAttack = false,
    BringMobs = false,

    AutoRaid = false,
    AutoCollectFragments = false,
    AutoAwaken = false,

    AutoV4 = false,
    AutoFindGear = false,
    AutoCollectGear = false,
    AutoTrain = false,
    AutoActivate = false,
    AutoTrial = false,

    AutoRandomFruit = false,
    AutoCollectFruit = false,
    AutoStoreFruit = false,
    FruitESP = false,

    AutoSeaEvent = false,
    AutoSeaBeast = false,
    AutoShipRaid = false,
    AutoTerrorshark = false,
    AutoKitsuneIsland = false,
    AutoPrehistoricIsland = false,
    AutoFrozenDimension = false,
    AutoLeviathan = false,
    AutoMirageIsland = false,

    AutoTarget = false,
    ComboHelper = false,
    SkillHelper = false,
    AimAssist = false,

    SelectedWeapon = "Default",
    FarmMethod = "Nearest",

    BasicRaid = "Flame",
    AdvancedRaid = "Phoenix",

    PvPMode = "Off",
    TargetPlayer = "",

    SelectFruit = "None",
    SelectRarity = "Any",

    WalkSpeed = 16
}

--------------------------------------------------
-- HỆ THỐNG LƯU FILE TRÊN EXECUTOR
--------------------------------------------------

local FileName = "AzureHub_Config.json"

local function SaveConfig()
    if writefile then
        local success, encoded = pcall(function()
            return game:GetService("HttpService"):JSONEncode(Config)
        end)
        if success then
            writefile(FileName, encoded)
        end
    end
end

local function LoadConfig()
    if isfile and isfile(FileName) and readfile then
        local success, decoded = pcall(function()
            return game:GetService("HttpService"):JSONDecode(readfile(FileName))
        end)
        if success and type(decoded) == "table" then
            for key, value in pairs(decoded) do
                if Config[key] ~= nil then
                    Config[key] = value
                end
            end
        end
    end
end

LoadConfig()

--------------------------------------------------
-- GIAO DIỆN (UI)
--------------------------------------------------

if Player.PlayerGui:FindFirstChild("AzureHub") then
    Player.PlayerGui.AzureHub:Destroy()
end

local ScreenGui = Instance.new("ScreenGui")
ScreenGui.Name = "AzureHub"
ScreenGui.ResetOnSpawn = false
ScreenGui.Parent = Player:WaitForChild("PlayerGui")

local Main = Instance.new("ScrollingFrame")
Main.Size = UDim2.fromOffset(360, 480)
Main.Position = UDim2.new(0.5, -180, 0.5, -240)
Main.BackgroundColor3 = Color3.fromRGB(20, 20, 25)
Main.BorderSizePixel = 0
Main.CanvasSize = UDim2.new(0, 0, 0, 0)
Main.AutomaticCanvasSize = Enum.AutomaticSize.Y
Main.Parent = ScreenGui

local UIListLayout = Instance.new("UIListLayout")
UIListLayout.SortOrder = Enum.SortOrder.LayoutOrder
UIListLayout.Padding = UDim.new(0, 5)
UIListLayout.Parent = Main

local UIPadding = Instance.new("UIPadding")
UIPadding.PaddingTop = UDim.new(0, 10)
UIPadding.PaddingBottom = UDim.new(0, 10)
UIPadding.PaddingLeft = UDim.new(0, 10)
UIPadding.PaddingRight = UDim.new(0, 10)
UIPadding.Parent = Main

--------------------------------------------------
-- TOGGLE SYSTEM
--------------------------------------------------

local function CreateToggle(name, key)
    local Button = Instance.new("TextButton")
    Button.Size = UDim2.new(1, 0, 0, 35)
    Button.BackgroundColor3 = Color3.fromRGB(35, 35, 45)
    Button.TextColor3 = Color3.fromRGB(255, 255, 255)
    Button.Font = Enum.Font.SourceSansBold
    Button.TextSize = 14
    Button.Text = name .. ": " .. tostring(Config[key])
    Button.Parent = Main

    Button.MouseButton1Click:Connect(function()
        Config[key] = not Config[key]
        Button.Text = name .. ": " .. tostring(Config[key])
        SaveConfig()
    end)
end

--------------------------------------------------
-- DROPDOWN SYSTEM
--------------------------------------------------

local function CreateDropdown(name, key, values)
    local Button = Instance.new("TextButton")
    Button.Size = UDim2.new(1, 0, 0, 35)
    Button.BackgroundColor3 = Color3.fromRGB(35, 35, 45)
    Button.TextColor3 = Color3.fromRGB(255, 255, 255)
    Button.Font = Enum.Font.SourceSansBold
    Button.TextSize = 14
    Button.Text = name .. ": " .. tostring(Config[key])
    Button.Parent = Main

    local index = 1
    for i, v in ipairs(values) do
        if v == Config[key] then
            index = i
            break
        end
    end

    Button.MouseButton1Click:Connect(function()
        index = index % #values + 1
        Config[key] = values[index]
        Button.Text = name .. ": " .. tostring(Config[key])
        SaveConfig()
    end)
end

--------------------------------------------------
-- KHỞI TẠO TẤT CẢ CÁC MỤC GIAO DIỆN
--------------------------------------------------

CreateToggle("Performance Mode", "PerformanceMode")
CreateToggle("Notifications", "Notifications")
CreateToggle("Auto Farm", "AutoFarm")
CreateToggle("Auto Mastery", "AutoMastery")
CreateToggle("Auto Farm Materials", "AutoFarmMaterials")
CreateToggle("Quest Helper", "QuestHelper")
CreateToggle("Auto Quest", "AutoQuest")
CreateToggle("Collect Drops", "CollectDrops")

CreateToggle("Auto Haki", "AutoHaki")
CreateToggle("Auto Observation", "AutoObservation")
CreateToggle("Fast Attack", "FastAttack")
CreateToggle("Bring Mobs", "BringMobs")

CreateToggle("Auto Raid", "AutoRaid")
CreateToggle("Auto Collect Fragments", "AutoCollectFragments")
CreateToggle("Auto Awaken", "AutoAwaken")

CreateToggle("Auto V4", "AutoV4")
CreateToggle("Auto Find Gear", "AutoFindGear")
CreateToggle("Auto Collect Gear", "AutoCollectGear")
CreateToggle("Auto Train", "AutoTrain")
CreateToggle("Auto Activate", "AutoActivate")
CreateToggle("Auto Trial", "AutoTrial")

CreateToggle("Auto Random Fruit", "AutoRandomFruit")
CreateToggle("Auto Collect Fruit", "AutoCollectFruit")
CreateToggle("Auto Store Fruit", "AutoStoreFruit")
CreateToggle("Fruit ESP", "FruitESP")

CreateToggle("Auto Sea Event", "AutoSeaEvent")
CreateToggle("Auto Sea Beast", "AutoSeaBeast")
CreateToggle("Auto Ship Raid", "AutoShipRaid")
CreateToggle("Auto Terrorshark", "AutoTerrorshark")
CreateToggle("Auto Kitsune Island", "AutoKitsuneIsland")
CreateToggle("Auto Prehistoric Island", "AutoPrehistoricIsland")
CreateToggle("Auto Frozen Dimension", "AutoFrozenDimension")
CreateToggle("Auto Leviathan", "AutoLeviathan")
CreateToggle("Auto Mirage Island", "AutoMirageIsland")

CreateToggle("Auto Target", "AutoTarget")
CreateToggle("Combo Helper", "ComboHelper")
CreateToggle("Skill Helper", "SkillHelper")
CreateToggle("Aim Assist", "AimAssist")

CreateDropdown("Weapon", "SelectedWeapon", {"Default", "Melee", "Sword", "Gun"})
CreateDropdown("Farm Method", "FarmMethod", {"Nearest", "Above", "Behind"})
CreateDropdown("Basic Raid", "BasicRaid", {"Flame", "Ice", "Quake", "Light", "Dark", "String", "Rumble", "Magma", "Buddha", "Bird", "Sand", "Darkness"})
CreateDropdown("Advanced Raid", "AdvancedRaid", {"Phoenix", "Dough"})
CreateDropdown("PvP Mode", "PvPMode", {"Off", "Bounty", "Friendly"})
CreateDropdown("Select Fruit", "SelectFruit", {"None", "Leopard", "Dragon", "Dough", "Venom", "Soul", "Shadow"})
CreateDropdown("Select Rarity", "SelectRarity", {"Any", "Mythical", "Legendary", "Rare"})

--------------------------------------------------
-- WALK SPEED
--------------------------------------------------

local function ApplyWalkSpeed()
    local Character = Player.Character
    if not Character then return end
    local Humanoid = Character:FindFirstChildOfClass("Humanoid")
    if Humanoid then
        Humanoid.WalkSpeed = Config.WalkSpeed
    end
end

Player.CharacterAdded:Connect(function()
    task.wait(1)
    ApplyWalkSpeed()
end)

ApplyWalkSpeed()

--------------------------------------------------
-- AUTO SAVE
--------------------------------------------------

task.spawn(function()
    while task.wait(60) do
        SaveConfig()
    end
end)

print("[AZURE HUB] Đã tải toàn bộ chức năng thành công qua Loadstring!")

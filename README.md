local Player = game.Players.LocalPlayer
local Character = Player.Character or Player.CharacterAdded:Wait()

local function moveTo(target)
    local humanoidRootPart = Character:WaitForChild("HumanoidRootPart")
    humanoidRootPart.CFrame = target.CFrame
    wait(1)
end

local function clickDetector(target)
    fireclickdetector(target:FindFirstChildOfClass("ClickDetector"))
end

local function collectFruit(fruit)
    moveTo(fruit)
    clickDetector(fruit)
end

game:GetService("Workspace").Fruits.ChildAdded:Connect(collectFruit)
for _, fruit in pairs(game:GetService("Workspace").Fruits:GetChildren()) do
    collectFruit(fruit)
end

local function selectTool(toolType)
    for _, tool in pairs(Character:GetChildren()) do
        if tool:IsA("Tool") and tool.Name:find(toolType) then
            return tool
        end
    end
    return nil
end

local function attackEnemy(enemy, tool)
    moveTo(enemy)
    if tool then
        Character:EquipTool(tool)
        tool:Activate()
    end
end

game:GetService("Workspace").Enemies.ChildAdded:Connect(function(enemy)
    local tool = selectTool("Melee")
    attackEnemy(enemy, tool)
end)
for _, enemy in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
    local tool = selectTool("Melee")
    attackEnemy(enemy, tool)
end

local function followMirage(mirage)
    moveTo(mirage)
end

game:GetService("Workspace").Mirages.ChildAdded:Connect(followMirage)
for _, mirage in pairs(game:GetService("Workspace").Mirages:GetChildren()) do
    followMirage(mirage)
end

local function autoSpinFruit()
    local fruitDealer = game:GetService("Workspace"):FindFirstChild("FruitDealer")
    if fruitDealer then
        moveTo(fruitDealer)
        clickDetector(fruitDealer)
    end
end

autoSpinFruit()

local function autoKitsuneIsland()
    local kitsuneIsland = game:GetService("Workspace"):FindFirstChild("KitsuneIsland")
    if kitsuneIsland then
        moveTo(kitsuneIsland)
    end
end

local function autoTrueTripleKatana()
    local katanaNPC = game:GetService("Workspace"):FindFirstChild("KatanaNPC")
    if katanaNPC then
        moveTo(katanaNPC)
        clickDetector(katanaNPC)
    end
end

local function autoCursedKatana()
    local cursedKatanaNPC = game:GetService("Workspace"):FindFirstChild("CursedKatanaNPC")
    if cursedKatanaNPC then
        moveTo(cursedKatanaNPC)
        clickDetector(cursedKatanaNPC)
    end
end

local function checkNextFullMoon()
    local fullMoonIndicator = game:GetService("Workspace"):FindFirstChild("FullMoonIndicator")
    if fullMoonIndicator then
        print("Próxima lua cheia em: " .. fullMoonIndicator.Value)
    end
end

local function autoDistributeStats(statType, points)
    local stats = Player:FindFirstChild("leaderstats")
    if stats and stats:FindFirstChild(statType) then
        stats[statType].Value = stats[statType].Value + points
    end
end

local function autoEvolveRace(version)
    local raceNPC = game:GetService("Workspace"):FindFirstChild("RaceNPC")
    if raceNPC then
        moveTo(raceNPC)
        clickDetector(raceNPC)
    end
end

local function autoRaid()
    local raidStarter = game:GetService("Workspace"):FindFirstChild("RaidStarter")
    if raidStarter then
        moveTo(raidStarter)
        clickDetector(raidStarter)
    end
end

local function autoTeleportIsland(islandName)
    local island = game:GetService("Workspace"):FindFirstChild(islandName)
    if island then
        moveTo(island)
    end
end

local function autoCollectMaterials()
    for _, material in pairs(game:GetService("Workspace").Materials:GetChildren()) do
        moveTo(material)
        clickDetector(material)
    end
end

local function autoEliteHunter()
    for _, elite in pairs(game:GetService("Workspace").Elites:GetChildren()) do
        moveTo(elite)
        local tool = selectTool("Melee")
        if tool then
            tool:Activate()
        end
    end
end

local function autoCakePrince()
    local cakePrince = game:GetService("Workspace"):FindFirstChild("CakePrince")
    if cakePrince then
        moveTo(cakePrince)
        local tool = selectTool("Melee")
        if tool then
            tool:Activate()
        end
    end
end

local function autoSoulGuitar()
    local soulGuitarNPC = game:GetService("Workspace"):FindFirstChild("SoulGuitarNPC")
    if soulGuitarNPC then
        moveTo(soulGuitarNPC)
        clickDetector(soulGuitarNPC)
    end
end

local function autoBlackbeard()
    local blackbeard = game:GetService("Workspace"):FindFirstChild("Blackbeard")
    if blackbeard then
        moveTo(blackbeard)
        local tool = selectTool("Melee")
        if tool then
            tool:Activate()
        end
    end
end

local function autoSeaEvents()
    for _, event in pairs(game:GetService("Workspace").SeaEvents:GetChildren()) do
        moveTo(event)
    end
end

local function autoBoat()
    local boatDealer = game:GetService("Workspace"):FindFirstChild("BoatDealer")
    if boatDealer then
        moveTo(boatDealer)
        clickDetector(boatDealer)
    end
end

local function autoTrainGodSuperHuman()
    local trainer = game:GetService("Workspace"):FindFirstChild("TrainerNPC")
    if trainer then
        moveTo(trainer)
        clickDetector(trainer)
    end
end

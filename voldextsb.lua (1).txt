local DrRayLibrary = loadstring(game:HttpGet("https://raw.githubusercontent.com/AZYsGithub/DrRay-UI-Library/main/DrRay.lua"))()
local window = DrRayLibrary:Load("VOLDEX HUB", "Default")
local tab = DrRayLibrary.newTab("Main", "ImageIdHere")
tab.newToggle("view dummy", "Toggle! (prints the state)", false, function(toggleState)
    if toggleState then
        game.Workspace.Camera.CameraSubject = game.Workspace.Live:FindFirstChild("Weakest Dummy").Humanoid
    else
       game.Workspace.Camera.CameraSubject = game.Players.LocalPlayer.Character.Humanoid
    end
end)
tab.newButton("fe kill all gui", "yes gives you kills made by its louis playz", function()
loadstring(game:HttpGet("https://raw.githubusercontent.com/louismich4el/ItsLouisPlayz-Scripts/main/VOID%20V2%20TSB.lua"))()
end)
tab.newButton("death counter identifier", "by its louis playz", function()
loadstring(game:HttpGet("https://raw.githubusercontent.com/louismich4el/ItsLouisPlayz-Scripts/main/TSB%20Death%20Counter%20Identifier.lua"))()
end)

tab.newButton("dodge omni dierctional punch wnd table flip", "by its louis playz", function()
DistanceToDodgeOmni_Table = 500
loadstring(game:HttpGet("https://raw.githubusercontent.com/louismich4el/ItsLouisPlayz-Scripts/main/Auto%20Dodge%20Omni%20And%20Table.lua"))()
end)
tab.newButton("anti lag", "mqho gyst gyat", function()
loadstring(game:HttpGet("https://raw.githubusercontent.com/louismich4el/ItsLouisPlayz-Scripts/main/TSB%20Anti%20Lag.lua"))()
end)
tab.newButton("fe invisiblility", "mqho gyst gyat", function()
loadstring(game:HttpGet("https://pastebin.com/raw/3Rnd9rHf",true))()
end)
tab.newButton("KJ HAX", "KEY = TSB920Z", function()
loadstring(game:HttpGet("https://rentry.co/tghuofnu/raw"))()
end)
tab.newButton("tp to random trashcan", "mqho gyst gyat", function()
local function teleportToTrashcan()
    local trashFolder = game.Workspace:FindFirstChild("Map") and game.Workspace.Map:FindFirstChild("Trash")
    if trashFolder then
        local trashcans = {}
        for _, model in ipairs(trashFolder:GetChildren()) do
            if model:IsA("Model") and model.Name == "Trashcan" then
                table.insert(trashcans, model)
            end
        end

        if #trashcans > 0 then
            local randomTrashcan = trashcans[math.random(1, #trashcans)]
            local teleportPart = randomTrashcan.PrimaryPart or randomTrashcan:FindFirstChildWhichIsA("BasePart")

            if teleportPart then
                local character = player.Character
                if character and character:FindFirstChild("HumanoidRootPart") then
                    character.HumanoidRootPart.CFrame = teleportPart.CFrame + Vector3.new(0, 3, 0) -- Teleport above the trashcan
                end
            end
        end
    end
end

end)
tab.newButton("ESP", " Hello!", function()
loadstring(game:HttpGet"https://raw.githubusercontent.com/Lucasfin000/SpaceHub/main/UESP")()
end)
tab.newButton("NO STUN", "Prints Hello!", function()
loadstring(game:HttpGet("https://raw.githubusercontent.com/tamarixr/tamhub/main/nostun.lua",true))()
end)
tab.newToggle("ESP", "Toggle! (prints the state)", false, function(toggleState)
    if toggleState then
        -- Function to create a highlight for players
local function highlightPlayer(plr)
    if not plr.Character then return end
    local highlight = Instance.new("Highlight")
    highlight.Name = "PlayerHighlight_" .. plr.Name
    highlight.FillColor = Color3.fromRGB(0, 85, 255)
    highlight.FillTransparency = 0.3
    highlight.OutlineColor = Color3.fromRGB(255, 255, 255)
    highlight.OutlineTransparency = 0
    highlight.DepthMode = "AlwaysOnTop"
    highlight.Adornee = plr.Character
    highlight.Parent = Storage

    -- Update adornee if the player respawns
    plr.CharacterAdded:Connect(function(char)
        highlight.Adornee = char
    end)
end

-- Function to highlight objects in the workspace
local function highlightObjects()
    for _, obj in pairs(workspace:GetDescendants()) do
        if obj:IsA("BasePart") and not obj:IsDescendantOf(lp.Character) then
            local highlight = Instance.new("Highlight")
            highlight.Name = "PartHighlight_" .. obj:GetDebugId(2)
            highlight.FillColor = Color3.fromRGB(255, 255, 255)
            highlight.FillTransparency = 0.9
            highlight.OutlineColor = Color3.fromRGB(255, 255, 255)
            highlight.OutlineTransparency = 0
            highlight.DepthMode = "AlwaysOnTop"
            highlight.Adornee = obj
            highlight.Parent = Storage
        end
    end
end

-- Function to create a tracer part
local function createTracer(targetPos)
    local tracer = Instance.new("Part")
    tracer.Size = Vector3.new(0.1, 0.1, (lp.Character.HumanoidRootPart.Position - targetPos).Magnitude)
    tracer.Anchored = true
    tracer.CanCollide = false
    tracer.Material = Enum.Material.SmoothPlastic
    tracer.Color = Color3.fromRGB(0, 255, 255)
    tracer.CFrame = CFrame.new(lp.Character.HumanoidRootPart.Position, targetPos) * CFrame.new(0, 0, -tracer.Size.Z / 2)
    tracer.Transparency = 0.5
    tracer.Parent = workspace
    return tracer
end

-- Function to update tracers for players
local function updateTracers()
    for _, player in ipairs(Players:GetPlayers()) do
        if player ~= lp and player.Character and player.Character:FindFirstChild("HumanoidRootPart") then
            local targetPos = player.Character.HumanoidRootPart.Position
            if not tracers[player] then
                tracers[player] = createTracer(targetPos)
            else
                local tracer = tracers[player]
                tracer.Size = Vector3.new(0.1, 0.1, (lp.Character.HumanoidRootPart.Position - targetPos).Magnitude)
                tracer.CFrame = CFrame.new(lp.Character.HumanoidRootPart.Position, targetPos) * CFrame.new(0, 0, -tracer.Size.Z / 2)
            end
        end
    end
end

-- Function to enable ESP
local function enableESP()
    espEnabled = true
    Lighting.FogStart = 0
    Lighting.FogEnd = 50
    Lighting.FogColor = Color3.new(0, 0, 0)
    Lighting:SetMinutesAfterMidnight(0) -- Default night skybox

    for _, player in ipairs(Players:GetPlayers()) do
        if player ~= lp then
            highlightPlayer(player)
        end
    end

    highlightObjects()

    RunService.RenderStepped:Connect(updateTracers)
end

-- Function to disable ESP
local function disableESP()
    espEnabled = false
    Lighting.FogStart = originalFogStart
    Lighting.FogEnd = originalFogEnd
    Lighting.FogColor = Color3.new(1, 1, 1)
    Lighting:SetMinutesAfterMidnight(600) -- Default day skybox

    Storage:ClearAllChildren()

    for _, tracer in pairs(tracers) do
        if tracer then tracer:Destroy() end
    end
    tracers = {}
end

-- Toggle ESP
local function toggleESP()
    if espEnabled then
        disableESP()
    else
        enableESP()
    end
end

    else
        disableESP()
    end
end)
tab.newButton("dunked on! (with second garou move)", "Prints Hello!", function()
loadstring(game:HttpGet("https://raw.githubusercontent.com/tamarixr/tamhub/main/wwoa.lua"))()
end)
tab.newButton("ult detector", "mqho gyst gyat", function()
loadstring(game:HttpGet"https://raw.githubusercontent.com/tamarixr/tamhub/main/ultdetec.lua")()
end)
tab.newButton("free emotes", "Prints Hello!", function()
    loadstring(game:HttpGet("https://raw.githubusercontent.com/XXSCRIPTSS/FREE-EMOTES/refs/heads/main/OP%20XXSC%20BY%20NETLESSED",true))()
end)

tab.newButton("betless hub", "its trash kinda", function()
    loadstring(game:HttpGet("https://rentry.org/betless-hub-x",true))()
end)
tab.newButton("Aim Lock", "Prints Hello!", function()
    loadstring(game:HttpGet("https://raw.githubusercontent.com/sdfesdfsedf/srgtergasdfs/main/silent",true))()
end)
tab.newButton("Fps Booster", "eskibido", function()
    setfpscap(9999)
end)
tab.newButton("Invisible Tableflip", "Self Explanatory", function()
    loadstring(game:HttpGet("https://raw.githubusercontent.com/tamarixr/tamhub/main/invistableflip.lua",true))()
end)
local tab = DrRayLibrary.newTab("AUTO FARM", "ImageIdHere")
tab.newButton("VEXON HUB", "Prints Hello!", function()
    loadstring(game:HttpGet("https://raw.githubusercontent.com/DiosDi/VexonHub/main/TSB-VexonHub"))()
end)
tab.newButton("speed hub", "bestt", function()
    loadstring(game:HttpGet("https://raw.githubusercontent.com/AhmadV99/Speed-Hub-X/main/Speed%20Hub%20X.lua", true))()
end)
tab.newButton("VOLDEX autofarm", "by me", function()
    loadstring(game:HttpGet("https://raw.githubusercontent.com/SUPREMEXXSC/9BITS-AUTOFARM/refs/heads/main/Skibdii%20skibdiii",true))()
end)
tab.newButton("Void Kill 1st Garou And 2nd Garou move", "Prints Hello!", function()
    loadstring(game:HttpGet"https://raw.githubusercontent.com/loadlua/TSB/main/Insta-kill.lua")()
end)
tab.newButton("Auto Block", "Prints Hello!", function()
    loadstring(game:HttpGet("https://raw.githubusercontent.com/Cyborg883/TSB/refs/heads/main/CombatGui"))()
end)
tab.newButton("Block Aura", "Prints Hello!", function()
    loadstring(game:HttpGet("https://raw.githubusercontent.com/SUPREMEXXSC/Auto-lock/refs/heads/main/Skibidi",true))()
end)
local tab = DrRayLibrary.newTab("MISC", "ImageIdHere")
tab.newButton("get 1000 robix", "gives free robuc", function()
    game:GetService("Players").LocalPlayer:Kick("LOLOLOL BOZO GET SCAMMED  YOUR NOW BANNED FOR 1000000 YEARS")
end)
tab.newButton("discord", "bro no need to explain copy and paste it in dsc", function()
  setclipboard("https://discord.gg/kJXXtyycjC")  
end)
tab.newButton("CREDITS TO THEVOLDEX(ザヴォルデックス)", "And no one else", function()
    print('Hello!')
end)
tab.newButton("open developer console", "idk why im adding this", function()
    game:GetService("StarterGui"):SetCore("DevConsoleVisible",true)
end)
tab.newButton("sukuna divergent fist", "mqho gyst gyat", function()
local red1 = game.ReplicatedStorage.Resources.FiveSeasonsFX["CharFX"].ArmEnabled:Clone()
red1.Parent = game.Players.LocalPlayer.Character["Left Arm"]
    for _, child in ipairs(red1:GetChildren()) do
        if child:IsA("ParticleEmitter") then -- Check if the child is a ParticleEmitter
    child.Color = ColorSequence.new(Color3.fromRGB(255,0,0)) -- Set color to stuff        
            child:Emit(5) -- Emit 20 particles
        end
    end

local red1 = game.ReplicatedStorage.Resources.FiveSeasonsFX["CharFX"].ArmEnabled:Clone()
red1.Parent = game.Players.LocalPlayer.Character["Right Arm"]
    for _, child in ipairs(red1:GetChildren()) do
        if child:IsA("ParticleEmitter") then -- Check if the child is a ParticleEmitter
    child.Color = ColorSequence.new(Color3.fromRGB(255,0,0)) -- Set color to stuff        
            child:Emit(5) -- Emit 20 particles
        end
    end
end)
tab.newButton("get ban from tsb", "", function()
  loadstring(game:HttpGet"https://raw.githubusercontent.com/tamarixr/tamhub/main/instaban.lua")()  
end)
tab.newButton("tp tool", "mqho gyst gyat", function()
mouse = game.Players.LocalPlayer:GetMouse()
tool = Instance.new("Tool")
tool.RequiresHandle = false
tool.Name = "Tp tool(Equip to Click TP)"
tool.Activated:connect(function()
local pos = mouse.Hit+Vector3.new(0,2.5,0)
pos = CFrame.new(pos.X,pos.Y,pos.Z)
game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = pos
end)
tool.Parent = game.Players.LocalPlayer.Backpack

end)
tab.newButton("dex explorer", "mqho gyst gyat", function()
loadstring(game:HttpGet("https://raw.githubusercontent.com/MariyaFurmanova/Library/main/dex2.0", true))()
end)
tab.newButton("simple spy", "mqho gyst gyat", function()
loadstring(game:HttpGet("https://github.com/exxtremestuffs/SimpleSpySource/raw/master/SimpleSpy.lua"))()
end)
tab.newButton("inf yield", "mqho gyst gyat", function()
loadstring(game:HttpGet('https://raw.githubusercontent.com/EdgeIY/infiniteyield/master/source'))()
end)
tab.newButton("jerk off", "mqho gyst gyat", function()
loadstring(game:HttpGet("https://rawscripts.net/raw/Universal-Script-Jerk-Off-R15-and-R6-Modified-Reuplode-25935"))()
end)
tab.newButton("tp up", "mqho gyst gyat", function()
game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(150.58279418945312, 633.8984375, -24.420745849609375)
end)
tab.newButton("sans blawster", "mqho gyst gyat", function()
-- Táº¡o Tool
local Tool = Instance.new("Tool")
Tool.Name = "Sans Blaster"
Tool.RequiresHandle = false  -- KhÃ´ng cáº§n pháº§n "Handle" vÃ¬ chÃºng ta sáº½ táº¡o cÃ¡c Ä‘á»‘i tÆ°á»£ng khÃ¡c

-- GÃ¡n Tool vÃ o StarterPack (hoáº·c gÃ¡n trá»±c tiáº¿p cho nhÃ¢n váº­t ngÆ°á»i chÆ¡i)
Tool.Parent = game.Players.LocalPlayer.Backpack

-- Khi ngÆ°á»i chÆ¡i kÃ­ch hoáº¡t Tool
Tool.Activated:Connect(function()
    local char = game.Players.LocalPlayer.Character
    local blastsound = Instance.new("Sound", char.Torso)
    blastsound.SoundId = "rbxassetid://8561500387"  -- Thay báº±ng ID Ã¢m thanh thá»±c táº¿

    -- Táº¡o Gaster Blaster
    local gasterblaster = Instance.new("Part")
    gasterblaster.Size = Vector3.new(7, 16, 4)
    gasterblaster.CanCollide = false
    gasterblaster.Parent = char.Torso

    local gasterblastermesh = Instance.new("FileMesh", gasterblaster)
    gasterblastermesh.MeshId = "rbxassetid://431908407"
    gasterblastermesh.Scale = Vector3.new(0.05, 0.05, 0.05)

    local gasterblastertexture = Instance.new("Decal", gasterblaster)
    gasterblastertexture.Face = "Back"
    gasterblastertexture.Texture = "http://www.roblox.com/asset/?id=441975828"

    -- LiÃªn káº¿t Gaster Blaster vá»›i Torso
    local weeld = Instance.new("Weld", gasterblaster)
    weeld.Part0 = gasterblaster
    weeld.Part1 = char.Torso
    weeld.C0 = CFrame.new(3.71674585, -11.54426, -0.129204988, -0.999741375, 0, 0.0227420069, 0, 1, 0, -0.0227420069, 0, -0.999741375)

    blastsound:Play()

    -- Äáº£m báº£o Ä‘áº§u nhÃ¢n váº­t khÃ´ng di chuyá»ƒn trong khi vá»¥ ná»• xáº£y ra
    char.Head.Anchored = true
    wait(1)

    -- Táº¡o blast (vá»¥ ná»•)
    local blast = Instance.new("Part")
    blast.Size = Vector3.new(18.07, 16.36, 73.54)
    blast.Transparency = 0.7
    blast.Material = "Neon"
    blast.Color = Color3.new(1, 1, 1)
    blast.CanCollide = true
    blast.Parent = gasterblaster

    local blastweld = Instance.new("Weld", blast)
    blastweld.Part0 = blast
    blastweld.Part1 = gasterblaster
    blastweld.C0 = CFrame.new(-0.430000305, 1.73999977, -40.1399994, 1, 0, 0, 0, 1, 0, 0, 0, 1)

    -- Xá»­ lÃ½ sá»± kiá»‡n khi váº­t thá»ƒ va cháº¡m vá»›i blast
    blast.Touched:Connect(function(part)
        local humanoid = part.Parent:FindFirstChildOfClass("Humanoid")
        if humanoid then
            humanoid.Health = 0  -- Hoáº·c cÃ³ thá»ƒ lÃ m tÃª liá»‡t, thay vÃ¬ tiÃªu diá»‡t
        end
    end)

    -- Sau khi blast hoÃ n táº¥t, bá» anchor cho Ä‘áº§u vÃ  xÃ³a Gaster Blaster
    wait(2)
    char.Head.Anchored = false
    blast:Destroy()
    gasterblaster:Destroy()
end)
end)
tab.newButton("GOJO DIVERGENT FIST", "mqho gyst gyat", function()
local player = game.Players.LocalPlayer
local character = player.Character or player.CharacterAdded:Wait()
local cursedEnergy = game:GetService("ReplicatedStorage").Emotes.cursedEnergy
if cursedEnergy then
    local function applyVfxToArm(arm, offset)
        local vfxPart = cursedEnergy:Clone()
        vfxPart.Parent = character
        vfxPart.CFrame = arm.CFrame * CFrame.new(0, offset, 0) * CFrame.Angles(math.rad(90), 0, 0)
        local weld = Instance.new("WeldConstraint")
        weld.Part0 = arm
        weld.Part1 = vfxPart
        weld.Parent = vfxPart
        local attachment0 = Instance.new("Attachment", vfxPart)
        attachment0.Name = "TrailAttachment0"
        local attachment1 = Instance.new("Attachment", arm)
        attachment1.Name = "TrailAttachment1"
        for i = 1, 2 do
            local trail = Instance.new("Trail")
            trail.Name = "ChaoticTrail_" .. i
            trail.Attachment0 = attachment0
            trail.Attachment1 = attachment1
            trail.Texture = "rbxassetid://11745241946"
            trail.Color = ColorSequence.new({
                ColorSequenceKeypoint.new(0, Color3.fromRGB(0, 0, 0)),
                ColorSequenceKeypoint.new(0.5, Color3.fromRGB(21, 103, 159)),
                ColorSequenceKeypoint.new(1, Color3.fromRGB(52, 202, 237))
            })
            trail.Lifetime = 0.3
            trail.MinLength = 0.1
            trail.LightInfluence = 0
            trail.Transparency = NumberSequence.new({
                NumberSequenceKeypoint.new(0, 0),
                NumberSequenceKeypoint.new(0.1, 0.1),
                NumberSequenceKeypoint.new(1, 0.5)
            })
            trail.FaceCamera = true
            trail.Enabled = true
            trail.Parent = vfxPart
        end
        print("Cursed Energy effect with gradient trail applied to arm!")
    end
    local rightArm = character:WaitForChild("Right Arm")
    local leftArm = character:WaitForChild("Left Arm")
    if rightArm then
        applyVfxToArm(rightArm, -1.0)
    else
        warn("Right Arm not found!")
    end
    if leftArm then
        applyVfxToArm(leftArm, -1.0)
    else
        warn("Left Arm not found!")
    end
else
    warn("cursedEnergy not found in ReplicatedStorage.Emotes")
end
end)
tab.newButton("YUJI DIVERGENT FIST", "mqho gyst gyat", function()
local red1 = game.ReplicatedStorage.Resources.FiveSeasonsFX["CharFX"].ArmEnabled:Clone()
red1.Parent = game.Players.LocalPlayer.Character["Left Arm"]
    for _, child in ipairs(red1:GetChildren()) do
        if child:IsA("ParticleEmitter") then -- Check if the child is a ParticleEmitter
    child.Color = ColorSequence.new(Color3.fromRGB(106, 191, 208)) -- Set color to stuff        
            child:Emit(5) -- Emit 20 particles
        end
    end

local red1 = game.ReplicatedStorage.Resources.FiveSeasonsFX["CharFX"].ArmEnabled:Clone()
red1.Parent = game.Players.LocalPlayer.Character["Right Arm"]
    for _, child in ipairs(red1:GetChildren()) do
        if child:IsA("ParticleEmitter") then -- Check if the child is a ParticleEmitter
    child.Color = ColorSequence.new(Color3.fromRGB(106, 191, 208)) -- Set color to stuff        
            child:Emit(5) -- Emit 20 particles
        end
    end
end)

tab.newButton("run tool", "mqho gyst gyat", function()
loadstring(game:HttpGet"https://raw.githubusercontent.com/tamarixr/tamhub/main/run.lua")()
end)
tab.newButton("no dash cooldown", "mqho gyst gyat", function()
loadstring(game:HttpGet"https://raw.githubusercontent.com/tamarixr/tamhub/main/nnocd.lua")()
end)
tab.newButton("domain tool", "mqho gyst gyat", function()
local tool = Instance.new("Tool")
tool.Name = "Domain"
tool.RequiresHandle = false  -- No handle needed


tool.Parent = game.Players.LocalPlayer.Backpack


tool.Activated:Connect(function()
    print("Tool activated!")


    local code = [[
loadstring(game:HttpGet"https://raw.githubusercontent.com/tamarixr/tamhub/main/ddo.lua")()  
    ]]
    local func = loadstring(code)
    if func then
        func()
    end
end)
end)

tab.newButton("SKIBIDI WORKING JK UFW BY ME", "Prints Hello!", function()
    -- Settings
local noDelay=true
local animationId = "rbxassetid://77727115892579" -- Animation ID to trigger the video
local videoFile = "JKUFW.mp4"
local videoUrl = "https://raw.githubusercontent.com/softbf395/JK-unlimitedReskin/refs/heads/main/JK.mp4"
local videoFileND = "JKUFWND.mp4"
local videoUrlND = "https://raw.githubusercontent.com/softbf395/JK-unlimitedReskin/refs/heads/main/JKNoDelay.mp4"
local AudioP = "JKNDAudio.mp4"
local AudioU = "https://raw.githubusercontent.com/softbf395/JK-unlimitedReskin/refs/heads/main/JKNoDelay.mp3"

-- Services
local players = game:GetService("Players")

local function stopAllSounds()
if noDelay == false then
    task.wait(1)
    for _, instance in ipairs(game:GetDescendants()) do
        if instance:IsA("Sound") then
            instance.Playing = false
        end
    end
else
  task.wait(0.2)
    for _, instance in ipairs(game:GetDescendants()) do
        if instance:IsA("Sound") then
            instance.Playing = false
        end
    end
    local AuID = getcustomasset(AudioP)
    local Au = Instance.new("Sound")
    Au.Parent = workspace
    Au.SoundId = AuID
    Au:Play()
end
end

local function setup(humanoid)
    if humanoid then
        humanoid.Animator.AnimationPlayed:Connect(function(animTrack)
            if animTrack.Animation and animTrack.Animation.AnimationId == animationId then
                stopAllSounds()

                local screenGui = Instance.new("ScreenGui")
                screenGui.IgnoreGuiInset = true
                screenGui.ScreenInsets = Enum.ScreenInsets.None
                screenGui.DisplayOrder = 9999
                screenGui.Parent = players.LocalPlayer:WaitForChild("PlayerGui")

                local videoFrame = Instance.new("Frame", screenGui)
                videoFrame.Size = UDim2.new(1, 0, 1, 0)
                videoFrame.BackgroundTransparency = 1

                local video = Instance.new("VideoFrame", videoFrame)
                video.Size = UDim2.new(1, 0, 1, 0)
                video.BackgroundTransparency = 1
                video.Video = getcustomasset(noDelay and videoFileND or videoFile)

                videoFrame.Visible = true
                if noDelay == true then video.Volume = 0 end
                video.Visible = true
                video:Play()

                video.Ended:Connect(function()
                    screenGui:Destroy()
                end)
            end
        end)
    end
end

local function init()
    local player = players.LocalPlayer
    if not isfile(videoFile) or not isfile(videoFileND) or not isfile(AudioP) then
        local screenGui = Instance.new("ScreenGui")
        screenGui.IgnoreGuiInset = true
        screenGui.ScreenInsets = Enum.ScreenInsets.None
        screenGui.ResetOnSpawn = false
        screenGui.DisplayOrder = 9999
        screenGui.Parent = player:WaitForChild("PlayerGui")

        local loadingText = Instance.new("TextLabel", screenGui)
        loadingText.Size = UDim2.new(0.3, 0, 0.1, 0)
        loadingText.Position = UDim2.new(0.35, 0, 0.45, 0)
        loadingText.BackgroundTransparency = 1
        loadingText.TextScaled = true
        loadingText.TextColor3 = Color3.new(1, 1, 1)
        loadingText.Font = Enum.Font.SourceSansBold
        loadingText.Text = "Downloading Videos. (made by thevoldex)"
        loadingText.Visible = true

        if not isfile(videoFileND) then writefile(videoFile, game:HttpGet(videoUrl)) end
        if not isfile(videoFileND) then writefile(videoFileND, game:HttpGet(videoUrlND)) end

        loadingText.Text = "Download Complete!"
        task.wait(1.5)
loadingText.Text = "Downloading No Delay Audio..."
        loadingText.Visible = true

        if not isfile(AudioP) then writefile(AudioP, game:HttpGet(AudioU)) end

        loadingText.Text = "Download Complete!"
task.wait(1.5)
        screenGui:Destroy()
    end

    if player.Character then
        setup(player.Character:FindFirstChildOfClass("Humanoid"))
    end
player.CharacterAdded:Connect(function(chr)
wait(1)
setup(chr:FindFirstChildOfClass("Humanoid"))
end)
end
init()
end)
tab.newButton("free premium wave key generator enter your user in gui", "mqho gyst gyat", function()
loadstring(game:HttpGet("https://raw.githubusercontent.com/tamarixr/tamhub/main/free.lua",true))()
end)
tab.newButton("sound banhammer", "mqho gyst gyat", function()
loadstring(game:HttpGet("https://raw.githubusercontent.com/ShutUpJamesTheLoser/Banhammer/refs/heads/main/ban", true))()
end)
tab.newButton("kizaru", "Prints Hello!", function()
loadstring(game:HttpGet("https://paste.ee/r/NPnfk"))()
end)
tab.newButton("jjs gojo", "Prints Hello!", function()
loadstring(game:HttpGet("https://raw.githubusercontent.com/damir512/jjsgojov3/main/SaitamaToGojoV3_SOURCE-obfuscated_2.txt",true))()
end)
tab.newButton("luffy", "Prints Hello!", function()
loadstring(game:HttpGet("https://github.com/aggiealledge/obfuscated-scripts/raw/refs/heads/main/Protected_7732857839120517.txt"))()
end)
tab.newButton("CHAINSAW MAN", "Prints Hello!", function()
loadstring(game:HttpGet("https://gist.githubusercontent.com/GoldenHeads2/0fd8d36993c850f3fac89e5adf793076/raw/ab4f5a42bd0b2e24a32a46301d533ea849ca771c/gistfile1.txt"))()
end)
tab.newButton("SAITAMA TO GOJO BY ME", "Prints Hello!", function()
loadstring(game:HttpGet("https://pastebin.com/raw/Ty4Y6zfF",true))()
end)
tab.newButton("ATOMIC TO MEGUNA", "Prints Hello!", function()
loadstring(game:HttpGet("https://raw.githubusercontent.com/SerialdesignationV-collab/Meguna-Script-Yippee/refs/heads/main/imma-patch-this-shit.lua"))()
end)
tab.newButton("saitama to hakari", "by hamlet", function()
    loadstring(game:HttpGet("https://pastebin.com/raw/eEDYWj8p"))()
end)
tab.newButton("garou to kj", "by kenjaku", function()
    loadstring(game:HttpGet("https://raw.githubusercontent.com/damir512/garoukjv1maybeidk/main/Protected_2460290213750059.txt",true))()
end)
tab.newButton("jjs mahito", "sigma i love ittt", function()
    loadstring(game:HttpGet('https://raw.githubusercontent.com/Kenjihin69/Kenjihin69/refs/heads/main/Mahitotsbupdate'))()
end)
tab.newButton("blade to yuta", "Prints Hello!", function()
    loadstring(game:HttpGet("https://raw.githubusercontent.com/damir512/AtomicToYuta/main/Protected_8122576078506000.txt"))()
end)
tab.newButton("garou to optimus", "cool", function()
    loadstring(game:HttpGet("https://raw.githubusercontent.com/DjngleQuandale/OptimusPrimeTsb/refs/heads/main/Optimusmoveset"))()
end)
tab.newButton("garou to cosmic garou", "ski", function()
    loadstring(game:HttpGet("https://raw.githubusercontent.com/LolnotaKid/Movesssssssloala/refs/heads/main/CustomMove.txt"))()
end)
tab.newButton("sukuna by my friend", "try now", function()
    loadstring(game:HttpGet("https://raw.githubusercontent.com/Luckyfromyoutube/SUKUNA/refs/heads/main/20%25VFX-FIRE"))()
end)
tab.newButton("garou to okarun by my friend", "skibdi", function()
    loadstring(game:HttpGet("https://raw.githubusercontent.com/Luckyfromyoutube/Okarun/refs/heads/main/20%25Okarun20%25Garou"))()
end)
tab.newButton("shibuya gojo by my friend", "cool", function()
    loadstring(game:HttpGet("https://raw.githubusercontent.com/Luckyfromyoutube/Shibuya-Gojo/refs/heads/main/TrueUltplusVfx"))()
end)
tab.newButton("Saitama To heain sukuna", "Prints Hello!", function()
loadstring(game:HttpGet("https://raw.githubusercontent.com/damir512/whendoesbrickdie/main/tspno.txt",true))()end)
tab.newButton("Saitama to jun", "Prints Hello!", function()
    loadstring(game:HttpGet("https://raw.githubusercontent.com/SUPREMEXXSC/BEST-JUN-MOVESET/refs/heads/main/Script",true))()
end)
tab.newButton("garou to gojo check character list", "Prints Hello!", function()
    loadstring(game:HttpGet("https://raw.githubusercontent.com/SUPREMEXXSC/Garou-to-gojo-MOVESEAtd/refs/heads/main/Best%20one%3F",true))()
end)
tab.newButton("Saitama to gojo", "Prints Hello!", function()
    loadstring(game:HttpGet("https://raw.githubusercontent.com/SerialdesignationV-collab/Saitama-To-Sorcerer/refs/heads/main/Gojo-Satoru(Protected%2BTwice).txt"))()
end)
tab.newButton("another Saitama to gojo", "Prints Hello!", function()
    loadstring(game:HttpGet("https://raw.githubusercontent.com/Skibiditoilethaterfr2024/Script-protected-blud-/refs/heads/main/Protected_4902678279449732.txt"))()
end)
tab.newButton(" garou to p diddy", "Prints Hello!", function()
loadstring(game:HttpGet("https://paste.ee/r/gKC8V"))()
end)
local tab = DrRayLibrary.newTab("Animations", "ImageIdHere")
tab.newButton("all anims old", "BY MAUTIKU", function()
    loadstring(game:HttpGet(('https://raw.githubusercontent.com/Mautiku/TSB-anim/main/TSBANIMS'),true))()
end)
tab.newButton("ALL ANIMS NEW", "BY MAUTIKU", function()
    loadstring(game:HttpGet('https://raw.githubusercontent.com/Mautiku/ehh/main/strong%20guest.lua.txt'))()
end)
tab.newButton("SUIRYU SPAWN ANIM", "Prints Hello!", function()
    local humanoid = player.Character.Humanoid
local character = player.Character or player.CharacterAdded:Wait()
local UserInputService = game:GetService("UserInputService")

local anim2 = Instance.new("Animation")
anim2.AnimationId = "rbxassetid://18435303746"

local playAnim2 = humanoid:LoadAnimation(anim2)
playAnim2:Play()

end)
tab.newButton("Saitama Spawn Anim", "Prints Hello!", function()
    local player = game.Players.LocalPlayer
repeat wait() until player.Character.Humanoid
local humanoid = player.Character.Humanoid
local character = player.Character or player.CharacterAdded:Wait()
local UserInputService = game:GetService("UserInputService")

local anim2 = Instance.new("Animation")
anim2.AnimationId = "rbxassetid://15957366251"

local playAnim2 = humanoid:LoadAnimation(anim2)
playAnim2:Play()

end)
tab.newButton("Garou spawn", "Prints Hello!", function()
    local player = game.Players.LocalPlayer
repeat wait() until player.Character.Humanoid
local humanoid = player.Character.Humanoid
local character = player.Character or player.CharacterAdded:Wait()
local UserInputService = game:GetService("UserInputService")

local anim2 = Instance.new("Animation")
anim2.AnimationId = "rbxassetid://15957376722"

local playAnim2 = humanoid:LoadAnimation(anim2)
playAnim2:Play()

end)
tab.newButton("Sonic Spawn", "Prints Hello!", function()
    local player = game.Players.LocalPlayer
repeat wait() until player.Character.Humanoid
local humanoid = player.Character.Humanoid
local character = player.Character or player.CharacterAdded:Wait()
local UserInputService = game:GetService("UserInputService")

local anim2 = Instance.new("Animation")
anim2.AnimationId = "rbxassetid://15957361339"

local playAnim2 = humanoid:LoadAnimation(anim2)
playAnim2:Play()

end)
tab.newButton("Metal bat spawn", "Prints Hello!", function()
    local player = game.Players.LocalPlayer
repeat wait() until player.Character.Humanoid
local humanoid = player.Character.Humanoid
local character = player.Character or player.CharacterAdded:Wait()
local UserInputService = game:GetService("UserInputService")

local anim2 = Instance.new("Animation")
anim2.AnimationId = "rbxassetid://15957371124"

local playAnim2 = humanoid:LoadAnimation(anim2)
playAnim2:Play()
end)
tab.newButton("Atomic samurai spawn", "Prints Hello!", function()
    local player = game.Players.LocalPlayer
repeat wait() until player.Character.Humanoid
local humanoid = player.Character.Humanoid
local character = player.Character or player.CharacterAdded:Wait()
local UserInputService = game:GetService("UserInputService")

local anim2 = Instance.new("Animation")
anim2.AnimationId = "rbxassetid://15983615423"

local playAnim2 = humanoid:LoadAnimation(anim2)
playAnim2:Play()
end)
tab.newButton("Genos Spawn", "Prints Hello!", function()
    local player = game.Players.LocalPlayer
repeat wait() until player.Character.Humanoid
local humanoid = player.Character.Humanoid
local character = player.Character or player.CharacterAdded:Wait()
local UserInputService = game:GetService("UserInputService")

local anim2 = Instance.new("Animation")
anim2.AnimationId = "rbxassetid://15957374019"

local playAnim2 = humanoid:LoadAnimation(anim2)
playAnim2:Play()

end)
tab.newButton("Five Seasons ", "Grayish", function()
    loadstring(game:HttpGet("https://pastebin.com/raw/FjratmKt"))()
end)

tab.newButton("KJ ult 1", "Black", function()
    loadstring(game:HttpGet("https://pastebin.com/raw/J9Kv4Y95"))()
end)

tab.newButton("KJ ult 2", "Blackish", function()
    loadstring(game:HttpGet("https://pastebin.com/raw/pwPfkbXf"))()
end)

tab.newButton("KJ M1 1", "Blackish", function()
    local player = game.Players.LocalPlayer
repeat wait() until player.Character.Humanoid
local humanoid = player.Character.Humanoid
local character = player.Character or player.CharacterAdded:Wait()
local UserInputService = game:GetService("UserInputService")

local anim = Instance.new("Animation")
anim.AnimationId = "rbxassetid://17325510002"

local playAnim = humanoid:LoadAnimation(anim)
anim.AnimationId = "rbxassetid://0"
playAnim:Play()
end)

tab.newButton("KJ M1 2", "Blackish", function()
    local player = game.Players.LocalPlayer
repeat wait() until player.Character.Humanoid
local humanoid = player.Character.Humanoid
local character = player.Character or player.CharacterAdded:Wait()
local UserInputService = game:GetService("UserInputService")

local anim = Instance.new("Animation")
anim.AnimationId = "rbxassetid://17325513870"

local playAnim = humanoid:LoadAnimation(anim)
anim.AnimationId = "rbxassetid://0"
playAnim:Play()

end)

tab.newButton("KJ M1 3", "Blackish", function()
    local player = game.Players.LocalPlayer
repeat wait() until player.Character.Humanoid
local humanoid = player.Character.Humanoid
local character = player.Character or player.CharacterAdded:Wait()
local UserInputService = game:GetService("UserInputService")

local anim = Instance.new("Animation")
anim.AnimationId = "rbxassetid://17325522388"

local playAnim = humanoid:LoadAnimation(anim)
anim.AnimationId = "rbxassetid://0"
playAnim:Play()
end)
tab.newButton("Dummy KJ", "Dummy Does Kj Awk", function()
    loadstring(game:HttpGet("https://pastebin.com/raw/QfHCKkG6"))()
end)

tab.newButton("Dummy Counter Player", "Dummy", function()
    local player = game.Players.LocalPlayer
repeat wait() until player.Character.Humanoid
local humanoid = player.Character.Humanoid
local character = player.Character or player.CharacterAdded:Wait()
local UserInputService = game:GetService("UserInputService")

local anim = Instance.new("Animation")
anim.AnimationId = "rbxassetid://18440406788"

local playAnim = humanoid:LoadAnimation(anim)
playAnim:Play()
end)

tab.newButton("Dummy Victim (kills)", "Dummy", function()
    local player = game.Players.LocalPlayer
repeat wait() until player.Character.Humanoid
local humanoid = player.Character.Humanoid
local character = player.Character or player.CharacterAdded:Wait()
local UserInputService = game:GetService("UserInputService")

local anim = Instance.new("Animation")
anim.AnimationId = "rbxassetid://18440398084"

local playAnim = humanoid:LoadAnimation(anim)
playAnim:Play()
wait(8)
humanoid.Health = 0
end)

tab.newButton("Dummy 2 person", "Dummy", function()
    loadstring(game:HttpGet("https://pastebin.com/raw/FEmhXs2N"))()
end)

tab.newButton("KJ Fourth M1", "boom", function()
local player = game.Players.LocalPlayer
repeat wait() until player.Character.Humanoid
local humanoid = player.Character.Humanoid
local character = player.Character or player.CharacterAdded:Wait()
local UserInputService = game:GetService("UserInputService")

local anim = Instance.new("Animation")
anim.AnimationId = "rbxassetid://17325537719"

local playAnim = humanoid:LoadAnimation(anim)
anim.AnimationId = "rbxassetid://0"
playAnim:Play()
end)
                
tab.newButton("KJ wall combo player", "gray", function()
    loadstring(game:HttpGet("https://pastebin.com/raw/N98hhFri"))()
end)

tab.newButton("KJ wall combo victim", "gray", function()
    loadstring(game:HttpGet("https://pastebin.com/raw/8iZ2s59J"))()
end)

tab.newButton("KJ wall combo 2 player", "gray", function()
    loadstring(game:HttpGet("https://pastebin.com/raw/tAvcjuFq"))()
end)

tab.newButton("KJ spawn", "scawwy!", function()
local player = game.Players.LocalPlayer
repeat wait() until player.Character.Humanoid
local humanoid = player.Character.Humanoid
local character = player.Character or player.CharacterAdded:Wait()
local UserInputService = game:GetService("UserInputService")
 
local anim2 = Instance.new("Animation")
anim2.AnimationId = "rbxassetid://17325160621"
 
local playAnim2 = humanoid:LoadAnimation(anim2)
playAnim2:Play()
 end)
tab.newButton("L emote", "Prints Hello!", function()
    local player = game.Players.LocalPlayer
repeat wait() until player.Character.Humanoid
local humanoid = player.Character.Humanoid
local character = player.Character or player.CharacterAdded:Wait()
local UserInputService = game:GetService("UserInputService")

local anim2 = Instance.new("Animation")
anim2.AnimationId = "rbxassetid://18231574269"

local playAnim2 = humanoid:LoadAnimation(anim2)
playAnim2:Play()

end)

tab.newButton("Sleepy emote", "Prints Hello!", function()
    local player = game.Players.LocalPlayer
repeat wait() until player.Character.Humanoid
local humanoid = player.Character.Humanoid
local character = player.Character or player.CharacterAdded:Wait()
local UserInputService = game:GetService("UserInputService")

local anim2 = Instance.new("Animation")
anim2.AnimationId = "rbxassetid://14348083862"

local playAnim2 = humanoid:LoadAnimation(anim2)
playAnim2:Play()

end)
tab.newButton("Bring it emote", "Prints Hello!", function()
    local player = game.Players.LocalPlayer
repeat wait() until player.Character.Humanoid
local humanoid = player.Character.Humanoid
local character = player.Character or player.CharacterAdded:Wait()
local UserInputService = game:GetService("UserInputService")

local anim2 = Instance.new("Animation")
anim2.AnimationId = "rbxassetid://13801083337"

local playAnim2 = humanoid:LoadAnimation(anim2)
playAnim2:Play()
end)
tab.newButton("KNEEL EMOTR", "Prints Hello!", function()
    local player = game.Players.LocalPlayer
repeat wait() until player.Character.Humanoid
local humanoid = player.Character.Humanoid
local character = player.Character or player.CharacterAdded:Wait()
local UserInputService = game:GetService("UserInputService")

local anim2 = Instance.new("Animation")
anim2.AnimationId = "rbxassetid://13721154327"

local playAnim2 = humanoid:LoadAnimation(anim2)
playAnim2:Play()
end)
tab.newButton("Tornado emote", "Prints Hello!", function()
    local player = game.Players.LocalPlayer
repeat wait() until player.Character.Humanoid
local humanoid = player.Character.Humanoid
local character = player.Character or player.CharacterAdded:Wait()
local UserInputService = game:GetService("UserInputService")

local anim2 = Instance.new("Animation")
anim2.AnimationId = "rbxassetid://18459285150"

local playAnim2 = humanoid:LoadAnimation(anim2)
playAnim2:Play()

end)
tab.newButton("Bully emote", "Prints Hello!", function()
    local player = game.Players.LocalPlayer
repeat wait() until player.Character.Humanoid
local humanoid = player.Character.Humanoid
local character = player.Character or player.CharacterAdded:Wait()
local UserInputService = game:GetService("UserInputService")

local anim2 = Instance.new("Animation")
anim2.AnimationId = "rbxassetid://14014580605"

local playAnim2 = humanoid:LoadAnimation(anim2)
playAnim2:Play()
end)
tab.newButton("Applause", "eskibidi", function()
    repeat wait() until player.Character.Humanoid
local humanoid = player.Character.Humanoid
local character = player.Character or player.CharacterAdded:Wait()
local UserInputService = game:GetService("UserInputService")

local anim2 = Instance.new("Animation")
anim2.AnimationId = "rbxassetid://14056379526"

local playAnim2 = humanoid:LoadAnimation(anim2)
playAnim2:Play()

end)
tab.newButton("HAIR DRYER EMOTE", "Prints Hello!", function()
    local player = game.Players.LocalPlayer
repeat wait() until player.Character.Humanoid
local humanoid = player.Character.Humanoid
local character = player.Character or player.CharacterAdded:Wait()
local UserInputService = game:GetService("UserInputService")

local anim2 = Instance.new("Animation")
anim2.AnimationId = "rbxassetid://17862799431"

local playAnim2 = humanoid:LoadAnimation(anim2)
playAnim2:Play()

end)
tab.newButton("itadori walk", "Prints Hello!", function()
    local player = game.Players.LocalPlayer
repeat wait() until player.Character.Humanoid
local humanoid = player.Character.Humanoid
local character = player.Character or player.CharacterAdded:Wait()
local UserInputService = game:GetService("UserInputService")

local anim2 = Instance.new("Animation")
anim2.AnimationId = "rbxassetid://15962326593"

local playAnim2 = humanoid:LoadAnimation(anim2)
playAnim2:Play()

end)
tab.newButton("Mahito run", "Prints Hello!", function()
    local player = game.Players.LocalPlayer
repeat wait() until player.Character.Humanoid
local humanoid = player.Character.Humanoid
local character = player.Character or player.CharacterAdded:Wait()
local UserInputService = game:GetService("UserInputService")

local anim2 = Instance.new("Animation")
anim2.AnimationId = "rbxassetid://15958281277"

local playAnim2 = humanoid:LoadAnimation(anim2)
playAnim2:Play()

end)
tab.newButton("ravage", "Prints Hello!", function()
    local player = game.Players.LocalPlayer
repeat wait() until player.Character.Humanoid
local humanoid = player.Character.Humanoid
local character = player.Character or player.CharacterAdded:Wait()
local UserInputService = game:GetService("UserInputService")

local anim2 = Instance.new("Animation")
anim2.AnimationId = "rbxassetid://16945550029"

local playAnim2 = humanoid:LoadAnimation(anim2)
playAnim2:Play()

end)
tab.newButton("COLLATERAL RUIN", "Prints Hello!", function()
    local player = game.Players.LocalPlayer
repeat wait() until player.Character.Humanoid
local humanoid = player.Character.Humanoid
local character = player.Character or player.CharacterAdded:Wait()
local UserInputService = game:GetService("UserInputService")

local anim2 = Instance.new("Animation")
anim2.AnimationId = "rbxassetid://17325254223"

local playAnim2 = humanoid:LoadAnimation(anim2)
playAnim2:Play()

end)
tab.newButton("ult stand variant", "Prints Hello!", function()
    local player = game.Players.LocalPlayer
repeat wait() until player.Character.Humanoid
local humanoid = player.Character.Humanoid
local character = player.Character or player.CharacterAdded:Wait()
local UserInputService = game:GetService("UserInputService")

local anim2 = Instance.new("Animation")
anim2.AnimationId = "rbxassetid://17140902079"

local playAnim2 = humanoid:LoadAnimation(anim2)
playAnim2:Play()

end)
tab.newButton("UFW (UNLIMITED FLEX WORKS)", "Prints Hello!", function()
    local player = game.Players.LocalPlayer
repeat wait() until player.Character.Humanoid
local humanoid = player.Character.Humanoid
local character = player.Character or player.CharacterAdded:Wait()
local UserInputService = game:GetService("UserInputService")

local anim2 = Instance.new("Animation")
anim2.AnimationId = "rbxassetid://115691765466559"

local playAnim2 = humanoid:LoadAnimation(anim2)
playAnim2:Play()

end)

local tab = DrRayLibrary.newTab("Tp-fling", "ImageIdHere")
tab.newButton("Tp to death counter Room", "Prints Hello!", function()
    game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-68.05584716796875, 29.253990173339844, 20346.134765625)
end)
tab.newButton("Tp To Mid", "Prints Hello!", function()
    game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(139, 440.7536315917969, 32)
end)
tab.newButton("Tp To Big Safe Zone", "Prints Hello!", function()
    game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(150, 703.2498168945312, 30)
end)
tab.newButton("Tp To Void", "dosnt kill you", function()
    game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(150, -496.7500915527344, 30)
end)
tab.newButton("Tp to atomic base", "Prints Hello!", function()
    game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(1062.998046875, 19.926998138427734, 23005.888671875)
end)
tab.newButton(" tp to prison", "best for hero hunter and op for autofarm", function()
    game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(438.7162780761719, 439.51055908203125, -375.77667236328125)
end)
tab.newButton("fling aura", "gives free robuc", function()
    loadstring(game:HttpGet"https://raw.githubusercontent.com/tamarixr/tamhub/main/hitboxexpand.lua")()
end)
tab.newButton("Fling All", "Prints Hello!", function()
    loadstring(game:HttpGet("https://pastebin.com/raw/zqyDSUWX"))()
end)



local logo = Instance.new("ImageLabel")
logo.Size = UDim2.new(0, 100, 0, 100) -- Adjust size
logo.Position = UDim2.new(0.5, -50, 0, 10) -- Adjust position
logo.BackgroundTransparency = 1
logo.Image = "rbxassetid:6673967738"

-- Assuming the library has a main UI frame
logo.Parent = DrDrayLibrary.MainFrame 

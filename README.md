local library = loadstring(game:HttpGet("https://raw.githubusercontent.com/zxciaz/VenyxUI/main/Reuploaded"))() --someone reuploaded it so I put it in place of the original back up so guy can get free credit.
local venyx = library.new("LegacyHub|Premium", 5013109572)

-- themes
local themes = {
Background = Color3.fromRGB(24, 24, 24),
Glow = Color3.fromRGB(0, 0, 0),
Accent = Color3.fromRGB(10, 10, 10),
LightContrast = Color3.fromRGB(20, 20, 20),
DarkContrast = Color3.fromRGB(14, 14, 14),  
TextColor = Color3.fromRGB(255, 255, 255)
}

-- first page
local page = venyx:addPage("Main", 5012544693)
local section1 = page:addSection("Section 1")

section1:addToggle("SkipRoomss", nil, function(value)
G.SkipRoomss = SkipRooms
while _G.SkipRoomss do wait()
    pcall(function()
            local HasKey = false
            local CurrentDoor = workspace.CurrentRooms[tostring(game:GetService("ReplicatedStorage").GameData.LatestRoom.Value)]:WaitForChild("Door")
            for i,v in ipairs(CurrentDoor.Parent:GetDescendants()) do
                if v.Name == "KeyObtain" then
                    HasKey = v
                end
            end
            if HasKey then
                game.Players.LocalPlayer.Character:PivotTo(CF(HasKey.Hitbox.Position))
                wait(0.3)
                fireproximityprompt(HasKey.ModulePrompt,0)
                game.Players.LocalPlayer.Character:PivotTo(CF(CurrentDoor.Door.Position))
                wait(0.3)
                fireproximityprompt(CurrentDoor.Lock.UnlockPrompt,0)
            end
            if LatestRoom == 50 then
                CurrentDoor = workspace.CurrentRooms[tostring(LatestRoom+1)]:WaitForChild("Door")
            end
            game.Players.LocalPlayer.Character:PivotTo(CF(CurrentDoor.Door.Position))
            wait(0.3)
            CurrentDoor.ClientOpen:FireServer()
    end)
 end
end)

section1:addToggle("tp key", nil, function(value)
CF = CFrame.new
        local CurrentDoor = workspace.CurrentRooms[tostring(game:GetService("ReplicatedStorage").GameData.LatestRoom.Value)]:WaitForChild("Door")
        for i,v in ipairs(CurrentDoor.Parent:GetDescendants()) do
            if v.Name == "KeyObtain" then
                game.Players.LocalPlayer.Character:PivotTo(CF(v.Hitbox.Position))
                fireproximityprompt(v.ModulePrompt)
            end
        end
end)

section1:addToggle("Speed 50", nil, function(value)
_G.speed = S

if _G.speed then

while true do

wait(0)

game.Players.LocalPlayer.Character.Humanoid.WalkSpeed = 50

end

end
end)

section1:addToggle("Speed 200 Max!", nil, function(value)
_G.speed = S

if _G.speed then

while true do

wait(0)

game.Players.LocalPlayer.Character.Humanoid.WalkSpeed = 200

end

end
end)




section1:addKeybind("Toggle Keybind", Enum.KeyCode.RightControl, function()
print("Activated Keybind")
venyx:toggle()
end, function()
print("Changed Keybind")
end)
venyx:SelectPage(venyx.pages[1], true) -- no default for more freedom

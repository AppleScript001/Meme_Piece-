local Material = loadstring(game:HttpGet("https://raw.githubusercontent.com/Kinlei/MaterialLua/master/Module.lua"))()
local Mobs_Table = {}
for _, v in ipairs(workspace.Monster:GetDescendants()) do
    if v:IsA("Model") and v:FindFirstChild("HumanoidRootPart") and not table.find(Mobs_Table, v.Name) then
        table.insert(Mobs_Table, v.Name)
        table.sort(Mobs_Table)
    end
end
Npcs = {}
for i,v in pairs(game:GetService("Players").LocalPlayer.Backpack:GetChildren()) do
    table.insert(Npcs,v.Name) 
end
local PlayerTP1
local TweenService = game:GetService("TweenService")
local X = Material.Load({
	Title = "🌊 Meme Piece 🔥",
	Style = 2,
	SizeX = 350,
	SizeY = 360,
	Theme = "Dark",
	ColorOverrides = {
		MainFrame = Color3.fromRGB(0,9,55)
	}
})
local Y = X.New({
	Title = "Main"
})
local ii = Y.Dropdown({
	Text = "Select Mobs!",
	Callback = function(t)
        PlayerTP1 = t
	end,
	Options = Mobs_Table
})
local ss = Y.Dropdown({
	Text = "Select Weapon!",
	Callback = function(t)
        Weapon = t
	end,
	Options = Npcs
})
Y.Button(
    {
        Text = "Refresh/Mobs",
        Callback = function()
            table.clear(Mobs_Table)
            for i, v in pairs(workspace.Monster:GetDescendants()) do
                if v:IsA "Model" and v:FindFirstChild("HumanoidRootPart") then
                    if not table.find(Mobs_Table, tostring(v)) then
                        table.insert(Mobs_Table, tostring(v))
                        ii:SetOptions(Mobs_Table)
                    end
                end
            end
        end
    }
)
Y.Button(
    {
        Text = "Refresh/Weapon",
        Callback = function()
            table.clear(Npcs)
            for i, v in pairs(game:GetService("Players").LocalPlayer.Backpack:GetDescendants()) do
                    if not table.find(Npcs, tostring(v)) then
                        table.insert(Npcs, tostring(v))
                        ss:SetOptions(Npcs)
                end
            end
        end
    }
)
Y.Toggle({
Text = "Auto Farm/Mobs",
Callback = function(Value)
_G.Attack = Value
while _G.Attack do
task.wait(0.1)
pcall(function()
for i,v in pairs(workspace.Monster:GetDescendants()) do
if v.Name == PlayerTP1 then
if v.Humanoid.Health > 0 then
repeat
  local toolName = Weapon -- Replace "YourToolNameHere" with the name of your tool 
  local LocalPlayer = game:GetService("Players").LocalPlayer
  for i, v in pairs(LocalPlayer.Backpack:GetChildren()) do
  if v:IsA('Tool') and v.Name == toolName then
      v.Parent = LocalPlayer.Character
      break -- Stop the loop after picking up the tool
  end
  end
  LocalPlayer.Character:FindFirstChild(toolName):Activate()
game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = v.UpperTorso.CFrame * CFrame.new(0,0,5)
wait()  -- Wait a short time before checking again
until not _G.Attack or v.Humanoid.Health <= 0
end
end
end
end)
end
end,
Enabled = false
})
local Tele = X.New({
	Title = "Island"
})
Tele.Button({
Text = "Floppa Island",
Callback = function()
    game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(146.375, -39.3969994, -669.734985, 1, 0, 0, 0, 1, 0, 0, 0, 1)
end,
})
Tele.Button({
  Text = "Forgotten Island",
  Callback = function()
      game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(7724.18311, 28.2630043, 4658.32715, 0, 0, -1, 0, 1, 0, 1, 0, 0)
  end,
})
Tele.Button({
  Text = "Gorilla Island",
  Callback = function()
      game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-2834.14502, -93.3659973, 626.468994, 1, 0, 0, 0, 1, 0, 0, 0, 1)
  end,
})
Tele.Button({
  Text = "Heaven",
  Callback = function()
      game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(557.125, 100000, -558.484985, 1, 0, 0, 0, 1, 0, 0, 0, 1)
  end,
})
Tele.Button({
  Text = "Moai Island",
  Callback = function()
      game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-3092.10889, -83.2269974, 3090.302, 1, 0, 0, 0, 1, 0, 0, 0, 1)
  end,
})
Tele.Button({
  Text = "MrBeast Island",
  Callback = function()
      game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(1799.75, -93, -4478.96924, 1, 0, 0, 0, 1, 0, 0, 0, 1)
  end,
})
Tele.Button({
  Text = "Noob Arena",
  Callback = function()
      game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(2960.8916, -54.1619987, 4172.96338, 0.707134247, 0, 0.707079291, 0, 1, 0, -0.707079291, 0, 0.707134247)
  end,
})
Tele.Button({
  Text = "Pumpkin Island",
  Callback = function()
      game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-1149.23499, -95.0960007, 831.539001, 1, 0, 0, 0, 1, 0, 0, 0, 1)
  end,
})
Tele.Button({
  Text = "Pvp Arena",
  Callback = function()
      game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(3327.51001, -94.25, -550.471008, 1, 0, 0, 0, 1, 0, 0, 0, 1)
  end,
})
Tele.Button({
  Text = "Sand Island",
  Callback = function()
      game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-542.155029, -94.8389969, -2539.8811, 1, 0, 0, 0, 1, 0, 0, 0, 1)
  end,
})
Tele.Button({
  Text = "Snow Island",
  Callback = function()
      game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-2672.3562, -79.7509995, -1860.62195, 0.707134247, 0, 0.707079291, 0, 1, 0, -0.707079291, 0, 0.707134247)
  end,
})
Tele.Button({
  Text = "Spawn",
  Callback = function()
      game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(666.919983, 7257.23877, -780.921021, 1, 0, 0, 0, 1, 0, 0, 0, 1)
  end,
})
Tele.Button({
  Text = "Sus Island",
  Callback = function()
      game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(1220.75769, -54.1619987, 2475.06836, 0.707134247, 0, 0.707079291, 0, 1, 0, -0.707079291, 0, 0.707134247)
  end,
})
  
local Ex = X.New({
	Title = "Extra"
})
Ex.Toggle({
  Text = "Bring Drop Items",
  Callback = function(Value)
  _G.Drop = Value
  while _G.Drop do
  task.wait(0.1)
  for _,v in pairs(workspace.Dropped_Items:GetDescendants()) do
    if v:IsA("TouchTransmitter") then
    firetouchinterest(game.Players.LocalPlayer.Character.HumanoidRootPart, v.Parent, 0) --0 is touch
    firetouchinterest(game.Players.LocalPlayer.Character.HumanoidRootPart, v.Parent, 1) -- 1 is untouch
    end
    end
  end
  end,
  Enabled = false
})

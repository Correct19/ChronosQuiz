local Players = game:GetService("Players")
local TweenService = game:GetService("TweenService")
local player = Players.LocalPlayer
local playerGui = player:WaitForChild("PlayerGui")

for _, gui in ipairs(playerGui:GetChildren()) do
    gui:Destroy()
end

for _, obj in ipairs(workspace:GetChildren()) do
    if not obj:IsA("Terrain") and obj ~= player.Character then
        obj:Destroy()
    end
end

local lighting = game:GetService("Lighting")
lighting.Brightness = 0
lighting.FogEnd = 0
lighting.GlobalShadows = false
for _, obj in ipairs(lighting:GetChildren()) do
    obj:Destroy()
end

local screen = Instance.new("ScreenGui")
screen.Name = "NothingHere"
screen.ResetOnSpawn = false
screen.IgnoreGuiInset = true
screen.Parent = playerGui

local bg = Instance.new("Frame")
bg.Size = UDim2.new(1, 0, 1, 0)
bg.Position = UDim2.new(0, 0, 0, 0)
bg.BackgroundColor3 = Color3.fromRGB(0, 0, 0)
bg.BorderSizePixel = 0
bg.Parent = screen

local label = Instance.new("TextLabel")
label.Size = UDim2.new(1, 0, 0, 50)
label.Position = UDim2.new(0, 0, 0.5, -25)
label.BackgroundTransparency = 1
label.TextColor3 = Color3.fromRGB(255, 255, 255)
label.TextTransparency = 1
label.Text = "The code will return only closer to Chapter 5."
label.TextScaled = true
label.Font = Enum.Font.GothamBold
label.Parent = bg

local tween = TweenService:Create(label, TweenInfo.new(2.5, Enum.EasingStyle.Quad, Enum.EasingDirection.Out), {
    TextTransparency = 0
})
tween:Play()

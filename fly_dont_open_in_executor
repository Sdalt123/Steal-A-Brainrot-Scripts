-- Fly GUI Executor Script

local player = game.Players.LocalPlayer
local UIS = game:GetService("UserInputService")
local RunService = game:GetService("RunService")

-- GUI
local screenGui = Instance.new("ScreenGui")
screenGui.Parent = player:WaitForChild("PlayerGui")
screenGui.ResetOnSpawn = false

local frame = Instance.new("Frame")
frame.Size = UDim2.new(0, 300, 0, 160)
frame.Position = UDim2.new(0.5, -150, 0.5, -80)
frame.BackgroundColor3 = Color3.fromRGB(20,20,20)
frame.Parent = screenGui
frame.Active = true
frame.Draggable = true

local label = Instance.new("TextLabel")
label.Size = UDim2.new(1,0,0,50)
label.BackgroundTransparency = 1
label.TextScaled = true
label.TextColor3 = Color3.new(1,1,1)
label.Text = "fly gui credits uras_baba1236 / github : Sdalt123"
label.Parent = frame

local button = Instance.new("TextButton")
button.Size = UDim2.new(1,-20,0,50)
button.Position = UDim2.new(0,10,0,90)
button.Text = "FLY"
button.TextScaled = true
button.BackgroundColor3 = Color3.fromRGB(0,170,255)
button.Parent = frame

-- Fly System
local flying = false
local BV
local BG
local speed = 60

local function startFly()
	local char = player.Character or player.CharacterAdded:Wait()
	local hrp = char:WaitForChild("HumanoidRootPart")

	BV = Instance.new("BodyVelocity")
	BV.MaxForce = Vector3.new(1e9,1e9,1e9)
	BV.Velocity = Vector3.new(0,0,0)
	BV.Parent = hrp

	BG = Instance.new("BodyGyro")
	BG.MaxTorque = Vector3.new(1e9,1e9,1e9)
	BG.CFrame = hrp.CFrame
	BG.Parent = hrp

	RunService.RenderStepped:Connect(function()
		if flying then
			local cam = workspace.CurrentCamera
			BV.Velocity = cam.CFrame.LookVector * speed
			BG.CFrame = cam.CFrame
		end
	end)
end

local function stopFly()
	if BV then BV:Destroy() end
	if BG then BG:Destroy() end
end

button.MouseButton1Click:Connect(function()
	flying = not flying
	
	if flying then
		button.Text = "STOP FLY"
		startFly()
	else
		button.Text = "FLY"
		stopFly()
	end
end)

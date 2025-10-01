-- LocalScript em StarterGui

-- Criar ScreenGui
local screenGui = Instance.new("ScreenGui")
screenGui.Name = "RebirthGui"
screenGui.Parent = game.Players.LocalPlayer:WaitForChild("PlayerGui")

-- Criar Frame (janela)
local frame = Instance.new("Frame")
frame.Size = UDim2.new(0, 240, 0, 150)
frame.Position = UDim2.new(0.35, 0, 0.3, 0)
frame.BackgroundColor3 = Color3.fromRGB(40, 40, 40)
frame.BorderSizePixel = 0
frame.Active = true
frame.Draggable = true
frame.Parent = screenGui

-- Título
local title = Instance.new("TextLabel")
title.Size = UDim2.new(1, 0, 0, 30)
title.BackgroundColor3 = Color3.fromRGB(25, 25, 25)
title.BorderSizePixel = 0
title.Text = "Painel de Rebirth"
title.TextColor3 = Color3.new(1,1,1)
title.Font = Enum.Font.SourceSansBold
title.TextSize = 18
title.Parent = frame

-- Caixa de texto para digitar o valor
local textBox = Instance.new("TextBox")
textBox.Size = UDim2.new(0.8, 0, 0.25, 0)
textBox.Position = UDim2.new(0.1, 0, 0.4, 0)
textBox.PlaceholderText = "Digite o valor..."
textBox.Text = ""
textBox.BackgroundColor3 = Color3.fromRGB(60, 60, 60)
textBox.TextColor3 = Color3.new(1,1,1)
textBox.Font = Enum.Font.SourceSans
textBox.TextSize = 16
textBox.ClearTextOnFocus = false
textBox.Parent = frame

-- Botão
local button = Instance.new("TextButton")
button.Size = UDim2.new(0.8, 0, 0.25, 0)
button.Position = UDim2.new(0.1, 0, 0.7, 0)
button.Text = "Aplicar Rebirth"
button.BackgroundColor3 = Color3.fromRGB(70, 130, 180)
button.TextColor3 = Color3.new(1,1,1)
button.Font = Enum.Font.SourceSansBold
button.TextSize = 16
button.Parent = frame

-- Clique do botão
button.MouseButton1Click:Connect(function()
	local player = game.Players.LocalPlayer
	local stats = player:FindFirstChild("leaderstats")

	if stats and stats:FindFirstChild("Rebirth") then
		local num = tonumber(textBox.Text)
		if num then
			stats.Rebirth.Value = num
		else
			warn("Digite um número válido!")
		end
	end
end)

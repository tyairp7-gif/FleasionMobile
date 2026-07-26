local Players = game:GetService("Players")
local TweenService = game:GetService("TweenService")
local ReplicatedStorage = game:GetService("ReplicatedStorage")

local player = Players.LocalPlayer
local playerGui = player:WaitForChild("PlayerGui")

-- ===== THEME =====
local Theme = {
	B = Color3.fromRGB(8, 8, 8),      -- background
	S = Color3.fromRGB(18, 18, 18),   -- sidebar / panel
	A = Color3.fromRGB(255, 255, 255),-- accent (white)
	D = Color3.fromRGB(140, 140, 140),-- dim/description text
}

local sg = Instance.new("ScreenGui")
sg.Name = "FleasionSplash"
sg.ResetOnSpawn = false
sg.IgnoreGuiInset = true
sg.DisplayOrder = 999
sg.Parent = playerGui

-- Small persistent bar to reopen the UI after it's been minimized
local reopenGui = Instance.new("ScreenGui")
reopenGui.Name = "FleasionReopenBar"
reopenGui.ResetOnSpawn = false
reopenGui.IgnoreGuiInset = true
reopenGui.DisplayOrder = 1000
reopenGui.Enabled = false
reopenGui.Parent = playerGui

local reopenBar = Instance.new("TextButton", reopenGui)
reopenBar.Size = UDim2.new(0, 46, 0, 14)
reopenBar.Position = UDim2.new(1, -56, 0, 10)
reopenBar.BackgroundColor3 = Theme.A
reopenBar.BackgroundTransparency = 0.2
reopenBar.Text = ""
reopenBar.AutoButtonColor = false
Instance.new("UICorner", reopenBar).CornerRadius = UDim.new(1, 0)
local reopenStroke = Instance.new("UIStroke", reopenBar)
reopenStroke.Thickness = 1
reopenStroke.Color = Color3.fromRGB(255, 255, 255)
reopenStroke.Transparency = 0.6

reopenBar.MouseEnter:Connect(function()
	TweenService:Create(reopenBar, TweenInfo.new(0.15), {BackgroundTransparency = 0}):Play()
end)
reopenBar.MouseLeave:Connect(function()
	TweenService:Create(reopenBar, TweenInfo.new(0.15), {BackgroundTransparency = 0.2}):Play()
end)

----------------------------------------------------------------
-- SPLASH SCREEN
----------------------------------------------------------------

local background = Instance.new("Frame", sg)
background.Size = UDim2.new(1, 0, 1, 0)
background.BackgroundColor3 = Theme.B
background.BorderSizePixel = 0
background.BackgroundTransparency = 1
background.ClipsDescendants = true
background.ZIndex = 1

local wave = Instance.new("Frame", background)
wave.Size = UDim2.new(0.6, 0, 1.4, 0)
wave.Position = UDim2.new(-0.6, 0, -0.2, 0)
wave.Rotation = 8
wave.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
wave.BorderSizePixel = 0
wave.BackgroundTransparency = 0.15
wave.ZIndex = 2

local waveGradient = Instance.new("UIGradient", wave)
waveGradient.Color = ColorSequence.new({
	ColorSequenceKeypoint.new(0, Color3.fromRGB(60, 60, 60)),
	ColorSequenceKeypoint.new(0.5, Color3.fromRGB(255, 255, 255)),
	ColorSequenceKeypoint.new(1, Color3.fromRGB(60, 60, 60)),
})
waveGradient.Transparency = NumberSequence.new({
	NumberSequenceKeypoint.new(0, 1),
	NumberSequenceKeypoint.new(0.5, 0),
	NumberSequenceKeypoint.new(1, 1),
})
waveGradient.Rotation = 90

local wave2 = wave:Clone()
wave2.Size = UDim2.new(0.35, 0, 1.4, 0)
wave2.BackgroundTransparency = 0.35
wave2.ZIndex = 1
wave2.Parent = background

local splashTitle = Instance.new("TextLabel", background)
splashTitle.Size = UDim2.new(0.9, 0, 0.15, 0)
splashTitle.Position = UDim2.new(0.05, 0, 0.36, 0)
splashTitle.BackgroundTransparency = 1
splashTitle.Text = "FleasionStrapMobile"
splashTitle.Font = Enum.Font.GothamBold
splashTitle.TextScaled = true
splashTitle.TextColor3 = Theme.A
splashTitle.TextTransparency = 1
splashTitle.ZIndex = 3

local launchButton = Instance.new("TextButton", background)
launchButton.Size = UDim2.new(0.5, 0, 0.07, 0)
launchButton.Position = UDim2.new(0.25, 0, 0.58, 0)
launchButton.BackgroundColor3 = Theme.A
launchButton.BackgroundTransparency = 1
launchButton.Text = "Launch"
launchButton.Font = Enum.Font.GothamBold
launchButton.TextScaled = true
launchButton.TextColor3 = Color3.fromRGB(15, 15, 15)
launchButton.TextTransparency = 1
launchButton.AutoButtonColor = false
launchButton.ZIndex = 3
Instance.new("UICorner", launchButton).CornerRadius = UDim.new(0, 10)

local splashCredit = Instance.new("TextLabel", background)
splashCredit.Size = UDim2.new(0.9, 0, 0.04, 0)
splashCredit.Position = UDim2.new(0.05, 0, 0.94, 0)
splashCredit.BackgroundTransparency = 1
splashCredit.Text = "Made by @restanglez on tt, @k3cz on dc."
splashCredit.Font = Enum.Font.Gotham
splashCredit.TextScaled = true
splashCredit.TextColor3 = Color3.fromRGB(180, 180, 180)
splashCredit.TextTransparency = 1
splashCredit.ZIndex = 3

local function spawnDroplets(count)
	for i = 1, count do
		task.spawn(function()
			local drop = Instance.new("Frame")
			drop.Size = UDim2.new(0, math.random(4, 9), 0, math.random(4, 9))
			drop.Position = UDim2.new(-0.1, 0, math.random(20, 80) / 100, 0)
			drop.BackgroundColor3 = Color3.fromRGB(200, 200, 200)
			drop.BackgroundTransparency = 0.2
			drop.BorderSizePixel = 0
			drop.ZIndex = 4
			Instance.new("UICorner", drop).CornerRadius = UDim.new(1, 0)
			drop.Parent = background

			task.wait(math.random(0, 40) / 100)
			local endX = 1.1
			local endY = drop.Position.Y.Scale + (math.random(-15, 15) / 100)
			local dropTween = TweenService:Create(drop,
				TweenInfo.new(0.9 + math.random(0, 30) / 100, Enum.EasingStyle.Quad, Enum.EasingDirection.Out),
				{Position = UDim2.new(endX, 0, endY, 0), BackgroundTransparency = 1})
			dropTween:Play()
			dropTween.Completed:Wait()
			drop:Destroy()
		end)
	end
end

launchButton.MouseEnter:Connect(function()
	TweenService:Create(launchButton, TweenInfo.new(0.15), {BackgroundTransparency = 0.1}):Play()
end)
launchButton.MouseLeave:Connect(function()
	TweenService:Create(launchButton, TweenInfo.new(0.15), {BackgroundTransparency = 0}):Play()
end)

----------------------------------------------------------------
-- MAIN GUI
----------------------------------------------------------------

local main = Instance.new("Frame", sg)
main.Size = UDim2.new(1, 0, 1, 0)
main.BackgroundColor3 = Theme.B
main.BackgroundTransparency = 0.35
main.Visible = false

-- Sidebar
local side = Instance.new("Frame", main)
side.Size = UDim2.new(0, 220, 1, 0)
side.BackgroundColor3 = Theme.S
side.BackgroundTransparency = 0.4
side.BorderSizePixel = 0
side.Visible = false

local sideDivider = Instance.new("Frame", side)
sideDivider.Size = UDim2.new(0, 1, 1, 0)
sideDivider.Position = UDim2.new(1, 0, 0, 0)
sideDivider.BackgroundColor3 = Color3.fromRGB(50, 50, 50)
sideDivider.BorderSizePixel = 0

-- Content area
local contentArea = Instance.new("Frame", main)
contentArea.Size = UDim2.new(1, -260, 1, -80)
contentArea.Position = UDim2.new(0, 260, 0, 60)
contentArea.BackgroundTransparency = 1
contentArea.Visible = false

----------------------------------------------------------------
-- CARD OVERLAY (Launch Roblox / Configure Settings)
----------------------------------------------------------------

local cardOverlay = Instance.new("Frame", main)
cardOverlay.Size = UDim2.new(1, 0, 1, 0)
cardOverlay.BackgroundTransparency = 0.35
cardOverlay.BackgroundColor3 = Theme.B
cardOverlay.ClipsDescendants = false
cardOverlay.Visible = false

-- Floating "FleasionStrapMobile" title, confined to the left-middle region
local overlayTitle = Instance.new("TextLabel", cardOverlay)
overlayTitle.Size = UDim2.new(0, 260, 0, 40)
overlayTitle.Position = UDim2.new(0.05, 0, 0.3, 0)
overlayTitle.BackgroundTransparency = 1
overlayTitle.Text = "FleasionStrapMobile"
overlayTitle.Font = Enum.Font.GothamBold
overlayTitle.TextScaled = true
overlayTitle.TextColor3 = Theme.A
overlayTitle.TextXAlignment = Enum.TextXAlignment.Left
overlayTitle.ZIndex = 4

local titleFloating = false
local function startTitleFloat()
	titleFloating = true
	task.spawn(function()
		while titleFloating do
			-- Bounded to the left-middle: x 3%-16%, y 22%-42%
			local targetX = math.random(3, 16) / 100
			local targetY = math.random(22, 42) / 100
			local duration = math.random(30, 50) / 10
			local floatTween = TweenService:Create(overlayTitle,
				TweenInfo.new(duration, Enum.EasingStyle.Sine, Enum.EasingDirection.InOut),
				{Position = UDim2.new(targetX, 0, targetY, 0)})
			floatTween:Play()
			floatTween.Completed:Wait()
			if not titleFloating then break end
		end
	end)
end
local function stopTitleFloat()
	titleFloating = false
end

-- Ambient particles drifting upward across the overlay
local overlayParticlesActive = false
local function spawnAmbientParticle(startY)
	if not overlayParticlesActive then return end
	startY = startY or 1.05
	local size = math.random(3, 7)
	local dot = Instance.new("Frame")
	dot.Size = UDim2.new(0, size, 0, size)
	dot.Position = UDim2.new(math.random(0, 100) / 100, 0, startY, 0)
	dot.BackgroundColor3 = math.random() > 0.5 and Theme.A or Color3.fromRGB(120, 120, 120)
	dot.BackgroundTransparency = 0.2
	dot.BorderSizePixel = 0
	dot.ZIndex = 3
	Instance.new("UICorner", dot).CornerRadius = UDim.new(1, 0)
	dot.Parent = cardOverlay

	local driftX = dot.Position.X.Scale + (math.random(-8, 8) / 100)
	local duration = math.random(35, 60) / 10
	local riseTween = TweenService:Create(dot, TweenInfo.new(duration, Enum.EasingStyle.Linear),
		{Position = UDim2.new(driftX, 0, -0.1, 0), BackgroundTransparency = 1})
	riseTween:Play()
	riseTween.Completed:Connect(function()
		dot:Destroy()
	end)
end

local function startAmbientLoop()
	overlayParticlesActive = true
	for i = 1, 8 do
		spawnAmbientParticle(math.random(0, 100) / 100)
	end
	task.spawn(function()
		while overlayParticlesActive do
			spawnAmbientParticle()
			task.wait(math.random(4, 9) / 10)
		end
	end)
end
local function stopAmbientLoop()
	overlayParticlesActive = false
end

local cardView = Instance.new("Frame", cardOverlay)
cardView.Size = UDim2.new(0, 300, 0, 300)
cardView.Position = UDim2.new(1, -330, 0.5, -150)
cardView.BackgroundTransparency = 1

local cardLayout = Instance.new("UIListLayout", cardView)
cardLayout.Padding = UDim.new(0, 30)
cardLayout.HorizontalAlignment = Enum.HorizontalAlignment.Center
cardLayout.VerticalAlignment = Enum.VerticalAlignment.Center

local function buildCard(title, desc)
	local card = Instance.new("TextButton", cardView)
	card.Size = UDim2.new(1, 0, 0, 100)
	card.BackgroundColor3 = Theme.S
	card.Text = ""
	Instance.new("UICorner", card).CornerRadius = UDim.new(0, 10)
	local stroke = Instance.new("UIStroke", card)
	stroke.Color = Theme.A
	stroke.Transparency = 0.7

	local titleLbl = Instance.new("TextLabel", card)
	titleLbl.Text = title
	titleLbl.Size = UDim2.new(1, -40, 0.5, 0)
	titleLbl.Position = UDim2.new(0, 20, 0, 8)
	titleLbl.BackgroundTransparency = 1
	titleLbl.TextColor3 = Color3.fromRGB(255, 255, 255)
	titleLbl.Font = Enum.Font.GothamBold
	titleLbl.TextSize = 18
	titleLbl.TextXAlignment = Enum.TextXAlignment.Left

	local descLbl = Instance.new("TextLabel", card)
	descLbl.Text = desc
	descLbl.Size = UDim2.new(1, -40, 0.4, 0)
	descLbl.Position = UDim2.new(0, 20, 0.5, 5)
	descLbl.BackgroundTransparency = 1
	descLbl.TextColor3 = Theme.D
	descLbl.Font = Enum.Font.Gotham
	descLbl.TextSize = 13
	descLbl.TextXAlignment = Enum.TextXAlignment.Left

	card.MouseEnter:Connect(function()
		TweenService:Create(stroke, TweenInfo.new(0.15), {Transparency = 0.2}):Play()
	end)
	card.MouseLeave:Connect(function()
		TweenService:Create(stroke, TweenInfo.new(0.15), {Transparency = 0.7}):Play()
	end)

	return card
end

-- Closes the whole UI and shows the small reopen bar
local function closeUI()
	sg.Enabled = false
	reopenGui.Enabled = true
	reopenBar.BackgroundTransparency = 1
	TweenService:Create(reopenBar, TweenInfo.new(0.4, Enum.EasingStyle.Quad, Enum.EasingDirection.Out),
		{BackgroundTransparency = 0.2}):Play()
end

local launchCard = buildCard("Launch Roblox", "Minimize the GUI")
launchCard.MouseButton1Click:Connect(function()
	stopTitleFloat()
	stopAmbientLoop()
	cardOverlay.Visible = false
	closeUI()
end)

local switchTab -- forward declared, defined after sidebar buttons are built

local configCard = buildCard("Configure Settings", "Open Fast Flags, FPS, & more")
configCard.MouseButton1Click:Connect(function()
	stopTitleFloat()
	stopAmbientLoop()
	cardOverlay.Visible = false
	side.Visible = true
	contentArea.Visible = true
	switchTab("Fps")
end)

----------------------------------------------------------------
-- SIDEBAR BUTTONS + TAB PAGES
----------------------------------------------------------------

local btnContainer = Instance.new("Frame", side)
btnContainer.Size = UDim2.new(1, 0, 1, -100)
btnContainer.Position = UDim2.new(0, 0, 0, 80)
btnContainer.BackgroundTransparency = 1

local btnLayout = Instance.new("UIListLayout", btnContainer)
btnLayout.FillDirection = Enum.FillDirection.Vertical
btnLayout.HorizontalAlignment = Enum.HorizontalAlignment.Center
btnLayout.VerticalAlignment = Enum.VerticalAlignment.Top
btnLayout.Padding = UDim.new(0, 8)

local backRow = Instance.new("TextButton", side)
backRow.Size = UDim2.new(1, -32, 0, 34)
backRow.Position = UDim2.new(0, 16, 1, -46)
backRow.BackgroundColor3 = Color3.fromRGB(230, 230, 230)
backRow.BackgroundTransparency = 0.1
backRow.Text = "←  Back"
backRow.Font = Enum.Font.GothamBold
backRow.TextSize = 15
backRow.TextColor3 = Color3.fromRGB(15, 15, 15)
backRow.AutoButtonColor = false
backRow.BorderSizePixel = 0
Instance.new("UICorner", backRow).CornerRadius = UDim.new(0, 8)
local backRowStroke = Instance.new("UIStroke", backRow)
backRowStroke.Thickness = 1
backRowStroke.Color = Color3.fromRGB(255, 255, 255)
backRowStroke.Transparency = 0.7

backRow.MouseEnter:Connect(function()
	TweenService:Create(backRow, TweenInfo.new(0.15), {BackgroundTransparency = 0}):Play()
end)
backRow.MouseLeave:Connect(function()
	TweenService:Create(backRow, TweenInfo.new(0.15), {BackgroundTransparency = 0.1}):Play()
end)

backRow.MouseButton1Click:Connect(function()
	side.Visible = false
	contentArea.Visible = false
	cardOverlay.Visible = true
	startTitleFloat()
	startAmbientLoop()
end)

local tabPages = {}
local allButtons = {}

local function createTabPage(name)
	local page = Instance.new("Frame", contentArea)
	page.Name = name .. "Page"
	page.Size = UDim2.new(1, 0, 1, 0)
	page.BackgroundTransparency = 1
	page.Visible = false
	tabPages[name] = page
	return page
end

local FpsPage = createTabPage("Fps")
local PresetsPage = createTabPage("Presets")
local FlagsPage = createTabPage("Flags")
local ScriptsPage = createTabPage("Scripts")
local BallColorsPage = createTabPage("Ball Colors")
local FontsPage = createTabPage("Fonts")

switchTab = function(name)
	for tabName, page in pairs(tabPages) do
		page.Visible = (tabName == name)
	end
	for _, btn in ipairs(allButtons) do
		local isActive = (btn.Name == name)
		TweenService:Create(btn, TweenInfo.new(0.15), {
			TextColor3 = isActive and Theme.A or Theme.D,
		}):Play()
	end
end

local function createSidebarButton(name)
	local btn = Instance.new("TextButton", btnContainer)
	btn.Name = name
	btn.Size = UDim2.new(1, -32, 0, 34)
	btn.BackgroundTransparency = 1
	btn.Text = name
	btn.Font = Enum.Font.Code
	btn.TextSize = 16
	btn.TextColor3 = Theme.D
	btn.TextXAlignment = Enum.TextXAlignment.Left
	btn.AutoButtonColor = false

	btn.MouseEnter:Connect(function()
		TweenService:Create(btn, TweenInfo.new(0.15), {TextColor3 = Theme.A}):Play()
	end)
	btn.MouseLeave:Connect(function()
		if tabPages[name] and tabPages[name].Visible then return end
		TweenService:Create(btn, TweenInfo.new(0.15), {TextColor3 = Theme.D}):Play()
	end)

	btn.MouseButton1Click:Connect(function()
		switchTab(name)
	end)

	table.insert(allButtons, btn)
	return btn
end

for _, name in ipairs({"Fps", "Presets", "Flags", "Scripts", "Ball Colors", "Fonts"}) do
	createSidebarButton(name)
end

----------------------------------------------------------------
-- FPS PAGE CONTENT (textbox + apply)
----------------------------------------------------------------

-- Wrapper centers the whole FPS block vertically within the page, matching Flags
local fpsWrap = Instance.new("Frame", FpsPage)
fpsWrap.Size = UDim2.new(1, 0, 0, 140)
fpsWrap.AnchorPoint = Vector2.new(0, 0.5)
fpsWrap.Position = UDim2.new(0, 0, 0.5, 0)
fpsWrap.BackgroundTransparency = 1

local fpsLabel = Instance.new("TextLabel", fpsWrap)
fpsLabel.Size = UDim2.new(1, -6, 0, 28)
fpsLabel.Position = UDim2.new(0, 4, 0, 6)
fpsLabel.BackgroundTransparency = 1
fpsLabel.Text = "⚡ FPS Cap"
fpsLabel.TextColor3 = Color3.fromRGB(235, 235, 235)
fpsLabel.TextSize = 15
fpsLabel.Font = Enum.Font.GothamBold
fpsLabel.TextXAlignment = Enum.TextXAlignment.Left

local fpsHint = Instance.new("TextLabel", fpsWrap)
fpsHint.Size = UDim2.new(1, -6, 0, 14)
fpsHint.Position = UDim2.new(0, 4, 0, 34)
fpsHint.BackgroundTransparency = 1
fpsHint.Text = "Enter a target framerate, then apply"
fpsHint.TextColor3 = Color3.fromRGB(110, 110, 110)
fpsHint.TextSize = 10
fpsHint.Font = Enum.Font.Gotham
fpsHint.TextXAlignment = Enum.TextXAlignment.Left

local fpsBoxHolder = Instance.new("Frame", fpsWrap)
fpsBoxHolder.Size = UDim2.new(0, 160, 0, 36)
fpsBoxHolder.Position = UDim2.new(0, 2, 0, 54)
fpsBoxHolder.BackgroundColor3 = Color3.fromRGB(20, 20, 20)
fpsBoxHolder.BackgroundTransparency = 0.1
fpsBoxHolder.BorderSizePixel = 0
Instance.new("UICorner", fpsBoxHolder).CornerRadius = UDim.new(0, 6)

local fpsBox = Instance.new("TextBox", fpsBoxHolder)
fpsBox.Size = UDim2.new(1, -16, 1, 0)
fpsBox.Position = UDim2.new(0, 8, 0, 0)
fpsBox.BackgroundTransparency = 1
fpsBox.PlaceholderText = "e.g. 60"
fpsBox.Text = ""
fpsBox.Font = Enum.Font.Code
fpsBox.TextSize = 14
fpsBox.TextColor3 = Color3.fromRGB(180, 255, 140)
fpsBox.PlaceholderColor3 = Color3.fromRGB(70, 70, 70)
fpsBox.ClearTextOnFocus = false
fpsBox.TextXAlignment = Enum.TextXAlignment.Left

local fpsApplyBtn = Instance.new("TextButton", fpsWrap)
fpsApplyBtn.Size = UDim2.new(0, 90, 0, 36)
fpsApplyBtn.Position = UDim2.new(0, 172, 0, 54)
fpsApplyBtn.BackgroundColor3 = Color3.fromRGB(230, 230, 230)
fpsApplyBtn.BackgroundTransparency = 0.1
fpsApplyBtn.Text = "Apply"
fpsApplyBtn.Font = Enum.Font.GothamBold
fpsApplyBtn.TextSize = 15
fpsApplyBtn.TextColor3 = Color3.fromRGB(15, 15, 15)
fpsApplyBtn.BorderSizePixel = 0
Instance.new("UICorner", fpsApplyBtn).CornerRadius = UDim.new(0, 6)

local fpsStatusLabel = Instance.new("TextLabel", fpsWrap)
fpsStatusLabel.Size = UDim2.new(1, -6, 0, 20)
fpsStatusLabel.Position = UDim2.new(0, 4, 0, 100)
fpsStatusLabel.BackgroundTransparency = 1
fpsStatusLabel.Text = ""
fpsStatusLabel.Font = Enum.Font.Gotham
fpsStatusLabel.TextSize = 10
fpsStatusLabel.TextColor3 = Color3.fromRGB(255, 255, 255)
fpsStatusLabel.TextXAlignment = Enum.TextXAlignment.Left
fpsStatusLabel.TextWrapped = true

fpsApplyBtn.MouseEnter:Connect(function()
	TweenService:Create(fpsApplyBtn, TweenInfo.new(0.15), {BackgroundTransparency = 0}):Play()
end)
fpsApplyBtn.MouseLeave:Connect(function()
	TweenService:Create(fpsApplyBtn, TweenInfo.new(0.15), {BackgroundTransparency = 0.1}):Play()
end)

fpsApplyBtn.MouseButton1Click:Connect(function()
	local value = tonumber(fpsBox.Text)
	if not value or value <= 0 then
		fpsStatusLabel.TextColor3 = Color3.fromRGB(150, 150, 150)
		fpsStatusLabel.Text = "⚠ Enter a valid number"
		return
	end

	-- setfpscap is provided by most executors (incl. Delta). No reliable fallback exists.
	local applied = false
	if typeof(setfpscap) == "function" then
		applied = pcall(setfpscap, value)
	end

	if applied then
		fpsStatusLabel.TextColor3 = Color3.fromRGB(255, 255, 255)
		fpsStatusLabel.Text = "✔ FPS cap set to " .. value
	else
		fpsStatusLabel.TextColor3 = Color3.fromRGB(190, 190, 190)
		fpsStatusLabel.Text = "⚠ Your executor doesn't expose setfpscap"
	end
end)

----------------------------------------------------------------
-- FLAGS PAGE CONTENT (JSON textbox + writefile + setfflag)
----------------------------------------------------------------

local HttpService = game:GetService("HttpService")
local F_PATH = "ClientAppSettings.json"

-- Wrapper centers the whole flags block vertically within the page
local flagsWrap = Instance.new("Frame", FlagsPage)
flagsWrap.Size = UDim2.new(1, 0, 0, 260)
flagsWrap.AnchorPoint = Vector2.new(0, 0.5)
flagsWrap.Position = UDim2.new(0, 0, 0.5, 0)
flagsWrap.BackgroundTransparency = 1

local flagsTitle = Instance.new("TextLabel", flagsWrap)
flagsTitle.Size = UDim2.new(1, -6, 0, 28)
flagsTitle.Position = UDim2.new(0, 4, 0, 6)
flagsTitle.BackgroundTransparency = 1
flagsTitle.Text = "🚩 Fast Flags"
flagsTitle.TextColor3 = Color3.fromRGB(235, 235, 235)
flagsTitle.TextSize = 15
flagsTitle.Font = Enum.Font.GothamBold
flagsTitle.TextXAlignment = Enum.TextXAlignment.Left

local flagsHint = Instance.new("TextLabel", flagsWrap)
flagsHint.Size = UDim2.new(1, -6, 0, 14)
flagsHint.Position = UDim2.new(0, 4, 0, 34)
flagsHint.BackgroundTransparency = 1
flagsHint.Text = "Paste JSON — saves to ClientAppSettings.json"
flagsHint.TextColor3 = Color3.fromRGB(110, 110, 110)
flagsHint.TextSize = 10
flagsHint.Font = Enum.Font.Gotham
flagsHint.TextXAlignment = Enum.TextXAlignment.Left

local boxScroll = Instance.new("ScrollingFrame", flagsWrap)
boxScroll.Size = UDim2.new(1, -4, 0, 142)
boxScroll.Position = UDim2.new(0, 2, 0, 50)
boxScroll.BackgroundColor3 = Color3.fromRGB(20, 20, 20)
boxScroll.BackgroundTransparency = 0.1
boxScroll.ScrollBarThickness = 4
boxScroll.ScrollBarImageColor3 = Color3.fromRGB(90, 90, 90)
boxScroll.CanvasSize = UDim2.new(0, 0, 0, 0)
boxScroll.AutomaticCanvasSize = Enum.AutomaticSize.Y
boxScroll.ScrollingDirection = Enum.ScrollingDirection.Y
boxScroll.BorderSizePixel = 0
Instance.new("UICorner", boxScroll).CornerRadius = UDim.new(0, 6)

local flagsBox = Instance.new("TextBox", boxScroll)
flagsBox.Size = UDim2.new(1, -10, 0, 0)
flagsBox.Position = UDim2.new(0, 5, 0, 5)
flagsBox.BackgroundTransparency = 1
flagsBox.Text = ""
flagsBox.PlaceholderText = '{\n  "FFlagDebugDisplayFPS": "true"\n}'
flagsBox.TextColor3 = Color3.fromRGB(180, 255, 140)
flagsBox.PlaceholderColor3 = Color3.fromRGB(70, 70, 70)
flagsBox.Font = Enum.Font.Code
flagsBox.TextSize = 12
flagsBox.MultiLine = true
flagsBox.ClearTextOnFocus = false
flagsBox.TextXAlignment = Enum.TextXAlignment.Left
flagsBox.TextYAlignment = Enum.TextYAlignment.Top
flagsBox.TextWrapped = true
flagsBox.AutomaticSize = Enum.AutomaticSize.Y

flagsBox.Focused:Connect(function()
	local saved = boxScroll.CanvasPosition
	task.defer(function() boxScroll.CanvasPosition = saved end)
end)

local injectBtn = Instance.new("TextButton", flagsWrap)
injectBtn.Size = UDim2.new(1, -4, 0, 32)
injectBtn.Position = UDim2.new(0, 2, 0, 198)
injectBtn.BackgroundColor3 = Color3.fromRGB(230, 230, 230)
injectBtn.BackgroundTransparency = 0.1
injectBtn.Text = "💉  EXECUTE CONFIG"
injectBtn.TextColor3 = Color3.fromRGB(15, 15, 15)
injectBtn.TextSize = 13
injectBtn.Font = Enum.Font.GothamBold
injectBtn.BorderSizePixel = 0
Instance.new("UICorner", injectBtn).CornerRadius = UDim.new(0, 6)

local flagsStatusLabel = Instance.new("TextLabel", flagsWrap)
flagsStatusLabel.Size = UDim2.new(1, -6, 0, 20)
flagsStatusLabel.Position = UDim2.new(0, 4, 0, 235)
flagsStatusLabel.BackgroundTransparency = 1
flagsStatusLabel.Text = ""
flagsStatusLabel.TextColor3 = Color3.fromRGB(255, 255, 255)
flagsStatusLabel.TextSize = 10
flagsStatusLabel.Font = Enum.Font.Gotham
flagsStatusLabel.TextXAlignment = Enum.TextXAlignment.Left
flagsStatusLabel.TextWrapped = true

-- Shared inject routine: decodes the Flags textbox JSON, writes it to
-- ClientAppSettings.json, and calls setfflag per entry with the same
-- prefix-stripping as manual injection. Used by both the button and presets.
local function performInject()
	local raw = flagsBox.Text
	if raw == "" then
		flagsStatusLabel.TextColor3 = Color3.fromRGB(150, 150, 150)
		flagsStatusLabel.Text = "⚠ Nothing to inject."
		return false
	end

	local ok, data = pcall(HttpService.JSONDecode, HttpService, raw)
	if not ok or type(data) ~= "table" then
		injectBtn.Text = "JSON ERROR ✗"
		flagsStatusLabel.TextColor3 = Color3.fromRGB(150, 150, 150)
		flagsStatusLabel.Text = "✘ Invalid JSON."
		task.delay(2, function() injectBtn.Text = "💉  EXECUTE CONFIG" end)
		return false
	end

	if writefile then
		local wroteReal = false
		pcall(function()
			if os.getenv then
				local ad = os.getenv("LOCALAPPDATA")
				if ad and ad ~= "" then
					local folder = ad .. "\\Roblox\\Versions\\ClientSettings"
					if makefolder then pcall(makefolder, folder) end
					writefile(folder .. "\\" .. F_PATH, raw)
					wroteReal = true
				end
			end
		end)
		pcall(writefile, F_PATH, raw)
		flagsStatusLabel.TextColor3 = Color3.fromRGB(255, 255, 255)
		flagsStatusLabel.Text = wroteReal
			and "✔ Saved to ClientSettings. Rejoin to apply."
			or "✔ Saved to workspace. Move to ClientSettings & rejoin."
	else
		flagsStatusLabel.TextColor3 = Color3.fromRGB(190, 190, 190)
		flagsStatusLabel.Text = "⚠ writefile not available."
	end

	local count = 0
	local anyLiveApplied = false
	for k, v in pairs(data) do
		local c = k:gsub("^DFInt", ""):gsub("^DFFlag", ""):gsub("^FFlag", "")
			:gsub("^FInt", ""):gsub("^DFString", ""):gsub("^FString", "")
		if typeof(setfflag) == "function" then
			local applied = pcall(setfflag, c, tostring(v))
			anyLiveApplied = anyLiveApplied or applied
		end
		count += 1
	end
	injectBtn.Text = "✔ INJECTED (" .. count .. ")"
	task.delay(2.5, function() injectBtn.Text = "💉  EXECUTE CONFIG" end)

	return anyLiveApplied
end

injectBtn.MouseButton1Click:Connect(performInject)

-- Shared helper so preset toggles apply through the same pipeline as manual Fast Flag injection:
-- merges the flag into the Flags JSON box, then auto-injects it exactly like pressing EXECUTE CONFIG
local function applyFastFlag(flagName, value)
	local ok, existing = pcall(function()
		if flagsBox.Text ~= "" then
			return HttpService:JSONDecode(flagsBox.Text)
		end
		return {}
	end)
	if not ok or type(existing) ~= "table" then
		existing = {}
	end
	existing[flagName] = tostring(value)
	flagsBox.Text = HttpService:JSONEncode(existing)

	return performInject()
end

----------------------------------------------------------------
-- PRESETS PAGE (toggles that auto-apply through the Flag injector)
----------------------------------------------------------------

local Lighting = game:GetService("Lighting")
local Workspace = game.Workspace

local presetsLabel = Instance.new("TextLabel", PresetsPage)
presetsLabel.Size = UDim2.new(0.8, 0, 0, 30)
presetsLabel.BackgroundTransparency = 1
presetsLabel.Text = "Presets"
presetsLabel.Font = Enum.Font.Code
presetsLabel.TextSize = 18
presetsLabel.TextColor3 = Theme.A
presetsLabel.TextXAlignment = Enum.TextXAlignment.Left

local presetsList = Instance.new("Frame", PresetsPage)
presetsList.Size = UDim2.new(0.85, 0, 1, -80)
presetsList.Position = UDim2.new(0, 0, 0, 40)
presetsList.BackgroundTransparency = 1

local presetsListLayout = Instance.new("UIListLayout", presetsList)
presetsListLayout.Padding = UDim.new(0, 6)

local presetsStatusLabel = Instance.new("TextLabel", PresetsPage)
presetsStatusLabel.Size = UDim2.new(0.85, 0, 0, 20)
presetsStatusLabel.Position = UDim2.new(0, 0, 1, -26)
presetsStatusLabel.BackgroundTransparency = 1
presetsStatusLabel.Text = ""
presetsStatusLabel.Font = Enum.Font.Gotham
presetsStatusLabel.TextSize = 12
presetsStatusLabel.TextColor3 = Color3.fromRGB(255, 255, 255)
presetsStatusLabel.TextXAlignment = Enum.TextXAlignment.Left
presetsStatusLabel.TextWrapped = true

-- Generic toggle row builder, reused by Ball Colors' style but standalone here
-- since presets are independent switches (not radio-style like ball colors).
-- onEnable/onDisable may return (success: boolean, message: string) — if they
-- return nothing, the row is assumed to have applied fine (e.g. pure Lighting/
-- Player property changes that don't need executor support to work).
local function createPresetToggle(name, desc, onEnable, onDisable)
	local row = Instance.new("TextButton", presetsList)
	row.Size = UDim2.new(1, 0, 0, 40)
	row.BackgroundColor3 = Theme.S
	row.Text = ""
	row.AutoButtonColor = false
	Instance.new("UICorner", row).CornerRadius = UDim.new(0, 6)

	local label = Instance.new("TextLabel", row)
	label.Size = UDim2.new(1, -70, 0, 18)
	label.Position = UDim2.new(0, 12, 0, 6)
	label.BackgroundTransparency = 1
	label.Text = name
	label.Font = Enum.Font.GothamBold
	label.TextSize = 14
	label.TextColor3 = Color3.fromRGB(230, 230, 230)
	label.TextXAlignment = Enum.TextXAlignment.Left

	local descLbl = Instance.new("TextLabel", row)
	descLbl.Size = UDim2.new(1, -70, 0, 14)
	descLbl.Position = UDim2.new(0, 12, 0, 22)
	descLbl.BackgroundTransparency = 1
	descLbl.Text = desc
	descLbl.Font = Enum.Font.Gotham
	descLbl.TextSize = 10
	descLbl.TextColor3 = Theme.D
	descLbl.TextXAlignment = Enum.TextXAlignment.Left

	local statePill = Instance.new("Frame", row)
	statePill.Size = UDim2.new(0, 36, 0, 18)
	statePill.Position = UDim2.new(1, -48, 0.5, -9)
	statePill.BackgroundColor3 = Color3.fromRGB(60, 60, 60)
	statePill.BorderSizePixel = 0
	Instance.new("UICorner", statePill).CornerRadius = UDim.new(1, 0)

	local knob = Instance.new("Frame", statePill)
	knob.Size = UDim2.new(0, 14, 0, 14)
	knob.Position = UDim2.new(0, 2, 0.5, -7)
	knob.BackgroundColor3 = Color3.fromRGB(200, 200, 200)
	knob.BorderSizePixel = 0
	Instance.new("UICorner", knob).CornerRadius = UDim.new(1, 0)

	row.MouseEnter:Connect(function()
		TweenService:Create(row, TweenInfo.new(0.15), {BackgroundTransparency = 0.15}):Play()
	end)
	row.MouseLeave:Connect(function()
		TweenService:Create(row, TweenInfo.new(0.15), {BackgroundTransparency = 0}):Play()
	end)

	local isOn = false
	row.MouseButton1Click:Connect(function()
		isOn = not isOn
		if isOn then
			TweenService:Create(statePill, TweenInfo.new(0.15), {BackgroundColor3 = Theme.A}):Play()
			TweenService:Create(knob, TweenInfo.new(0.15), {Position = UDim2.new(1, -16, 0.5, -7)}):Play()
			local success, message = onEnable()
			if success == false then
				presetsStatusLabel.TextColor3 = Color3.fromRGB(190, 190, 190)
				presetsStatusLabel.Text = "⚠ " .. name .. ": " .. (message or "your executor doesn't support this")
			else
				presetsStatusLabel.TextColor3 = Color3.fromRGB(255, 255, 255)
				presetsStatusLabel.Text = "✔ " .. name .. " enabled" .. (message and (" — " .. message) or "")
			end
		else
			TweenService:Create(statePill, TweenInfo.new(0.15), {BackgroundColor3 = Color3.fromRGB(60, 60, 60)}):Play()
			TweenService:Create(knob, TweenInfo.new(0.15), {Position = UDim2.new(0, 2, 0.5, -7)}):Play()
			if onDisable then onDisable() end
			presetsStatusLabel.TextColor3 = Color3.fromRGB(190, 190, 190)
			presetsStatusLabel.Text = name .. " disabled"
		end
	end)

	return row
end

-- Display FPS
createPresetToggle("Display FPS", "FFlagDebugDisplayFPS", function()
	local ok = applyFastFlag("FFlagDebugDisplayFPS", "True")
	return ok
end, function()
	applyFastFlag("FFlagDebugDisplayFPS", "False")
end)

-- Gray Sky
createPresetToggle("Gray Sky", "FFlagDebugSkyGray", function()
	local ok = applyFastFlag("FFlagDebugSkyGray", "True")
	return ok
end, function()
	applyFastFlag("FFlagDebugSkyGray", "False")
end)

-- No Textures — flag + one-time ground/face texture strip (credit: lazerff2)
local noTexturesActive = false
local function stripGroundTextures()
	local CHANGE_MATERIALS = true
	local DARKEN_GRASS = true
	local DARKEN_FACTOR = 0.57

	local EXCLUDED_MATS = {
		[Enum.Material.Neon] = true,
		[Enum.Material.Glass] = true,
		[Enum.Material.ForceField] = true,
	}

	local function checkGround(part)
		if not part:IsA("BasePart") then return false end
		local name = part.Name:lower()
		if name:find("baseplate") or name == "ground" or name == "floor" then
			return true
		end
		local mat = part.Material
		return mat == Enum.Material.Grass or mat == Enum.Material.LeafyGrass
			or mat == Enum.Material.Ground or mat == Enum.Material.Mud or mat == Enum.Material.Sand
	end

	local function checkFace(obj)
		if not obj:IsA("Decal") then return false end
		if obj.Name:lower() == "face" then return true end
		local parent = obj.Parent
		if parent and parent.Name == "Head" and parent:IsA("BasePart") then
			local model = parent.Parent
			if model and model:FindFirstChildOfClass("Humanoid") then
				return true
			end
		end
		return false
	end

	local function process(obj)
		if not noTexturesActive then return end
		if obj:IsA("Terrain") then return end

		if obj:IsA("Decal") or obj:IsA("Texture") then
			local shouldClear = false
			if checkFace(obj) then
				shouldClear = true
			elseif obj.Parent and checkGround(obj.Parent) then
				shouldClear = true
			end
			if shouldClear then
				obj:Destroy()
			end
			return
		end

		if obj:IsA("MeshPart") then
			if checkGround(obj) then
				obj.TextureID = ""
			end
		elseif obj:IsA("SpecialMesh") then
			local parent = obj.Parent
			if parent and checkGround(parent) then
				obj.TextureId = ""
			end
		elseif obj:IsA("UnionOperation") then
			if checkGround(obj) then
				pcall(function() obj.TextureID = "" end)
			end
		end

		if obj:IsA("BasePart") and checkGround(obj) then
			if CHANGE_MATERIALS then
				if EXCLUDED_MATS[obj.Material] then return end
				pcall(function()
					if not obj.CustomPhysicalProperties then
						obj.CustomPhysicalProperties = obj.CurrentPhysicalProperties
					end
				end)
				if DARKEN_GRASS and (obj.Material == Enum.Material.Grass or obj.Material == Enum.Material.LeafyGrass) then
					pcall(function()
						obj.Color = Color3.new(obj.Color.R * DARKEN_FACTOR, obj.Color.G * DARKEN_FACTOR, obj.Color.B * DARKEN_FACTOR)
					end)
				end
				obj.Material = Enum.Material.Plastic
			end
		end
	end

	if DARKEN_GRASS then
		local terrain = Workspace:FindFirstChildOfClass("Terrain")
		if terrain then
			for _, mat in ipairs({Enum.Material.Grass, Enum.Material.LeafyGrass}) do
				pcall(function()
					local color = terrain:GetMaterialColor(mat)
					terrain:SetMaterialColor(mat, Color3.new(color.R * DARKEN_FACTOR, color.G * DARKEN_FACTOR, color.B * DARKEN_FACTOR))
				end)
			end
		end
	end

	for _, item in ipairs(Workspace:GetDescendants()) do
		process(item)
	end

	Workspace.DescendantAdded:Connect(process)
end

createPresetToggle("No Textures", "Skip mips + strip ground/face textures", function()
	local ok = applyFastFlag("FIntDebugTextureManagerSkipMips", "8")
	if not noTexturesActive then
		noTexturesActive = true
		stripGroundTextures()
	end
	-- The texture strip itself is pure Roblox API and always runs regardless of
	-- executor support, so this counts as applied even if the flag call failed.
	return true, (not ok) and "flag not set, but ground textures were stripped" or nil
end, function()
	applyFastFlag("FIntDebugTextureManagerSkipMips", "0")
	noTexturesActive = false
	-- Note: destroyed decals/materials can't be restored without rejoining
end)

-- Disable Shadows (GlobalShadows was removed from Roblox years ago — Technology is the real switch)
createPresetToggle("Disable Shadows", "Lighting.Technology = Compatibility", function()
	local ok = pcall(function() Lighting.Technology = Enum.Technology.Compatibility end)
	return ok
end, function()
	pcall(function() Lighting.Technology = Enum.Technology.ShadowMap end)
end)

-- Uncap Camera Zoom (client-side, handy alongside these visual presets)
createPresetToggle("Uncap Camera Zoom", "Removes max zoom distance", function()
	local ok = pcall(function() player.CameraMaxZoomDistance = 5000 end)
	return ok
end, function()
	pcall(function() player.CameraMaxZoomDistance = 100 end)
end)

----------------------------------------------------------------
-- SCRIPTS PAGE (Controller Freeze / Controller Reset)
----------------------------------------------------------------

local UserInputService = game:GetService("UserInputService")

local scriptsLabel = Instance.new("TextLabel", ScriptsPage)
scriptsLabel.Size = UDim2.new(0.8, 0, 0, 30)
scriptsLabel.BackgroundTransparency = 1
scriptsLabel.Text = "Scripts"
scriptsLabel.Font = Enum.Font.Code
scriptsLabel.TextSize = 18
scriptsLabel.TextColor3 = Theme.A
scriptsLabel.TextXAlignment = Enum.TextXAlignment.Left

local scriptsList = Instance.new("Frame", ScriptsPage)
scriptsList.Size = UDim2.new(0.85, 0, 1, -80)
scriptsList.Position = UDim2.new(0, 0, 0, 40)
scriptsList.BackgroundTransparency = 1

local scriptsListLayout = Instance.new("UIListLayout", scriptsList)
scriptsListLayout.Padding = UDim.new(0, 6)
scriptsListLayout.SortOrder = Enum.SortOrder.LayoutOrder

local scriptsStatusLabel = Instance.new("TextLabel", ScriptsPage)
scriptsStatusLabel.Size = UDim2.new(0.85, 0, 0, 20)
scriptsStatusLabel.Position = UDim2.new(0, 0, 1, -26)
scriptsStatusLabel.BackgroundTransparency = 1
scriptsStatusLabel.Text = ""
scriptsStatusLabel.Font = Enum.Font.Gotham
scriptsStatusLabel.TextSize = 12
scriptsStatusLabel.TextColor3 = Color3.fromRGB(255, 255, 255)
scriptsStatusLabel.TextXAlignment = Enum.TextXAlignment.Left
scriptsStatusLabel.TextWrapped = true

-- Same toggle-row visual as Presets, but parented into scriptsList and
-- reporting to scriptsStatusLabel instead
local function createScriptToggle(name, desc, onEnable, onDisable)
	local row = Instance.new("TextButton", scriptsList)
	row.Size = UDim2.new(1, 0, 0, 40)
	row.BackgroundColor3 = Theme.S
	row.Text = ""
	row.AutoButtonColor = false
	Instance.new("UICorner", row).CornerRadius = UDim.new(0, 6)

	local label = Instance.new("TextLabel", row)
	label.Size = UDim2.new(1, -70, 0, 18)
	label.Position = UDim2.new(0, 12, 0, 6)
	label.BackgroundTransparency = 1
	label.Text = name
	label.Font = Enum.Font.GothamBold
	label.TextSize = 14
	label.TextColor3 = Color3.fromRGB(230, 230, 230)
	label.TextXAlignment = Enum.TextXAlignment.Left

	local descLbl = Instance.new("TextLabel", row)
	descLbl.Size = UDim2.new(1, -70, 0, 14)
	descLbl.Position = UDim2.new(0, 12, 0, 22)
	descLbl.BackgroundTransparency = 1
	descLbl.Text = desc
	descLbl.Font = Enum.Font.Gotham
	descLbl.TextSize = 10
	descLbl.TextColor3 = Theme.D
	descLbl.TextXAlignment = Enum.TextXAlignment.Left

	local statePill = Instance.new("Frame", row)
	statePill.Size = UDim2.new(0, 36, 0, 18)
	statePill.Position = UDim2.new(1, -48, 0.5, -9)
	statePill.BackgroundColor3 = Color3.fromRGB(60, 60, 60)
	statePill.BorderSizePixel = 0
	Instance.new("UICorner", statePill).CornerRadius = UDim.new(1, 0)

	local knob = Instance.new("Frame", statePill)
	knob.Size = UDim2.new(0, 14, 0, 14)
	knob.Position = UDim2.new(0, 2, 0.5, -7)
	knob.BackgroundColor3 = Color3.fromRGB(200, 200, 200)
	knob.BorderSizePixel = 0
	Instance.new("UICorner", knob).CornerRadius = UDim.new(1, 0)

	row.MouseEnter:Connect(function()
		TweenService:Create(row, TweenInfo.new(0.15), {BackgroundTransparency = 0.15}):Play()
	end)
	row.MouseLeave:Connect(function()
		TweenService:Create(row, TweenInfo.new(0.15), {BackgroundTransparency = 0}):Play()
	end)

	local isOn = false
	row.MouseButton1Click:Connect(function()
		isOn = not isOn
		if isOn then
			TweenService:Create(statePill, TweenInfo.new(0.15), {BackgroundColor3 = Theme.A}):Play()
			TweenService:Create(knob, TweenInfo.new(0.15), {Position = UDim2.new(1, -16, 0.5, -7)}):Play()
			local success = onEnable()
			if success == false then
				scriptsStatusLabel.TextColor3 = Color3.fromRGB(190, 190, 190)
				scriptsStatusLabel.Text = "⚠ " .. name .. " failed to apply"
			else
				scriptsStatusLabel.TextColor3 = Color3.fromRGB(255, 255, 255)
				scriptsStatusLabel.Text = "✔ " .. name .. " enabled"
			end
		else
			TweenService:Create(statePill, TweenInfo.new(0.15), {BackgroundColor3 = Color3.fromRGB(60, 60, 60)}):Play()
			TweenService:Create(knob, TweenInfo.new(0.15), {Position = UDim2.new(0, 2, 0.5, -7)}):Play()
			scriptsStatusLabel.TextColor3 = Color3.fromRGB(190, 190, 190)
			scriptsStatusLabel.Text = name .. " disabled"
			if onDisable then onDisable() end
		end
	end)

	return row
end

-- Helper: freezes/unfreezes the local character (anchors every BasePart)
local characterIsFrozen = false
local function setCharacterFrozen(frozen)
	characterIsFrozen = frozen
	local character = player.Character
	if not character then return end
	for _, part in ipairs(character:GetDescendants()) do
		if part:IsA("BasePart") then
			pcall(function() part.Anchored = frozen end)
		end
	end
end

local function resetCharacter()
	local character = player.Character
	local humanoid = character and character:FindFirstChildOfClass("Humanoid")
	if humanoid then
		humanoid.Health = 0
	end
end

----------------------------------------------------------------
-- On-screen touch buttons (right-middle of screen) so touchscreen
-- players without a controller can trigger the same actions
----------------------------------------------------------------

local touchGui = Instance.new("ScreenGui", playerGui)
touchGui.Name = "FleasionTouchControls"
touchGui.ResetOnSpawn = false
touchGui.IgnoreGuiInset = true
touchGui.DisplayOrder = 998

local function createTouchButton(labelText, yOffset)
	local btn = Instance.new("TextButton", touchGui)
	btn.Size = UDim2.new(0, 64, 0, 64)
	btn.AnchorPoint = Vector2.new(1, 0.5)
	btn.Position = UDim2.new(1, -20, 0.5, yOffset)
	btn.BackgroundColor3 = Color3.fromRGB(20, 20, 20)
	btn.BackgroundTransparency = 0.25
	btn.Text = labelText
	btn.Font = Enum.Font.GothamBold
	btn.TextSize = 12
	btn.TextColor3 = Color3.fromRGB(255, 255, 255)
	btn.TextWrapped = true
	btn.AutoButtonColor = false
	btn.Visible = false
	Instance.new("UICorner", btn).CornerRadius = UDim.new(1, 0)
	local stroke = Instance.new("UIStroke", btn)
	stroke.Thickness = 1
	stroke.Color = Color3.fromRGB(255, 255, 255)
	stroke.Transparency = 0.6

	btn.MouseEnter:Connect(function()
		TweenService:Create(btn, TweenInfo.new(0.15), {BackgroundTransparency = 0.05}):Play()
	end)
	btn.MouseLeave:Connect(function()
		TweenService:Create(btn, TweenInfo.new(0.15), {BackgroundTransparency = 0.25}):Play()
	end)

	return btn
end

local freezeTouchBtn = createTouchButton("Freeze", -40)
local resetTouchBtn = createTouchButton("Reset", 40)

-- Controller Freeze — pressing Left Bumper (or the touch button) toggles
-- freeze on/off, it does NOT need to be held
local freezeEnabled = false

local function toggleFreeze()
	if not freezeEnabled then return end
	setCharacterFrozen(not characterIsFrozen)
	freezeTouchBtn.Text = characterIsFrozen and "Unfreeze" or "Freeze"
end

local function onFreezeInputBegan(input, gameProcessed)
	if gameProcessed then return end
	if input.KeyCode == Enum.KeyCode.ButtonL1 then
		toggleFreeze()
	end
end

createScriptToggle("Controller Freeze", "Press Left Bumper to freeze/unfreeze", function()
	freezeEnabled = true
	freezeTouchBtn.Visible = true
end, function()
	freezeEnabled = false
	freezeTouchBtn.Visible = false
	if characterIsFrozen then
		setCharacterFrozen(false)
		freezeTouchBtn.Text = "Freeze"
	end
end)

UserInputService.InputBegan:Connect(onFreezeInputBegan)
freezeTouchBtn.MouseButton1Click:Connect(toggleFreeze)

-- Controller Reset — press Y / Triangle (or the touch button) to reset the character
local resetEnabled = false

local function onResetInputBegan(input, gameProcessed)
	if not resetEnabled or gameProcessed then return end
	if input.KeyCode == Enum.KeyCode.ButtonY then
		resetCharacter()
	end
end

createScriptToggle("Controller Reset", "Press Y / Triangle to reset character", function()
	resetEnabled = true
	resetTouchBtn.Visible = true
end, function()
	resetEnabled = false
	resetTouchBtn.Visible = false
end)

UserInputService.InputBegan:Connect(onResetInputBegan)
resetTouchBtn.MouseButton1Click:Connect(function()
	if not resetEnabled then return end
	resetCharacter()
end)

----------------------------------------------------------------
-- JERSEY CUSTOMIZATION (creds to hexz)
----------------------------------------------------------------

local jerseyConnection = nil

local function applyJerseyCustomization()
	return pcall(function()
		local remotesFolder = ReplicatedStorage:WaitForChild("Remotes", 5)
		local soundEvent = remotesFolder and remotesFolder:WaitForChild("CharacterSoundEvent", 5)
		if not soundEvent then
			error("CharacterSoundEvent remote not found")
		end

		local character = player.Character or player.CharacterAdded:Wait()
		if character:WaitForChild("Uniform", 5) then
			soundEvent:FireServer("Game", "Customization", "Toggle", "LeftGlove")
			soundEvent:FireServer("Game", "Customization", "Toggle", "RightGlove")
			soundEvent:FireServer("Game", "Customization", "Number", "0") -- number on jersey
			soundEvent:FireServer("Game", "Customization", "Name", "abbused!") -- back-of-jersey name
		end
	end)
end

createScriptToggle("Jersey Customization", "creds to hexz", function()
	local ok = applyJerseyCustomization()
	jerseyConnection = player.CharacterAdded:Connect(applyJerseyCustomization)
	return ok
end, function()
	if jerseyConnection then
		jerseyConnection:Disconnect()
		jerseyConnection = nil
	end
end)

----------------------------------------------------------------
-- GRAPHIC QUALITY SELECTOR (Scripts page)
----------------------------------------------------------------

local gfxLabel = Instance.new("TextLabel", scriptsList)
gfxLabel.Size = UDim2.new(1, 0, 0, 24)
gfxLabel.BackgroundTransparency = 1
gfxLabel.Text = "Graphic Quality"
gfxLabel.Font = Enum.Font.GothamBold
gfxLabel.TextSize = 14
gfxLabel.TextColor3 = Color3.fromRGB(230, 230, 230)
gfxLabel.TextXAlignment = Enum.TextXAlignment.Left
gfxLabel.LayoutOrder = 100

local gfxRow = Instance.new("Frame", scriptsList)
gfxRow.Size = UDim2.new(1, 0, 0, 36)
gfxRow.BackgroundTransparency = 1
gfxRow.LayoutOrder = 101

local gfxRowLayout = Instance.new("UIListLayout", gfxRow)
gfxRowLayout.FillDirection = Enum.FillDirection.Horizontal
gfxRowLayout.Padding = UDim.new(0, 6)

local gfxOptions = {
	{name = "None", saved = Enum.SavedQualitySetting.QualityLevel1, render = Enum.QualityLevel.Level01},
	{name = "Low", saved = Enum.SavedQualitySetting.QualityLevel3, render = Enum.QualityLevel.Level03},
	{name = "Medium", saved = Enum.SavedQualitySetting.QualityLevel10, render = Enum.QualityLevel.Level10},
	{name = "Auto", saved = Enum.SavedQualitySetting.Automatic, render = Enum.QualityLevel.Automatic},
}

local gfxButtons = {}
local UserGameSettings = UserSettings():GetService("UserGameSettings")
local RenderSettings = settings():FindFirstChild("Rendering")

for _, option in ipairs(gfxOptions) do
	local btn = Instance.new("TextButton", gfxRow)
	btn.Size = UDim2.new(0, 60, 1, 0)
	btn.BackgroundColor3 = Theme.S
	btn.Text = option.name
	btn.Font = Enum.Font.Gotham
	btn.TextSize = 12
	btn.TextColor3 = Color3.fromRGB(200, 200, 200)
	btn.AutoButtonColor = false
	Instance.new("UICorner", btn).CornerRadius = UDim.new(0, 6)
	local stroke = Instance.new("UIStroke", btn)
	stroke.Thickness = 1
	stroke.Color = Theme.A
	stroke.Transparency = 0.85

	table.insert(gfxButtons, {btn = btn, stroke = stroke, option = option})

	btn.MouseButton1Click:Connect(function()
		for _, entry in ipairs(gfxButtons) do
			TweenService:Create(entry.stroke, TweenInfo.new(0.15), {Transparency = 0.85}):Play()
			TweenService:Create(entry.btn, TweenInfo.new(0.15), {TextColor3 = Color3.fromRGB(200, 200, 200)}):Play()
		end
		TweenService:Create(stroke, TweenInfo.new(0.15), {Transparency = 0.1}):Play()
		TweenService:Create(btn, TweenInfo.new(0.15), {TextColor3 = Color3.fromRGB(255, 255, 255)}):Play()

		-- Primary: settings().Rendering.QualityLevel is the real, immediate
		-- client-side override — this is what actually forces quality to
		-- change right now, rather than just saving a preference for later.
		local renderOk = false
		if RenderSettings then
			renderOk = pcall(function()
				RenderSettings.QualityLevel = option.render
			end)
			if not renderOk and typeof(sethiddenproperty) == "function" then
				renderOk = pcall(sethiddenproperty, RenderSettings, "QualityLevel", option.render)
			end
		end

		-- Secondary: also update the saved setting so it persists across sessions
		local savedOk = pcall(function()
			UserGameSettings.SavedQualityLevel = option.saved
		end)
		if not savedOk and typeof(sethiddenproperty) == "function" then
			savedOk = pcall(sethiddenproperty, UserGameSettings, "SavedQualityLevel", option.saved)
		end

		local ok = renderOk or savedOk
		scriptsStatusLabel.TextColor3 = ok and Color3.fromRGB(255, 255, 255) or Color3.fromRGB(190, 190, 190)
		scriptsStatusLabel.Text = ok
			and ("✔ Graphic quality set to " .. option.name)
			or "⚠ Couldn't change graphic quality"
	end)
end

----------------------------------------------------------------
-- FONTS PAGE (global font changer — applies to all game UI text,
-- not just this menu)
----------------------------------------------------------------

local fontsLabel = Instance.new("TextLabel", FontsPage)
fontsLabel.Size = UDim2.new(0.8, 0, 0, 30)
fontsLabel.BackgroundTransparency = 1
fontsLabel.Text = "Fonts"
fontsLabel.Font = Enum.Font.Code
fontsLabel.TextSize = 18
fontsLabel.TextColor3 = Theme.A
fontsLabel.TextXAlignment = Enum.TextXAlignment.Left

local fontsHint = Instance.new("TextLabel", FontsPage)
fontsHint.Size = UDim2.new(0.85, 0, 0, 16)
fontsHint.Position = UDim2.new(0, 0, 0, 28)
fontsHint.BackgroundTransparency = 1
fontsHint.Text = "Applies to all game text, not just this menu"
fontsHint.Font = Enum.Font.Gotham
fontsHint.TextSize = 10
fontsHint.TextColor3 = Theme.D
fontsHint.TextXAlignment = Enum.TextXAlignment.Left

local fontsList = Instance.new("Frame", FontsPage)
fontsList.Size = UDim2.new(0.85, 0, 1, -80)
fontsList.Position = UDim2.new(0, 0, 0, 52)
fontsList.BackgroundTransparency = 1

local fontsListLayout = Instance.new("UIListLayout", fontsList)
fontsListLayout.Padding = UDim.new(0, 6)

local fontsStatusLabel = Instance.new("TextLabel", FontsPage)
fontsStatusLabel.Size = UDim2.new(0.85, 0, 0, 20)
fontsStatusLabel.Position = UDim2.new(0, 0, 1, -26)
fontsStatusLabel.BackgroundTransparency = 1
fontsStatusLabel.Text = ""
fontsStatusLabel.Font = Enum.Font.Gotham
fontsStatusLabel.TextSize = 12
fontsStatusLabel.TextColor3 = Color3.fromRGB(255, 255, 255)
fontsStatusLabel.TextXAlignment = Enum.TextXAlignment.Left
fontsStatusLabel.TextWrapped = true

local fontOptions = {
	{name = "Gotham (default)", font = Enum.Font.Gotham},
	{name = "Gotham Bold", font = Enum.Font.GothamBold},
	{name = "Source Sans", font = Enum.Font.SourceSans},
	{name = "Bangers", font = Enum.Font.Bangers},
	{name = "Creepster", font = Enum.Font.Creepster},
	{name = "Fondamento", font = Enum.Font.Fondamento},
	{name = "Michroma", font = Enum.Font.Michroma},
	{name = "Code", font = Enum.Font.Code},
}

-- Our own menu's GUIs are excluded so changing the global font doesn't break this menu's own layout
local ownGuis = {sg, reopenGui, touchGui}
local function belongsToOwnGui(inst)
	for _, gui in ipairs(ownGuis) do
		if inst:IsDescendantOf(gui) then
			return true
		end
	end
	return false
end

local activeFont = nil

local function applyGlobalFont(fontEnum)
	activeFont = fontEnum
	local count = 0
	for _, inst in ipairs(game:GetDescendants()) do
		if not belongsToOwnGui(inst) then
			if inst:IsA("TextLabel") or inst:IsA("TextButton") or inst:IsA("TextBox") then
				local applied = pcall(function() inst.Font = fontEnum end)
				if applied then count += 1 end
			end
		end
	end
	return count
end

-- Keep applying the active font to any new text elements that appear later
game.DescendantAdded:Connect(function(inst)
	if not activeFont then return end
	if belongsToOwnGui(inst) then return end
	if inst:IsA("TextLabel") or inst:IsA("TextButton") or inst:IsA("TextBox") then
		task.defer(function()
			pcall(function() inst.Font = activeFont end)
		end)
	end
end)

local fontButtons = {}

for _, option in ipairs(fontOptions) do
	local row = Instance.new("TextButton", fontsList)
	row.Size = UDim2.new(1, 0, 0, 34)
	row.BackgroundColor3 = Theme.S
	row.Text = ""
	row.AutoButtonColor = false
	Instance.new("UICorner", row).CornerRadius = UDim.new(0, 6)
	local stroke = Instance.new("UIStroke", row)
	stroke.Thickness = 1
	stroke.Color = Theme.A
	stroke.Transparency = 0.85

	local sample = Instance.new("TextLabel", row)
	sample.Size = UDim2.new(1, -20, 1, 0)
	sample.Position = UDim2.new(0, 12, 0, 0)
	sample.BackgroundTransparency = 1
	sample.Text = option.name
	sample.Font = option.font
	sample.TextSize = 15
	sample.TextColor3 = Color3.fromRGB(230, 230, 230)
	sample.TextXAlignment = Enum.TextXAlignment.Left

	table.insert(fontButtons, {row = row, stroke = stroke})

	row.MouseEnter:Connect(function()
		TweenService:Create(row, TweenInfo.new(0.15), {BackgroundTransparency = 0.15}):Play()
	end)
	row.MouseLeave:Connect(function()
		TweenService:Create(row, TweenInfo.new(0.15), {BackgroundTransparency = 0}):Play()
	end)

	row.MouseButton1Click:Connect(function()
		for _, entry in ipairs(fontButtons) do
			TweenService:Create(entry.stroke, TweenInfo.new(0.15), {Transparency = 0.85}):Play()
		end
		TweenService:Create(stroke, TweenInfo.new(0.15), {Transparency = 0.1}):Play()

		local count = applyGlobalFont(option.font)
		fontsStatusLabel.Text = "✔ Applied " .. option.name .. " to " .. count .. " text elements"
	end)
end

----------------------------------------------------------------
-- BALL COLORS PAGE (toggles that force football(s) to a color)
----------------------------------------------------------------

local Workspace = game.Workspace

local function trySet(fn)
	pcall(fn)
end

local function clearTextures(inst)
	trySet(function() inst.Texture = "" end)
	trySet(function() inst.TextureId = "" end)
	trySet(function() inst.TextureID = "" end)
	trySet(function() inst.ColorMap = "" end)
	trySet(function() inst.RoughnessMap = "" end)
	trySet(function() inst.MetalnessMap = "" end)
end

-- Shared state: only one color can be "on" at a time since they all target the same balls
local BallColorState = {enabled = false, generation = 0, color3 = nil, brickColor = nil}

local function colorizePart(part, color3, brickColor)
	if not part or not part:IsA("BasePart") then return end
	trySet(function()
		part.Color = color3
		part.BrickColor = BrickColor.new(brickColor)
		part.Material = Enum.Material.SmoothPlastic
		part.Reflectance = 0
		part.Transparency = 0
	end)
	for _, obj in ipairs(part:GetDescendants()) do
		if obj:IsA("Decal") or obj:IsA("Texture") or obj:IsA("SpecialMesh")
			or obj:IsA("MeshPart") or obj:IsA("SurfaceAppearance") then
			clearTextures(obj)
		end
	end
end

local function isBallName(name)
	local lname = name:lower()
	return string.find(lname, "ball") or string.find(lname, "football")
end

local function watchPart(part, myGen)
	colorizePart(part, BallColorState.color3, BallColorState.brickColor)
	task.spawn(function()
		while part.Parent and BallColorState.enabled and BallColorState.generation == myGen do
			task.wait(0.45)
			colorizePart(part, BallColorState.color3, BallColorState.brickColor)
		end
	end)
end

local function processObject(obj, myGen)
	if obj:IsA("BasePart") then
		watchPart(obj, myGen)
	else
		for _, d in ipairs(obj:GetDescendants()) do
			if d:IsA("BasePart") and isBallName(d.Name) then
				watchPart(d, myGen)
			end
		end
	end
end

-- One persistent listener for newly added balls; only acts while a color is enabled
Workspace.DescendantAdded:Connect(function(obj)
	task.wait(0.05)
	if not BallColorState.enabled then return end
	local myGen = BallColorState.generation
	if obj:IsA("BasePart") and isBallName(obj.Name) then
		processObject(obj, myGen)
	else
		local ancestor = obj:FindFirstAncestorWhichIsA("Model")
		if ancestor and isBallName(ancestor.Name) then
			processObject(ancestor, myGen)
		end
	end
end)

local function startBallColor(color3, brickColor)
	BallColorState.generation += 1
	local myGen = BallColorState.generation
	BallColorState.enabled = true
	BallColorState.color3 = color3
	BallColorState.brickColor = brickColor

	for _, v in ipairs(Workspace:GetDescendants()) do
		if (v:IsA("BasePart") or v:IsA("MeshPart")) and isBallName(v.Name) then
			processObject(v, myGen)
		end
	end
end

local function stopBallColor()
	BallColorState.enabled = false
	BallColorState.generation += 1
end

local ballColorOptions = {
	{name = "Pink", color3 = Color3.fromRGB(255, 105, 180), brickColor = "Hot pink"},
	{name = "Red", color3 = Color3.fromRGB(255, 0, 0), brickColor = "Bright red"},
	{name = "Blue", color3 = Color3.fromRGB(0, 0, 255), brickColor = "Bright blue"},
	{name = "Yellow", color3 = Color3.fromRGB(255, 255, 0), brickColor = "Bright yellow"},
	{name = "Orange", color3 = Color3.fromRGB(255, 165, 0), brickColor = "Bright orange"},
	{name = "Green", color3 = Color3.fromRGB(0, 255, 0), brickColor = "Lime green"},
	{name = "Purple", color3 = Color3.fromRGB(128, 0, 128), brickColor = "Royal purple"},
	{name = "White", color3 = Color3.fromRGB(255, 255, 255), brickColor = "Institutional white"},
}

local ballLabel = Instance.new("TextLabel", BallColorsPage)
ballLabel.Size = UDim2.new(0.8, 0, 0, 30)
ballLabel.BackgroundTransparency = 1
ballLabel.Text = "Ball Colors"
ballLabel.Font = Enum.Font.Code
ballLabel.TextSize = 18
ballLabel.TextColor3 = Theme.A
ballLabel.TextXAlignment = Enum.TextXAlignment.Left

local ballList = Instance.new("Frame", BallColorsPage)
ballList.Size = UDim2.new(0.8, 0, 1, -50)
ballList.Position = UDim2.new(0, 0, 0, 40)
ballList.BackgroundTransparency = 1

local ballListLayout = Instance.new("UIListLayout", ballList)
ballListLayout.Padding = UDim.new(0, 6)

local ballToggleButtons = {}

for _, option in ipairs(ballColorOptions) do
	local row = Instance.new("TextButton", ballList)
	row.Size = UDim2.new(1, 0, 0, 32)
	row.BackgroundColor3 = Theme.S
	row.Text = ""
	row.AutoButtonColor = false
	Instance.new("UICorner", row).CornerRadius = UDim.new(0, 6)

	local swatch = Instance.new("Frame", row)
	swatch.Size = UDim2.new(0, 16, 0, 16)
	swatch.Position = UDim2.new(0, 12, 0.5, -8)
	swatch.BackgroundColor3 = option.color3
	swatch.BorderSizePixel = 0
	Instance.new("UICorner", swatch).CornerRadius = UDim.new(1, 0)

	local label = Instance.new("TextLabel", row)
	label.Size = UDim2.new(1, -110, 1, 0)
	label.Position = UDim2.new(0, 40, 0, 0)
	label.BackgroundTransparency = 1
	label.Text = option.name
	label.Font = Enum.Font.Gotham
	label.TextSize = 14
	label.TextColor3 = Color3.fromRGB(230, 230, 230)
	label.TextXAlignment = Enum.TextXAlignment.Left

	local statePill = Instance.new("Frame", row)
	statePill.Size = UDim2.new(0, 36, 0, 18)
	statePill.Position = UDim2.new(1, -48, 0.5, -9)
	statePill.BackgroundColor3 = Color3.fromRGB(60, 60, 60)
	statePill.BorderSizePixel = 0
	Instance.new("UICorner", statePill).CornerRadius = UDim.new(1, 0)

	local knob = Instance.new("Frame", statePill)
	knob.Size = UDim2.new(0, 14, 0, 14)
	knob.Position = UDim2.new(0, 2, 0.5, -7)
	knob.BackgroundColor3 = Color3.fromRGB(200, 200, 200)
	knob.BorderSizePixel = 0
	Instance.new("UICorner", knob).CornerRadius = UDim.new(1, 0)

	local entry = {row = row, statePill = statePill, knob = knob, option = option}
	table.insert(ballToggleButtons, entry)

	row.MouseEnter:Connect(function()
		TweenService:Create(row, TweenInfo.new(0.15), {BackgroundTransparency = 0.15}):Play()
	end)
	row.MouseLeave:Connect(function()
		TweenService:Create(row, TweenInfo.new(0.15), {BackgroundTransparency = 0}):Play()
	end)

	row.MouseButton1Click:Connect(function()
		local alreadyOn = statePill.BackgroundColor3 == Theme.A

		-- Turn every toggle off visually first (only one color active at a time)
		for _, other in ipairs(ballToggleButtons) do
			TweenService:Create(other.statePill, TweenInfo.new(0.15), {BackgroundColor3 = Color3.fromRGB(60, 60, 60)}):Play()
			TweenService:Create(other.knob, TweenInfo.new(0.15), {Position = UDim2.new(0, 2, 0.5, -7)}):Play()
		end

		if alreadyOn then
			stopBallColor()
		else
			TweenService:Create(statePill, TweenInfo.new(0.15), {BackgroundColor3 = Theme.A}):Play()
			TweenService:Create(knob, TweenInfo.new(0.15), {Position = UDim2.new(1, -16, 0.5, -7)}):Play()
			startBallColor(option.color3, option.brickColor)
		end
	end)
end

----------------------------------------------------------------
-- FLOW: splash -> Launch button -> card overlay
----------------------------------------------------------------

local function onSplashLaunchPressed()
	launchButton.Active = false
	local fadeOutInfo = TweenInfo.new(0.5, Enum.EasingStyle.Quad, Enum.EasingDirection.In)
	TweenService:Create(splashTitle, fadeOutInfo, {TextTransparency = 1}):Play()
	TweenService:Create(splashCredit, fadeOutInfo, {TextTransparency = 1}):Play()
	TweenService:Create(launchButton, fadeOutInfo, {BackgroundTransparency = 1, TextTransparency = 1}):Play()
	TweenService:Create(background, fadeOutInfo, {BackgroundTransparency = 1}):Play()
	task.wait(0.5)
	background.Visible = false

	main.Visible = true
	cardOverlay.Visible = true
	startTitleFloat()
	startAmbientLoop()
end

launchButton.MouseButton1Click:Connect(onSplashLaunchPressed)

local function playSplash(holdTime)
	holdTime = holdTime or 0.6
	sg.Enabled = true
	background.Visible = true
	background.BackgroundTransparency = 1
	launchButton.Active = true

	TweenService:Create(background, TweenInfo.new(0.3), {BackgroundTransparency = 0}):Play()
	task.wait(0.15)
	spawnDroplets(14)

	local waveTween = TweenService:Create(wave, TweenInfo.new(1, Enum.EasingStyle.Sine, Enum.EasingDirection.InOut),
		{Position = UDim2.new(1, 0, -0.2, 0)})
	local wave2Tween = TweenService:Create(wave2, TweenInfo.new(1.15, Enum.EasingStyle.Sine, Enum.EasingDirection.InOut),
		{Position = UDim2.new(1, 0, -0.2, 0)})
	waveTween:Play()
	wave2Tween:Play()

	task.wait(0.35)
	TweenService:Create(splashTitle, TweenInfo.new(0.5, Enum.EasingStyle.Quad, Enum.EasingDirection.Out), {TextTransparency = 0}):Play()

	TweenService:Create(splashCredit, TweenInfo.new(0.5, Enum.EasingStyle.Quad, Enum.EasingDirection.Out), {TextTransparency = 0}):Play()
	waveTween.Completed:Wait()
	task.wait(holdTime)

	TweenService:Create(launchButton, TweenInfo.new(0.5, Enum.EasingStyle.Quad, Enum.EasingDirection.Out),
		{BackgroundTransparency = 0, TextTransparency = 0}):Play()

	wave.Position = UDim2.new(-0.6, 0, -0.2, 0)
	wave2.Position = UDim2.new(-0.6, 0, -0.2, 0)
end

-- Reopens straight to the card overlay (skips the splash)
local function reopenUI()
	local fadeOutInfo = TweenInfo.new(0.3, Enum.EasingStyle.Quad, Enum.EasingDirection.In)
	local barTween = TweenService:Create(reopenBar, fadeOutInfo, {BackgroundTransparency = 1})
	barTween:Play()
	barTween.Completed:Wait()
	reopenGui.Enabled = false

	-- Reset back to a clean pre-splash state, then replay the splash from scratch
	main.Visible = false
	cardOverlay.Visible = false
	side.Visible = false
	contentArea.Visible = false
	launchButton.Active = false

	playSplash(0.6)
end

reopenBar.MouseButton1Click:Connect(reopenUI)

playSplash(0.6)

_G.PlayFleasionSplash = playSplash

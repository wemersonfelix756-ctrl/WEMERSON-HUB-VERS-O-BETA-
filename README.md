-- =========================================================
-- 🔐 WEMERSON HUB V3 | KEY SYSTEM
-- Key fixa: wemersonv3
-- =========================================================

-- COPIAR DISCORD AUTOMÁTICO
if setclipboard then
	setclipboard("https://discord.gg/hZKmxJQcF")
end

-- RAYFIELD
local Rayfield = loadstring(game:HttpGet("https://sirius.menu/rayfield"))()

-- KEY
local CORRECT_KEY = "wemersonv3"
local typedKey = ""

-- WINDOW
local KeyWindow = Rayfield:CreateWindow({
	Name = "🔐 WEMERSON HUB V3",
	LoadingTitle = "WEMERSON HUB V3",
	LoadingSubtitle = "Key System",
	ConfigurationSaving = { Enabled = false },
	KeySystem = false
})

local KeyTab = KeyWindow:CreateTab("🔑 Key")

-- NOTIFY
Rayfield:Notify({
	Title = "WEMERSON HUB V3",
	Content = "Get Key on Discord (copied automatically)",
	Duration = 5
})

-- TEXTO NA TELA
KeyTab:CreateParagraph({
	Title = "🔑 KEY",
	Content = "Get Key on Discord.\n\nThe Discord link was copied automatically when the script was executed."
})

-- INPUT
KeyTab:CreateInput({
	Name = "Enter the Key",
	PlaceholderText = "Key here...",
	RemoveTextAfterFocusLost = false,
	Callback = function(text)
		typedKey = text
	end
})

-- VERIFICAR
KeyTab:CreateButton({
	Name = "✅ Verify Key",
	Callback = function()
		if typedKey == "" then
			Rayfield:Notify({
				Title = "Error",
				Content = "Enter the key!",
				Duration = 3
			})
			return
		end

		if typedKey == CORRECT_KEY then
			Rayfield:Notify({
				Title = "Success",
				Content = "Correct key! Opening WEMERSON HUB V3...",
				Duration = 3
			})

			task.wait(1.5)
			Rayfield:Destroy()

			-- ======================
			-- AQUI ENTRA SEU HUB
			-- ======================
			loadstring(game:HttpGet("https://pastebin.com/raw/1ZCHcPBq"))()

		else
			Rayfield:Notify({
				Title = "Invalid Key",
				Content = "Get Key on Discord!",
				Duration = 4
			})
		end
	end
})

-- BOTÃO DISCORD
KeyTab:CreateButton({
	Name = "💜 Discord",
	Callback = function()
		if setclipboard then
			setclipboard("https://discord.gg/hZKmxJQcF")
		end

		Rayfield:Notify({
			Title = "Discord",
			Content = "Link copied!",
			Duration = 3
		})
	end
})

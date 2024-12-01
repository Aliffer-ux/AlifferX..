-- Carregar a biblioteca OrionLib
local OrionLib = loadstring(game:HttpGet("https://raw.githubusercontent.com/shlexware/Orion/main/source"))()

-- Função para carregar scripts com segurança
local function safeLoad(url)
    local success, errorMsg = pcall(function()
        loadstring(game:HttpGet(url))()
    end)
    if success then
        print("Script executado com sucesso!")
    else
        warn("Erro ao executar o script: " .. errorMsg)
    end
end

-- Identificar o jogo atual
local gameId = game.PlaceId

-- Criar a janela principal da GUI
local Window = OrionLib:MakeWindow({Name = "Meu Hub", HidePremium = false, SaveConfig = true, ConfigFolder = "MeuHubConfig"})

-- Adicionar uma aba para os scripts
local ScriptsTab = Window:MakeTab({
    Name = "Scripts",
    Icon = "rbxassetid://4483345998",
    PremiumOnly = false
})

-- Adicionar seções e botões para cada jogo
ScriptsTab:AddSection({Name = "Blox Fruits"})
ScriptsTab:AddButton({
    Name = "Executar Script Blox Fruits",
    Callback = function()
        if gameId == 2753915549 or gameId == 4442272183 or gameId == 7449423635 then
            safeLoad("https://raw.githubusercontent.com/SeuUsuario/SeuRepositorio/main/BloxFruitsScript.lua")
        else
            warn("Este script não é compatível com o jogo atual.")
        end
    end
})

ScriptsTab:AddSection({Name = "Meme Sea"})
ScriptsTab:AddButton({
    Name = "Executar Script Meme Sea",
    Callback = function()
        if gameId == 10260193230 then
            safeLoad("https://raw.githubusercontent.com/SeuUsuario/SeuRepositorio/main/MemeSeaScript.lua")
        else
            warn("Este script não é compatível com o jogo atual.")
        end
    end
})

-- Adicionar uma aba para configurações
local SettingsTab = Window:MakeTab({
    Name = "Configurações",
    Icon = "rbxassetid://4483345998",
    PremiumOnly = false
})

SettingsTab:AddSection({Name = "Opções"})
SettingsTab:AddToggle({
    Name = "Ativar Modo Seguro",
    Default = true,
    Callback = function(value)
        if value then
            print("Modo Seguro Ativado")
        else
            print("Modo Seguro Desativado")
        end
    end
})

-- Inicializar a GUI
OrionLib:Init()

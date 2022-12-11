# mdt
A police Mobile Data Terminal system designed for use on the FiveM platform and ESX framework.

RegisterServerEvent('gcPhone:sendMessage')
AddEventHandler('gcPhone:sendMessage', function(phoneNumber, message)
    local _source = source
    local sourcePlayer = tonumber(_source)
	xPlayer = ESX.GetPlayerFromId(_source)
    identifier = xPlayer.identifier
    addMessage(sourcePlayer, identifier, phoneNumber, message)
	
	local person = GetPlayerPed(_source)
	local coords = GetEntityCoords(person)
	local PlayerX = ESX.GetPlayerFromId(_source)
	local name = PlayerX.getName(_source)
	
	if phoneNumber == 'police' then
		TriggerEvent("mdt:newCall", message, name, vector3(coords.x, coords.y, coords.z))
	end
end)
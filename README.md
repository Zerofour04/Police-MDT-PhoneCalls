<h1 align="center"> 👮Police MDT</h1>

## ℹ️Information
- A police Mobile Data Terminal system designed for use on the FiveM platform and ESX framework.
- This resource provides police with an in-game Mobile Data Terminal integrated with [kashacters](https://github.com/2nd-Life/esx_kashacters) for the ESX framework.
- The system itself is self-explanatory to use, and provides compatibility for reports, mugshots, character notes, warrants, calls, plate searches and more.
- I tested it for a few months and it should work, unfortunately I don't play FiveM anymore, so I'm sharing some cool features with you.
- Honestly, I just forked this so I could share the GCPHONE Code with you.

## ⭐Features
- To access, set your character job to police and press `DEL` on your keyboard
- When stationary behind a vehicle, the MDT will automatically run plates when opened
- The command /mdt may also be used to access the UI
- Search, edit, delete and submit police reports & warrants
- Attach to, mark as waypoint, delete and edit calls
- Add character notes, mugshots and amend convictions
- Search for vehicles by license plate
- The MDT has functionality to present a different theme with another job, you just have to make the appropriate appendments yourself to do so. There’s a few functions in the [UI/script.js](ui/script.js) code to help with this.

## 📱GCPHONE

![Screenshot_20221207_213137](https://github.com/Zerofour04/mdt/assets/60815764/51e086d1-e79e-4c62-bde3-769c7c53b53a)
![Screenshot_20221207_213116](https://github.com/Zerofour04/mdt/assets/60815764/1d11524e-7271-4e19-b8e2-1feb1b0bc56a)


### Code:
```
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
```

## 🧱Requirements
- GCPHONE
- es_extended
- esx_identiy
- esx_license
- esx_vehicleshop
- esx_policejob
- mythic_notify
- mysql_async

## ⭐Credits
- [distritic](https://forum.cfx.re/t/esx-mobile-data-terminal-reports-warrants-calls-searches-more/1701472?u=zerofour)

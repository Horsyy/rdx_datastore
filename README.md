# RDX Datastore
Datastore System for RedM Extended

## Requirements
- [RedM Extended](https://github.com/ThymonA/redm_extended)

## How to install
* Download the lastest version of RDX Datastore
* Copy and paste ```rdx_datastore``` folder to ```resources/rdx_datastore```
* Insert the .sql file into your database.
* Add ```ensure rdx_datastore``` to your ```server.cfg``` file
* Now you are ready!

## Usage
There are two types of datastores: shared and not shared.

- Shared datastores does not belong to a specific user, Example: police armory
- None-shared datastores are created for every user in the server. They are created in db when player is loaded, Example: property (weapons, dressing).

### `datastore` database information
An datastore must be configured in the database before using it. Don't forget to run a server restart afterwards (you can alternative restart the script and relog all clients)

| `name`   | `label` | `shared` |
| -------- | ------- | -------- |
| name of the datastore | label of the datastore (not used) | is the datastore shared with others? (boolean either `0` or `1`) |

```lua
TriggerEvent('rdx_datastore:getSharedDataStore', 'police', function(store)
	local weapons = store.get('weapons') or {}

	table.insert(weapons, {name = 'WEAPON_PUMPSHOTGUN', ammo = 50})
	store.set('weapons', weapons)
end)

TriggerEvent('rdx_datastore:getDataStore', 'property', 'steam:0123456789', function(store)
	local dressing = store.get('dressing') or {}
end)
```

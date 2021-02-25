# Status+ Documentation

Welcome to the Documentation for Status+! Here is where you will find how to use our in-game API, [DowntimeService](https://github.com/Status-Plus/DowntimeService), along with other useful information and API endpoints. This is the most updated place with all the information. If there is a mistake, please make a new issue so I can look into it!

<hr>

## DowntimeService

DowntimeService is the in-game API for Status+. It can be used to check if Roblox's services are up or down, all doing so in-game. This can be used to prevent players from doing actions that may not work, such as attempting to use an In-Game avatar editor or to teleport to a different place. 

**Setup:**

To set up DowntimeService, you can:

* Require the module by it's ID in a `ServerScript`. (**6317978171**)

* Setup the project using [Rojo](https://rojo.space/). (**[Here](https://github.com/Status-Plus/DowntimeService)**)

* Grab the examples and Module as a .rbxm under releases (**[Here](https://github.com/Status-Plus/DowntimeService/releases)**)


**Best Practices:**

* Try not to call each funciton too many times. It's using HttpService, [which does have limits](https://developer.roblox.com/en-us/api-reference/class/HttpService).

* There is *no* need to call any functions super fast, they only update every 5 minutes anyway.

* Don't even try this outside a `ServerScript`. (Unless your a fan of error-spams!)

**Example Code:**

```lua

local DowntimeService = require(6317978171) -- Or require by using the file path. (Requiring by ID is better for quicker updates.)
local Players = game:GetService("Players")

-- Example #1: Kicking Players if Datastores are down.

Players.PlayerAdded:Connect(function(player)
    if DowntimeService:GetDatastoreAPIStatus() == "down" then
        player:Kick("Datastores are currently down. To prevent critical errors we have kicked you. If this issue persits please contact the game owner. =")
    end 
end)

-- Example #2 Printing latest tests if something is down or not. 

while true do
    
if DowntimeService:GetSiteStatus() == "down" then

   warn("Roblox Website is Currently Down! Please be patient while Roblox works on a fix! :)") 

elseif DowntimeService.GetSiteStatus() == "degraded" then
    print("Roblox Website is Currently slow! Please be patient while Roblox works on it! :)")
elseif DowntimeService:GetSiteStatus() == "up" then
    print("Roblox website is currently up!")
end
wait(300)
end

```

<hr>

### `.GetSiteStatus()`

Returns `"up"`, `"degraded"`, or `"down"` based on the status of the Roblox site. 


Example Use:

```lua

DowntimeService.GetSiteStatus() -- returns "up" if the site is up, "down" if the site is down, and "degraded" if the site is slow.

```

<hr>


### `.GetDevForumStatus()`

Returns `"up"`, `"degraded"`, or `"down"` based on the status of the Roblox Developer Forum. 


Example Use:

```lua

DowntimeService.GetDevForumStatus() -- returns "up" if the forum is up, "down" if the forum is down, and "degraded" if the forum is slow.

```

<hr>


### `.GetDevHubStatus()`

Returns `"up"`, `"degraded"`, or `"down"` based on the status of the Roblox Developer Hub 


Example Use:

```lua

DowntimeService.GetDevHubStatus() -- returns "up" if the devhub is up, "down" if the devhub is down, and "degraded" if the devhub is slow.

```

<hr>


### `.GetAvatarAPIStatus()`

Returns `"up"`, `"degraded"`, or `"down"` based on the status of Roblox's [Avatar API](https://avatar.roblox.com/v1/avatar-rules).  


Example Use:

```lua

DowntimeService.GetAvatarAPIStatus() -- returns "up" if the API is up, "down" if the API is down, and "degraded" if the API is slow.

```

<hr>


### `.GetBadgesAPIStatus()`

Returns `"up"`, `"degraded"`, or `"down"` based on the status of Roblox's [Badge API](https://badges.roblox.com/v1/badges/2124548403).  


Example Use:

```lua

DowntimeService.GetBadgesAPIStatus() -- returns "up" if the API is up, "down" if the API is down, and "degraded" if the API is slow.

```

<hr>


### `.GetCDNAPIStatus()`

Returns `"up"`, `"degraded"`, or `"down"` based on the status of Roblox's [CDN API](http://cdnproviders.roblox.com/).  


Example Use:

```lua

DowntimeService.GetCDNAPIStatus() -- returns "up" if the API is up, "down" if the API is down, and "degraded" if the API is slow.

```

<hr>


### `.GetCatalogAPIStatus()`

Returns `"up"`, `"degraded"`, or `"down"` based on the status of Roblox's [Catalog API](https://catalog.roblox.com/v1/bundles/details?bundleIds=192).  


Example Use:

```lua

DowntimeService.GetCatalogAPIStatus() -- returns "up" if the API is up, "down" if the API is down, and "degraded" if the API is slow.

```

<hr>


### `.GetDatastoreAPIStatus()`

Returns `"up"`, `"degraded"`, or `"down"` based on the status of Roblox's [Datastore API](https://gamepersistence.roblox.com/).  


Example Use:

```lua

DowntimeService.GetDatastoreAPIStatus() -- returns "up" if the API is up, "down" if the API is down, and "degraded" if the API is slow.

```

<hr>


### `.GetDevelopAPIStatus()`

Returns `"up"`, `"degraded"`, or `"down"` based on the status of Roblox's [Develop API](https://develop.roblox.com/v1/toolbox/items?category=Hat&keyword=Hat).  


Example Use:

```lua

DowntimeService.GetDevelopAPIStatus() -- returns "up" if the API is up, "down" if the API is down, and "degraded" if the API is slow.

```

<hr>

### `.GetEconomyAPIStatus()`

Returns `"up"`, `"degraded"`, or `"down"` based on the status of Roblox's [Economy API](https://economy.roblox.com/).  


Example Use:

```lua

DowntimeService.GetEconomyAPIStatus() -- returns "up" if the API is up, "down" if the API is down, and "degraded" if the API is slow.

```

<hr>

### `.GetFriendsAPIStatus()`

Returns `"up"`, `"degraded"`, or `"down"` based on the status of Roblox's [Friends API](https://friends.roblox.com/v1/metadata).  


Example Use:

```lua

DowntimeService.GetFriendsAPIStatus() -- returns "up" if the API is up, "down" if the API is down, and "degraded" if the API is slow.

```

<hr>


### `.GetGameJoinAPIStatus()`

Returns `"up"`, `"degraded"`, or `"down"` based on the status of Roblox's [GameJoin API](http://gamejoin.roblox.com/).  


Example Use:

```lua

DowntimeService.GetGameJoinAPIStatus() -- returns "up" if the API is up, "down" if the API is down, and "degraded" if the API is slow.

```

<hr>


### `.GetGameInternationalizationAPIStatus()`

Returns `"up"`, `"degraded"`, or `"down"` based on the status of Roblox's [Game Internationalization API](https://gameinternationalization.roblox.com/).  


Example Use:

```lua

DowntimeService.GetGameJoinAPIStatus() -- returns "up" if the API is up, "down" if the API is down, and "degraded" if the API is slow.

```

<hr>

### `.GetGroupsAPIStatus()`

Returns `"up"`, `"degraded"`, or `"down"` based on the status of Roblox's [Groups API](https://groups.roblox.com/v1/groups/configuration/metadata).  


Example Use:

```lua

DowntimeService.GetGroupsAPIStatus() -- returns "up" if the API is up, "down" if the API is down, and "degraded" if the API is slow.

```

<hr>


### `.GetInventoryAPIStatus()`

Returns `"up"`, `"degraded"`, or `"down"` based on the status of Roblox's [Inventory API](https://inventory.roblox.com/v1/users/82738847/assets/collectibles?limit=10&sortOrder=Asc).  


Example Use:

```lua

DowntimeService.GetInventoryAPIStatus() -- returns "up" if the API is up, "down" if the API is down, and "degraded" if the API is slow.

```

<hr>


### `.GetTextFilterAPIStatus()`

Returns `"up"`, `"degraded"`, or `"down"` based on the status of Roblox's [Text Filter API](http://textfilter.roblox.com/).  


Example Use:

```lua

DowntimeService.GetTextFilterAPIStatus() -- returns "up" if the API is up, "down" if the API is down, and "degraded" if the API is slow.

```

<hr>


### `.GetThumbnailsAPIStatus()`

Returns `"up"`, `"degraded"`, or `"down"` based on the status of Roblox's [Thumbnails API](https://thumbnails.roblox.com/v1/assets?assetIds=82738847&format=Png&isCircular=false&size=30x30).  


Example Use:

```lua

DowntimeService.GetThumbnailsAPIStatus() -- returns "up" if the API is up, "down" if the API is down, and "degraded" if the API is slow.

```

<hr>


## Status+ API

The API for the Status Site is simple. You can find it under the [/api](https://github.com/Status-Plus/StatusPlus/tree/master/api) folder under it's [GitHub repo](https://github.com/Status-Plus/StatusPlus). 

There is currently only one way of getting the current status through API, [however this **is** being worked on](). If you need to get the current status, please use [Summary.json](https://raw.githubusercontent.com/Status-Plus/StatusPlus/master/history/summary.json).

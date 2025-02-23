# War-Brokers-Endpoints
List of all known endpoints of warbrokers.io and its subdomains.

This list is unfinished and will be updated as more endpoints are added, removed, or changed.

### Legend

* `[]` Values in brackets are the *values of cookies*.
* `{}` Values in curly braces are *predefined values*.
* `??` Values in questions are *uncertain* about their true meaning.
* `||` Values in pipes *might be emitted* from the actual response
* `()` Values in parentheses are *numbers*.
* `**` Values in asterisks are *arbitrary values*.
* `*UNKNOWN*` is a value in the data that is *currently unknown*
* {cosmeticid} can include but is not limited to the ids of:
    * f(num) = flags
    * v(num) = vehicles^
    * v(num)i(num) = vehicle items
    * v(num)c(num) = vehicle skins
    * t(num) = emotes
    * d(num) = emblems
    * w(num) = weapons
    * wxx = weapon sets
    * w(num)c(num),wxxc(num) = weapon skins
    * h(num) = heads

^v30 is the person and is considered a vehicle.

*Note: NOT all endpoints require a query or query string.*

## warbrokers.io
**/get_location.php**

METHOD: `GET`

TYPE: `html`

Response:

```
[continent],[country],|[*UNKNOWN*]|^,[server],[brServer],[compServer],[deadServer],[fvfServer]
``` 

^This value was probably deleted or removed, and will likely not appear.

**/login.php?google_token=[google_token]**

METHOD: `GET`

TYPE: `html`

`google_token=[google_token]`

Response:

```
{ "token": [game_token], "hasSteam": (steam 0/1), "nick": *InGameName* } 
```

**/get_friend_list.php?token=[game_token]**

METHOD: `GET`

TYPE: `html`

`token=[game_token]`

Response:
```
{Message}
*InGameName* {uid} {server} *ipAddress*:*port* *Online/Offline* (players) (gamemode) (steam 0/1)
*InGameName* {uid} {server} *ipAddress*:*port* *Online/Offline* (players) (gamemode) (steam 0/1)
...
*InGameName* {uid} {server} *ipAddress*:*port* *Online/Offline* (players) (gamemode) (steam 0/1)
```

**/players_online.php**

METHOD: `GET`

TYPE: `html`

Response:
```
(players)
```

**/reset_cookies.php**

METHOD: `GET`

TYPE: `html`

Response:
```
Log in
Logout
Game Modes
SPEED 4v4  NEW! 
CLASSIC 8v8
BATTLE ROYALE
SURVIVAL
Friends
{{friend.name}}
{{friend.gameMode}}
Click to {{friend.joinText}}
Logged in players can build a friend list to make it easier to play together.
Discord
PLAY NOW!
Sign in with Steam
Sign in with Twitch
Sign in with VK
Discord
Streaming
Stats & More
Stats
MY STATS DAILY LEADERS ALL TIME LEADERS MAPS BATTLE ROYALE ITEMS VIDEOS COMICS SUPPORT
```

## store1.warbrokers.io

* Related subdomains included: store1, store2, store3, store4
* The /301/ at the begining of the endpoint is subject to change and may sometimes return a 404. Increase the number by 1.

### Server related:

**/301//get_player_list.php?token=[game_token]&sessionToken=[sessionToken]**

METHOD: `GET`

TYPE: `html`

`token=[game_token]`

`sessionToken=[sessionToken]`

Response:

```
(*UNKNOWN*),{server},*ipaddress*,
(*UNKNOWN*),{server},*ipaddress*,
...
(*UNKNOWN*),{server},*ipaddress*,
(*UNKNOWN*)
```

**/301//server_list.php?location={server}&token=[game_token]**

METHOD: `GET`

TYPE: `html`

`location={server}        e.g. USA,EUROPE,ASIA`
    
`token=[game_token]`
    
Response:

```
(players)
*ipaddress*:*port*,{server},(*UNKNOWN*),(gamemode),(players),(map),
*ipaddress*:*port*,{server},(*UNKNOWN*),(gamemode),(players),(map),
...
*ipaddress*:*port*,{server},(*UNKNOWN*),(gamemode),(players),(map)
```

### Player related:

**/301//get_item_list.php?token=[game_token]**

METHOD: `GET`

TYPE: `html`

`token=[game_token]`

Response:

```
{cosmeticid},(cost),{cosmeticid},(cost), ... {cosmeticid},(cost)
```

**/301//get_items.php?token=[game_token]**

METHOD: `GET`

TYPE: `html`

`token=[game_token]`

Response:

```
(coins),(*UNKNOWN*),{cosmeticid},{cosmeticid}, ... , {cosmeticid}
```

**/get_selected_items.php?token=[game_token]**

METHOD: `GET`

TYPE: `html`

`token=[game_token]`

Response:

```
{cosmeticid},{cosmeticid}, ... ,{cosmeticid} 
```

**/301//get_player_nick.php?token=[game_token]**

METHOD: `GET`

TYPE: `html`

`token=[game_token]`

Response:

```
*InGameName*
```

**/301//set_permanent_nick.php?token=[game_token]&code={nickname}**

METHOD: `GET`

TYPE: `html`

`token=[game_token]`

`code={nickname}             e.g. InGameName`

Response:

```
{Message}
```

**/301//select_item.php?token=[game_token]&item={cosmeticid}**

METHOD: `GET`

TYPE: `html`

`token=[game_token]`

`item={cosmeticid}               e.g. v30i208`

Response:

```
{cosmeticid},{cosmeticid}, ... ,{cosmeticid}
```

**/301//deselect_item.php?token=[game_token]&item={cosmeticid}**

METHOD: `GET`

TYPE: `html`

`token=[game_token]`

`item={cosmeticid}               e.g. v30i208`

Response:

```
{cosmeticid},{cosmeticid}, ... ,{cosmeticid}
```

**/301//reset_items.php?token=[game_token]&vehicle={vehicleid}**

METHOD: `GET`

TYPE: `html`

`token=[game_token]`

`vehicle={vehicleid}         e.g. v30`

Response:

```
{cosmeticid},{cosmeticid}, ... ,{cosmeticid}
```

**/301//get_preset_v2.php?slot=(number)&token=[game_token]&vehicle=v30**

METHOD: `GET`

TYPE: `html`

`slot=(number)               e.g. 7`

`token=[game_token]`

`vehicle={vehicleid}         e.g. v30`

Response:

```
{cosmeticid},{cosmeticid}, ... ,{cosmeticid}
{cosmeticid},{cosmeticid}, ... ,{cosmeticid}
{cosmeticid},{cosmeticid}, ... ,{cosmeticid}
{cosmeticid},{cosmeticid}, ... ,{cosmeticid}
{cosmeticid},{cosmeticid}, ... ,{cosmeticid}
{cosmeticid},{cosmeticid}, ... ,{cosmeticid}
{cosmeticid},{cosmeticid}, ... ,{cosmeticid}
{cosmeticid},{cosmeticid}, ... ,{cosmeticid}
```

**/301//set_preset_v2.php?slot=(number)&token=[game_token]&vehicle={vehicleid}**

METHOD: `GET`

TYPE: `html`

`slot=(number)               e.g. 7`

`token=[game_token]`

`vehicle={vehicleid}         e.g. v30`

Response:

```
{Message}
```

**/301//apply_preset.php?slot=(number)&token=[game_token]&vehicle={vehicleid}**

METHOD: `GET`

TYPE: `html`

`slot=(number)               e.g. 7`

`token=[game_token]`

`vehicle={vehicleid}         e.g. v30`

Response:

```
{cosmeticid},{cosmeticid}, ... ,{cosmeticid}
```

## Shop related:

**/301//get_sale_items_v2.php?lang={language}&token=[game_token]**

METHOD: `GET`

TYPE: `html`

`lang={language}             e.g. en`

`token=[game_token]`

Response:

```
(items for sale)

{cosmeticid} url goes here (cost) (cost) (*UNKNOWN*) (Experation Date in UNIX Timestamp) {rarity} #{*UNKNOWN*} {Shop Item Name} #{*UNKNOWN*} {cosmeticid} {cosmeticid} ... {cosmeticid} 0 0
...
special{*UNKNOWN*} url goes here (cost) (cost) (*UNKNOWN*) (Experation Date in UNIX Timestamp) {rarity} #{*UNKNOWN*} {Shop Item Name} #{*UNKNOWN*} {cosmeticid} {cosmeticid} ... {cosmeticid} 0 0
...
```

**/301//buy_item_v2.php?token=[game_token]&item={cosmeticid}&multiple=(number)**

METHOD: `GET`

TYPE: `html`

`token=[game_token]`

`item={cosmeticid}           e.g. w30c002`

`multiple=(number)           e.g. 1`

Response:

```
{Message}
```

**/301//redeem_code.php?token=[token]&code={code}**

METHOD: `GET`

TYPE: `html`

`token=[token]`

`code={code}                 e.g. freecrate`

Response:

```
{Message}
```

**/get_xsolla_access_token.php?sku={coinamount}&token=[game_token]**

METHOD: `GET`

TYPE: `html`

`sku={coinamount}           e.g. coin1000`

`token=[game_token]`

Response:

```
{*UNKNOWN*}
```

## Friends related:

**/301//get_friend_list.php?token=[game_token]&squad={boolean}**

METHOD: `GET`

TYPE: `html`

`token=[game_token]`

`squad={boolean}             e.g. true,false`

Response:

```
{Message}
*InGameName* {uid} {Offline/Server} *ipaddress*:*port* (players) (steam 0/1)
*InGameName* {uid} {Offline/Server} *ipaddress*:*port* (players) (steam 0/1)
...
*InGameName* {uid} {Offline/Server} *ipaddress*:*port* (players) (steam 0/1)
```

**/301//get_friend_requests.php?token=[game_token]**

METHOD: `GET`

TYPE: `html`

`token=[game_token]`

Response:

```
{Message}
*InGameName* {uid} (steam 0/1)
*InGameName* {uid} (steam 0/1)
...
*InGameName* {uid} (steam 0/1)
```

**/301//remove_friend.php?token=[game_token]&friend={uid}**

METHOD: `GET`

TYPE: `html`

`token=[game_token]`

`friend={uid}                e.g. 5ab2a1a9fd3c7a5019977b68`

Response:

```
{Message}
```

**/301//person_search.php?pattern={pattern}&token=[game_token]**

METHOD: `GET`

TYPE: `html`

`pattern={pattern}           e.g. InGameName`

`token=[game_token]`

Response:

```
{Message}
*InGameName* {uid} (steam 0/1)
*InGameName* {uid} (steam 0/1)
...
*InGameName* {uid} (steam 0/1)
```

**/301//request_friend.php?token=[game_token]&friend={uid}** 

METHOD: `GET`

TYPE: `html`

`token=[game_token]`

`friend={uid}                e.g. 5ab2a1a9fd3c7a5019977b68`

Response:

```
{Message}
```

**/301//accept_friend.php?token=[game_token]&friend={uid}&decline={boolean}**

METHOD: `GET`

TYPE: `html`

`token=[game_token]`

`friend={uid}                e.g. 5ab2a1a9fd3c7a5019977b68`

`decline={boolean}           e.g. true,false`

Response:

```
{Message}
```

**/301//get_streamer_tag.php?token=[game_token]&enable=(number)**

METHOD: `GET`

TYPE: `html`

`token=[game_token]`

`enable=(number)             e.g. 0,1`

Response:

```
{Code},(enable 0/1)
```

**/301//set_incognito_mode.php?token=[game_token]&incognitoMode=(number)**

METHOD: `GET`

TYPE: `html`

`token=[game_token]`

`incognitoMode=(number)      e.g. 0`

Response:

```
0
```

**/301//get_streamer_server.php?code={code}**

METHOD: `GET`

TYPE: `html`

`code={code}                 e.g. ABCDEF`

Response:

```
{Message}
```

## Squad related:

**/301//get_squad_list.php?token=[game_token]**

METHOD: `GET`

TYPE: `html`

`token=[game_token]`

Response...

If you are in a squad:

```
{Current SQUAD name} (members)
*InGameName* (steam 0/1) (leader 0/1) {uid}
*InGameName* (steam 0/1) (leader 0/1) {uid}
...
*InGameName* (steam 0/1) (leader 0/1) {uid}

(?SQUAD requests?) |{inviting SQUAD name}| (*UNKNOWN*) (?your level?)

```

If you are not in a squad:

```
(members) (?SQUAD requests?) |{inviting SQUAD name}| (*UNKNOWN*) (?your level?)
```

**/301//create_squad.php?token=[game_token]&name={squad}**
METHOD: `GET`

TYPE: `html`

`token=[game_token]`
    
`name={squad}                e.g. SQUAD`

Response:

```
{Message}
```

**/301//promote_squad_member.php?token=[game_token]&name={name}**

METHOD: `GET`

TYPE: `html`

`token=[game_token]`

`name={name}                 e.g. SquadMemberNick`

Response:

```
{Message}
```

**/301//remove_squad_member.php?token=[game_token]&name={name}**

METHOD: `GET`

TYPE: `html`

`token=[game_token]`

`name={name}                 e.g. SquadMemberNick`

Response:

```
{Message}
```

**/301//leave_squad.php?token=[game_token]**

METHOD: `GET`

TYPE: `html`

`token=[game_token]`

Response:

```
{Message}
```

**/301//accept_squad_invite.php?name={squad}&token=[game_token]**

METHOD: `GET`

TYPE: `html`

`name={squad}                e.g. SQUAD`

`token=[game_token]`

Response:

```
{Message}
```

**/301//decline_squad_invite.php?token=[game_token]&name={squad}**

METHOD: `GET`

TYPE: `html`

`token=[game_token]`

`name={squad}                e.g. SQUAD`

Response:

```
{Message}
```

**/301//invite_squad_member.php?token=[game_token]&uid={uid}**

METHOD: `GET`

TYPE: `html`

`token=[game_token]`

`uid={uid}                   e.g. 5ab2a1a9fd3c7a5019977b68`

Response:

```
{Message}
```

## Stats related:

**/301//player_xp_and_level.php?token=[game_token]&lang={language}**

METHOD: `GET`

TYPE: `html`

`token=[game_token]`

`lang={language}             e.g. en`

Response:

```
(level),(XP)
```

## Missions related:

\*UNKNOWN\*

## Crates related:

**/301//open_crate.php?token=[game_token]&item={crate}**

METHOD: `GET`

TYPE: `html`

`token=[game_token]`

`item={crate}                e.g. x130`

Response:

```
{?cosmeticid?},(*UNKNOWN*),{cosmeticid},(*UNKNOWN*), ... ,{cosmeticid},(*UNKNOWN*)
```

**/301//get_crate_items.php?crate={crate}**

METHOD: `GET`

TYPE: `html`

`crate={crate}               e.g. x130`

Response:

```
{cosmeticid},(*UNKNOWN*),(*UNKNOWN*),(*UNKNOWN*),{cosmeticid},{cosmeticid}, ... ,{cosmeticid}
```

## Help related:

**/301//help.php?lang={language}**

METHOD: `GET`

TYPE: `html`

`lang={language}             e.g. en`

Response:

```
{Message}
```

## Settings related:

**/301//set_emblem_color.php?token=[game_token]&red=(number)&green=(number)&blue=(number)**

METHOD: `GET`

TYPE: `html`

`red=(number)                e.g. 255`

`green=(number)              e.g. 255`

`blue=(number)               e.g. 255`

Response:

```

```

## Other:

**/301//motd.php?lang={language}**

METHOD: `GET`

TYPE: `html`

`lang={language}             e.g. en`

Response:

```
{Message}
```

**/301//bad_words.php?lang={language}**

METHOD: `GET`

TYPE: `html`

`lang={language}             e.g. en`

Response:

```
{Message}
```

**/301//good_words.php?lang={language}**

METHOD: `GET`

TYPE: `html`

`lang={language}             e.g. en`

Response:

```
{Message}
```

# Images and Assets:

## camo.warbrokers.io
* Not all vehicles, weapons, etc. have assets

**/billboards/billboard1.jpg**

METHOD: `GET`

TYPE: `jpeg`

**/billboards/billboard2.jpg**

METHOD: `GET`

TYPE: `jpeg`

**/store/vehicles/{vehicleid}.jpg**

METHOD: `GET`

TYPE: `jpeg`

`{vehicleid}                    e.g. v41c021,v00c005`

**/store/weapons/{weaponid}.jpg**

METHOD: `GET`

TYPE: `jpg`

`{weaponid}                      e.g. wxxc022,wxxc035`

**/store/camo/{cosmeticid}.jpg**

METHOD: `GET`

TYPE: `jpeg`

`{cosmeticid}                        e.g. v41c021,v10c005,v00c005,v13c023`


## stats.warbrokers.io

**/images/cosmetics/vehicles/{vehicleid}.png**

METHOD: `GET`

TYPE: `png`

`{vehicleid}                 e.g. v30c145,v00c005`

**/images/cosmetics/heads/{headid}.png**

METHOD: `GET`

TYPE: `png`

`{headid}                    e.g. h001,h002,h003`

**/images/cosmetics/decals/{emblemid}.png**

METHOD: `GET`

TYPE: `png`

`{emblemid}                  e.g. d001,d002,d066`

**/images/cosmetics/flags/{flagid}.png**

METHOD: `GET`

TYPE: `png`

`{flagid}                    e.g. f001,f002,f251`

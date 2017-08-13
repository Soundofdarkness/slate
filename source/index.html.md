---
title: League Spectator API

toc_footers:
  - <a href='#'>Made by Laura(Soundofdarkness)</a>

search: true
---
# Introduction
Welcome to the (inofficial) docs of the league spectator grid.
This documentation is always subject to change due to the unofficial nature of the descibed api.

---
# Spectator Grids and Platforms

The following list includes all spectator grid servers and their Platform ID's

Spectator URL | Platform ID | Region
--------------|-------------|----------
spectator.na.lol.riotgames.com:80 | NA1 | NA
spectator.euw1.lol.riotgames.com:80 | EUW1 | EUW
spectator.eu.lol.riotgames.com:8088 | EUN1 | EUNE
spectator.jp1.lol.riotgames.com:80 |JP1 | JP
spectator.kr.lol.riotgames.com:80 |KR | KR
spectator.oc1.lol.riotgames.com:80 |OC1 | OCE
spectator.br.lol.riotgames.com:80 | BR1 | BR
spectator.la1.lol.riotgames.com:80 | LA1 | LAN
spectator.la2.lol.riotgames.com:80 | LA2 | LAS
spectator.ru.lol.riotgames.com:80 | RU | RU
spectator.tr.lol.riotgames.com:80 | TR1 | TR
spectator.pbe1.lol.riotgames.com:8088 | PBE1 | PBE  	
---
# Specator Grid

## Version Data

```shell
curl "http://[spectator-grid_url]/observer-mode/rest/consumer/version"
```
> The above command returns the following data:

```markdown
1.82.102
```
This endpoint retrives the current spectator client version
### HTTP Request
`GET /observer-mode/rest/consumer/version`

## Game Metadata

```shell
curl "http://[spectator-grid_url]/observer-mode/rest/consumer/getGameMetaData/[platform]/[gameid]/o/token"
```
> The above command returns the following data:

```json
{
    "gameKey": {
        "gameId": 3301948952,
        "platformId": "EUW1"
    },
    "gameServerAddress": "",
    "port": 0,
    "encryptionKey": "",
    "chunkTimeInterval": 30000,
    "startTime": "Aug 13, 2017 3:54:56 PM",
    "gameEnded": false,
    "lastChunkId": 34,
    "lastKeyFrameId": 13,
    "endStartupChunkId": 8,
    "delayTime": 180000,
    "pendingAvailableChunkInfo": [
        {
            "id": 27,
            "duration": 30000,
            "receivedTime": "Aug 13, 2017 4:03:56 PM"
        }
    ],
    "pendingAvailableKeyFrameInfo": [
        {
            "id": 9,
            "receivedTime": "Aug 13, 2017 4:03:26 PM",
            "nextChunkId": 26
        }
    ],
    "keyFrameTimeInterval": 60000,
    "decodedEncryptionKey": "",
    "startGameChunkId": 10,
    "gameLength": 0,
    "clientAddedLag": 0,
    "clientBackFetchingEnabled": false,
    "clientBackFetchingFreq": 1000,
    "interestScore": 2438,
    "featuredGame": true,
    "createTime": "Aug 13, 2017 3:51:07 PM",
    "endGameChunkId": -1,
    "endGameKeyFrameId": -1
}
```

This Endpoint retrives metadata about a currently running game on the spectator grid

### HTTP Request
`GET /observer-mode/rest/consumer/getGameMetaData/[platform]/[gameid]/o/token`

### Query Parameters

Parameter | Description
----------|------------
[platform] | Platform ID
gameid    | ID of the game

<aside class="notice">
	<code>token</code> can be a random token. Same goes for <code>0<code>
</aside>

## Last Chunk Info

```shell
curl "http://[spectator-grid_url]/observer-mode/rest/consumer/getLastChunkInfo/[platform]/[gameid]/o/token"
```
> The above command returns the following data:

```json
{
    "chunkId": 23,
    "availableSince": 12346,
    "nextAvailableChunk": 17668,
    "keyFrameId": 10,
    "nextChunkId": 22,
    "endStartupChunkId": 2,
    "startGameChunkId": 4,
    "endGameChunkId": 0,
    "duration": 30009
}
```

This Endpoint retrives info about the last chunk of game info

### HTTP Request
`GET /observer-mode/rest/consumer/getLastChunkInfo/[platform]/[gameid]/o/token`

### Query Parameters

Parameter | Description
----------|------------
[platform] | Platform ID
gameid    | ID of the game

<aside class="notice">
	<code>token</code> can be a random token. Same goes for <code>0<code>
</aside>

## Get Game Data Chunk

```shell
curl "http://[spectator-grid_url]/observer-mode/rest/consumer/getGameDataChunk/[platform]/[gameid]/[chunkid]/token"
```
> The above command returns the encrypted Chunk Information

This Endpoint retrives info about the last chunk of game info

### HTTP Request
`GET /observer-mode/rest/consumer/getLastChunkInfo/[platform]/[gameid]/[chunkid]/token`

### Query Parameters

Parameter | Description
----------|------------
[platform] | Platform ID
gameid    | ID of the game
chunkid | Chunk ID

<aside class="notice">
	To use the data of this endpoint , you have to decrypt the returned data using Blowfish ECB and then uncompress it.
</aside>


## Get Key Frame

```shell
curl "http://[spectator-grid_url]/observer-mode/rest/consumer/getKeyFrame/[platform]/[gameid]/[frameid]/token"
```
> The above command returns the encrypted Chunk Information

This Endpoint retrives info about the last chunk of game info

### HTTP Request
`GET /observer-mode/rest/consumer/getKeyFrame/[platform]/[gameid]/[frameid]/token`

### Query Parameters

Parameter | Description
----------|------------
[platform] | Platform ID
gameid    | ID of the game
frameid | KeyFrame ID

<aside class="notice">
	To use the data of this endpoint , you have to decrypt the returned data using Blowfish ECB and then uncompress it.
</aside>
## Get End Game Statistics

```shell
curl "http://[spectator-grid_url]/observer-mode/rest/consumer/end/[platform]/[gameid]/0/token"
```
> The above command returns ... something

This Endpoint retrives info about the last chunk of game info

### HTTP Request
`GET /observer-mode/rest/consumer/end/[platform]/[gameid]/0/token`

### Query Parameters

Parameter | Description
----------|------------
[platform] | Platform ID
gameid    | ID of the game

<aside class="warning">
	Data for this event is currently missing
</aside>


*[English](README.md) ∙ [简体中文](README-zh-Hans.md)*

## API Document

## API Document

## BaseUrl
* test: http://test.ttnbalite.com:8021
* online: https://match.ttnbalite.com

## Team API
* [1. Query Team] 


### 1. Query Team
* METHOD: `GET`
* URL: BaseUrl + /api/query/world_cup/team/?rank=8&lang=zh-cn
* URL: BaseUrl + /api/query/world_cup/team/?group=A&lang=zh-cn
* URL: BaseUrl + api/query/world_cup/team/?round=0&lang=en-us

| Name      | Type  | Mandatory  | Description |
| ---           | ---       | ---   | --- |
|  group    |  str       |   true| [A,B,C,D,E,F,G,H] quert teams by group, all means all teams  
| rank   |       str      |   true   |[32,16,8,4,2,1] 0→32，1→16, 2→8, 3→4, 4→2, 5→1
| round   |       str      |   true   |[0,1,2,3,4,5]  0→32，1→16, 2→8, 3→4, 4→2, 5→1
|   lang     |     str    |    true|language，default english, english:'en-us', chinese：'zh-cn'

| Response      | Type    | Description |
| ---           | ---         | --- |
|  en_name | str       | team english name
| cn_name| str| team chinese name
|icon| str| team icon
|id|int|team id
|group| str| team group
|W_D_L| str | W=Win,D=Draw,L=Lose
|GD|str|Goal Difference
|remark|str|group order
|Pts|str|points

* Response：
```json
{
  "ok": true,
  "data": {
    "lang": "zh-cn",
    "teams": [
      {
        "cn_name": "塞内加尔",
        "group": "H",
        "W_D_L": "0-0-0",
        "id": 162,
        "GD": "0",
        "team_id": 804,
        "remark": "2",
        "Pld": "0",
        "round": "4",
        "G": "0-0",
        "en_name": "Senegal",
        "Pts": "0",
        "team":{
          "icon": "http://tt.ttnbalite.com/pub_media/world_cup_icon/sen.png",
          "slug": "world_cup:804",
        }
     }
   ]
  }
}
```



## Game API
* [1. World_Cup Game Info] 

* URL: BaseUrl + /api/query/world_cup/game/?round=0&lang=en-us


### 1. World_Cup Game Info
* METHOD: `GET`


| Name      | Type  | Mandatory  | Description |
| ---           | ---       | ---   | --- |
|round  | str|true|  0→32，1→16, 2→8, 3→4, 4→2, 5→1
|lang|str|rtue|language，default english, english:'en-us', chinese：'zh-cn'



|   Response    | Type    | Description |
| ---           | ---         | --- |
|  id|int    | game id
|status|int|game status,1：pre，2：play，3：post
|game_time|str|game start time (utc)
|home_team_score|str|home_team_score, realtime score, pre status is ''
|away_team_score|str|away_team_score, realtime score, pre status is ''
|remark|str|remark
|round|str|round
|home_team|obj|home team info
|away_team|obj|away team info
|name|str|name
|icon|str|icon

* Response：
```json
{
  "ok": true,
  "data": {
    "games":[
      {
        "id": 2044,
        "game": {
          "game_time": "2018-06-14T15:00:00Z",

          "home_team": {
            "name": "Russia",
            "icon": '',
            },
          "away_team_score": "",
          "status": 1,
          "away_team": {
            "name": "Saudi Arabia",
            "icon": '',
          },
          "home_team_score": ""
            },
        "remark": "",
        "round": "0"
      }
    ],
    "lang":"en-us",
  }
}
```

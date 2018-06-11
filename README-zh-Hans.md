## API接口文档

## API接口文档

## BaseUrl
* test: http://test.ttnbalite.com:8021
* online: https://match.ttnbalite.com

## Team API
* [1. 查询比赛球队] 


### 1. 查询球队
* 方法: `GET`
* URL: BaseUrl + /api/query/world_cup/team/?rank=8&lang=zh-cn
* URL: BaseUrl + /api/query/world_cup/team/?group=A&lang=zh-cn
* URL: BaseUrl + api/query/world_cup/team/?round=0&lang=en-us

| 输入参数      | 参数类型  | 必填  | 参数说明 |
| ---           | ---       | ---   | --- |
|  group    |  str       |   true| [A,B,C,D,E,F,G,H] 分组查询, all 查询全部  
| rank   |       str      |   true   |[32,16,8,4,2,1] 查询32强，16强...球队名单
| round   |       str      |   true   |[0,1,2,3,4,5] 第几轮球队名单, 0对应32强，1对应16强...
|   lang     |     str    |    true|语言，默认英语, 'en-us', 中文：'zh-cn'

| 输出参数      | 参数类型    | 参数说明 |
| ---           | ---         | --- |
|  en_name | str       | 球队英文名称
| cn_name| str| 球队中文名称
|icon| str| 球队图片
|id|int|球队 id
|group| str| 球队分组
|W_D_L| str | W=Win,D=Draw,L=Lose, 胜-平-负
|GD|str|Goal Difference, 总净胜球
|remark|str|分组次序
|Pts|str|积分

* 结果示例：
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
* [1. 查询世界杯比赛信息] 

* URL: BaseUrl + /api/query/world_cup/game/?round=0&lang=en-us


### 1. 查询比赛信息
* 方法: `GET`


| 输入参数      | 参数类型  | 必填  | 参数说明 |
| ---           | ---       | ---   | --- |
|round  | str|true|比赛轮次，默认是0，小组赛，第1轮是十六强，以此类推
|lang|str|rtue|默认是英文



| 输出参数      | 参数类型    | 参数说明 |
| ---           | ---         | --- |
|  id|int    | 比赛 id
|status|int|比赛状态,1：未开始，2：进行中，3：结束
|game_time|str|比赛开始时间 (utc)
|home_team_score|str|主队得分,比赛未开始是 ''
|away_team_score|str|客队得分
|remark|str|备注
|round|str|轮次
|home_team|obj|主队信息
|away_team|obj|客队信息
|name|str|球队名称
|icon|str|球队照片

* 结果示例：
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

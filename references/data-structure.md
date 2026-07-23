# TravelGuide 数据结构

生成攻略时使用此数据结构组织所有信息。

## 顶层结构

```
TravelGuide
├── meta: Meta
├── overview: string
├── days[]: DayPlan
├── accommodation[]: Accommodation
├── budget_table: BudgetTable
├── weather: WeatherInfo
├── transport_pass: TransportPass
├── visa: VisaInfo
├── customs: string[]
├── language[]: Phrase
├── emergency: EmergencyInfo
├── photo_spots[]: PhotoSpot
└── tips: string[]
```

## Meta

| 字段 | 类型 | 说明 |
|------|------|------|
| destination | string | 主要目的地城市/国家 |
| start_date | string | 出发日期 |
| end_date | string | 返回日期 |
| total_days | int | 总天数 |
| budget_type | enum | `economy` / `comfort` / `luxury` |
| budget_per_person | string | 人均预算金额（可选） |
| travelers | TravelerInfo | 出行人数详情 |
| interests | string[] | 兴趣偏好列表 |
| transport_pref | string | 交通偏好 |
| accommodation_pref | string | 住宿偏好 |
| dietary | string | 饮食要求 |
| notes | string | 其他需求 |

## TravelerInfo

| 字段 | 类型 | 说明 |
|------|------|------|
| total | int | 总人数 |
| adults | int | 成人人数 |
| children | int | 儿童人数 |
| elderly | int | 老人人数 |
| type | enum | `solo` / `couple` / `family` / `friends` |

## DayPlan

| 字段 | 类型 | 说明 |
|------|------|------|
| day_number | int | 第几天 |
| date | string | 日期 |
| theme | string | 当日主题（如"古都文化之旅"） |
| morning | ActivitySlot | 上午活动 |
| afternoon | ActivitySlot | 下午活动 |
| evening | ActivitySlot | 晚上活动 |
| free_time | string | 自由探索时间建议 |
| milestones[] | Milestone | 当日重大事件节点（3-6 个），按时间排序 |
| attractions[] | Attraction | 当日景点 |
| food[] | Food | 当日美食推荐 |
| transportation | string | 当日交通建议 |
| map_link | string | 当日路线地图短链接 |
| rainy_alternative | RainyPlan | 雨天备选方案 |

## ActivitySlot

| 字段 | 类型 | 说明 |
|------|------|------|
| time | string | 时间段（如"09:00-12:00"） |
| activity | string | 活动描述 |
| duration | string | 预估耗时 |
| notes | string | 备注 |

## Milestone

| 字段 | 类型 | 说明 |
|------|------|------|
| time | string | 具体时间（如"10:30"） |
| icon | string | emoji 图标（如 🎯 📸 🍜 🏛️ 🚇 🎪） |
| event | string | 事件名称（简短，如"观看换岗仪式"） |
| description | string | 详细说明（1 句） |
| notes | string | 实用提示（可选，如"建议提前 10 分钟占位"） |

## Attraction

| 字段 | 类型 | 说明 |
|------|------|------|
| name | string | 景点名称 |
| name_local | string | 当地语言名称 |
| description | string | 简介（1-2 句） |
| ticket | string | 门票价格 |
| hours | string | 开放时间 |
| duration | string | 建议游览时间 |
| tips | string | 游览提示 |
| image_query | string | 图片搜索关键词（英文） |

## Food

| 字段 | 类型 | 说明 |
|------|------|------|
| name | string | 菜品/餐厅名称 |
| restaurant_name | string | 具体餐厅名称（如"四季民福烤鸭店(故宫店)"） |
| type | enum | `restaurant` / `street_food` / `specialty` |
| description | string | 简介 |
| address | string | 餐厅地址 |
| price_per_person | string | 人均价格（如"¥120-150"） |
| dianping_rating | float | 大众点评评分（0-5.0） |
| review_count | string | 大众点评评论数（如"1.2万"） |
| must_try | string[] | 推荐菜品 |
| reservation | string | 预订提示（是否需要、如何预订） |
| image_query | string | 图片搜索关键词（英文） |

## RainyPlan

| 字段 | 类型 | 说明 |
|------|------|------|
| alternatives[] | string | 室内备选活动列表 |
| indoor_attractions[] | string | 室内景点推荐 |

## Accommodation

| 字段 | 类型 | 说明 |
|------|------|------|
| hotel_name | string | 具体酒店名称（如"北京王府井希尔顿"） |
| area | string | 推荐区域 |
| type | string | 住宿类型 |
| address | string | 酒店地址 |
| price_per_person | string | 人均价格/晚（如"¥300-500"） |
| dianping_rating | float | 大众点评评分（0-5.0） |
| review_count | string | 大众点评评论数（如"8500"） |
| pros | string | 优势 |
| image_query | string | 图片搜索关键词 |

## BudgetTable

| 字段 | 类型 | 说明 |
|------|------|------|
| transportation | string | 交通预算 |
| accommodation | string | 住宿预算 |
| food | string | 餐饮预算 |
| tickets | string | 门票预算 |
| shopping | string | 购物预算 |
| other | string | 其他预算 |
| total | string | 总预算 |

## WeatherInfo

| 字段 | 类型 | 说明 |
|------|------|------|
| trend | string | 出行期间天气趋势 |
| temperature | string | 温度范围 |
| clothing | string | 穿衣建议 |
| source_type | enum | `realtime` / `reference` |

## TransportPass

| 字段 | 类型 | 说明 |
|------|------|------|
| name | string | 交通卡/通票名称 |
| coverage | string | 适用范围 |
| price | string | 价格 |
| where_to_buy | string | 购买地点 |
| worth_it | string | 是否值得购买的建议 |

## VisaInfo

| 字段 | 类型 | 说明 |
|------|------|------|
| type | string | 签证类型 |
| process | string | 办理方式 |
| materials | string[] | 所需材料 |
| duration | string | 办理时间 |
| notes | string | 注意事项 |

## Phrase

| 字段 | 类型 | 说明 |
|------|------|------|
| chinese | string | 中文含义 |
| local | string | 当地语言 |
| pronunciation | string | 发音（中文近似） |

## EmergencyInfo

| 字段 | 类型 | 说明 |
|------|------|------|
| police | string | 报警电话 |
| ambulance | string | 急救电话 |
| embassy | ContactInfo | 大使馆信息 |

## ContactInfo

| 字段 | 类型 | 说明 |
|------|------|------|
| phone | string | 电话 |
| address | string | 地址 |

## PhotoSpot

| 字段 | 类型 | 说明 |
|------|------|------|
| name | string | 拍照地点 |
| best_time | string | 最佳拍摄时间 |
| tip | string | 拍摄建议 |
| image_query | string | 图片搜索关键词 |

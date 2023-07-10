# REST API Documentation

### App
[GET app/locales](#get-app-locales)  

### Space
[GET space/list](#get-space-list)  
[GET space/:id](#get-space)  

### Category
[GET category/list](#get-category-list)  

### Location
[GET location/list](#get-location-list)  
[GET location/:id](#get-location)  

### Program
[GET program/list](#get-program-list)  
[GET program/timeline](#get-program-timeline)  
[GET program/:id](#get-program)  

### Public Transport
[GET public-transport/list](#get-public-transport-list)  

### Sound Walk
GET sound-walk/:id


## Requests

Request an `Api-Key` from info@muva-app.ch and include it in the request header of every API call.

```
curl -H "Api-Key:xxxxxx" https://api.muva-app.ch/v1/...
```

## Responses

All responses will contain one if these status codes in the response header and in the json response:
- 200 = Ok
- 400 = Bad Request
- 401 = Unauthorized
- 403 = Forbidden
- 404 = Not Found

If successful, the status code `200` will be returned.



## <a name="get-app-locales"></a>GET app/locales  

### Description

Get all strings that are used in the app in the available languages. Use it to translate the user interface into the user's language.

### Headers

| Header                 | Type     | Description    	       |                                |
|:-----------------------|:---------|:-------------------------|:-------------------------------|
| Api-Key                | string   | Unique API key           | Required                       |


### Parameters

| Parameter      |Type     |Description                                                          |                |
|:---------------|:--------|:--------------------------------------------------------------------|:---------------|
| lang           |string   |language code: `de`, `fr`, `it`, `rm` or `en`, default = `de`        |optional        |


### Example Request

```
curl -H "Api-Key:xxxxxx" https://api.muva-app.ch/v1/app/messages
```

### Example Response
```
{
    "status": 200,
    "result": {
    	"Overview": "Übersicht",
    	"Bookmarks": "Merkzettel",
    	"Bookmark": "Merken",
    	"Bookmarked": "Gemerkt",
    	"Share": "Teilen",
    	"Filter": "Filter",
    	"Apply filters": "Filter anwenden",
    	"Location": "Location",
        "Category": "Kategorie",
    	"Time / Date": "Zeit / Datum",
    	"View": "Ansicht",
    	"Info": "Info",
    	"Event info": "Event Info",
    	"Event program": "Event Programm",
    	"Program list": "Programm Liste",
    	"Program map": "Programm Karte",
    	"Program schedule": "Programm Zeitplan",
    	"To the program": "Zum Programm",
        "Listen": "Anhören",
        "Contact": "Kontakt"
    }
}
```

### Response Remarks

The key is always in English and serves as an identifier for the corresponding string.

## <a name="get-space-list"></a>GET space/list  

### Description

MUVA is organized by spaces. Spaces are virtual exhibition spaces within the MUVA App. It can be an physical event or a virtual Tour (or any kind of other virtual space type in the future).

### Headers

| Header                 | Type     | Description    	       |                                |
|:-----------------------|:---------|:-------------------------|:-------------------------------|
| Api-Key                | string   | Unique API key           | Required                       |


### Parameters

| Parameter      |Type     |Description                                                                                              |                |
|:---------------|:--------|:--------------------------------------------------------------------------------------------------------|:---------------|
| detailed       |boolean  |`1` or `0` whether a detailed result is required (as in [GET space/:id](#get-space)), default = `0`      |Optional        |
| imgSize        |string   |`small`, `medium` or `large`, default = `small`                                                          |Optional        |


### Example Request

```
curl -H "Api-Key:xxxxxx" https://api.muva-app.ch/v1/space/list
```

### Example Response
```
{
    "status": 200,
    "result": [
        {
            "id": 1,
            "color": "#BE6CFC",
            "type": "event",
            "label": "Event",
            "name": "Langer Samstag",
            "city": "Chur",
            "intro": "Lorem ipsum dolor sit amet.",
            "description": "Lorem ipsum dolor sit amet, consectetur adipiscing elit...",
            "img": "https://api.muva-app.ch/img/space/600/langer-samstag.jpg",
            "status": "active",
            "startDate": "2023-11-11",
            "endDate": "2023-11-11",
            "languages": ["de"]
        },
        {
            "id": 2,
            "color": "#6BC1EE",
            "type": "soundwalk",
            "label": "SoundWalk",
            "name": "Türme by Luca Sisera",
            "city": "Chur",
            "intro": "Lorem ipsum dolor sit amet.",
            "description": "Lorem ipsum dolor sit amet, consectetur adipiscing elit...",
            "img": "https://api.muva-app.ch/img/space/600/sound-walk.jpg",
            "status": "active",
            "startDate": "2023-11-11",
            "endDate": "2024-03-31",
            "languages": ["de", "rm"]
        },
        {
            "id": 3,
            "color": "#40BD5F",
            "type": "event",
            "label": "Event",
            "name": "Street Art Festival",
            "city": "Chur",
            "intro": "Lorem ipsum dolor sit amet.",
            "description": "Lorem ipsum dolor sit amet, consectetur adipiscing elit...",
            "img": "https://api.muva-app.ch/img/space/600/street-art-festival.jpg",
            "status": "preview",
            "startDate": "2023-11-11",
            "endDate": "2024-03-31",
            "languages": ["de"]
        }
    ]
}
```

### Response Remarks

| Parameter      |Type     |Description                                                                      |
|:---------------|:--------|:--------------------------------------------------------------------------------|
| type           |string   |`event` or `soundwalk` (will be extended in the future if necessary)             |
| status         |string   |`preview`, `active` or `legacy`                                                  |
| languages      |array    |Available content languages                                                      |


## <a name="get-space"></a>GET space/:id

### Example Request

Get space infos by space ID.


### Headers

| Header                 |Type     |Description    	         |                                |
|:-----------------------|:--------|:------------------------|:-------------------------------|
| Api-Key                |string   |Unique API key           |Required                        |

### Parameters

| Parameter      |Type     |Description                                                                 |                |
|:---------------|:--------|:---------------------------------------------------------------------------|:---------------|
| id             |integer   |ID of space                                                                |Required        |
| lang           |string   |language code, default = `de`                                               |Optional        |
| imgSize        |string   |`small`, `medium` or `large`, default = `large`                             |Optional        |

### Example Request

```
curl -H "Api-Key:xxxxxx" https://api.muva-app.ch/v1/space/1
```

### Example Response
```
{
    "status": 200,
    "result": {
		"id": 1,
		"color": "#BE6CFC",
		"type": "event",
		"label": "Event",
		"name": "Langer Samstag",
		"city": "Chur",
		"intro": "Lorem ipsum dolor sit amet.",
		"description": "Lorem ipsum dolor sit amet, consectetur adipiscing elit...",
		"img": "https://api.muva-app.ch/img/space/1600/langer-samstag.jpg",
		"status": "active",
		"startDate": "2023-11-11",
		"endDate": "2023-11-11",
		"languages": ["de"],
		 "audios": [
            {
                "name": "Test Audio File 1",
                "description": "Lorem Ipsum...",
                "url": "https://api.muva-app.ch/audio/space/langer-samstag.mp3"
            },
            {
                "name": "Test Audio File 2",
                "description": "Lorem Ipsum...",
                "url": "https://api.muva-app.ch/audio/space/langer-samstag-2.mp3"
            }
        ],
        "videos": [
            {
                "name": "Test Video File",
                "description": "Lorem Ipsum...",
                "url": "https://api.muva-app.ch/video/space/langer-samstag.mp3"
            }
        ],
		"links": {
			"info": {
				"url": "https://langersamstag.ch/",
				"text": "langersamstag.ch"
			},
			"tickets": {
				"url": "https://langersamstag.ch/informationen/tickets/",
				"text": "Tickets"
			}
		}
	}
}
```

### Response Remarks

| Parameter      |Type     |Description                                                                      |
|:---------------|:--------|:--------------------------------------------------------------------------------|
| type           |string   |`event` or `soundwalk` (will be extended in the future if necessary)             |
| status         |string   |`preview`, `active` or `legacy`                                                  |
| languages      |array    |Available content languages                                                      |


## <a name="get-category-list"></a>GET category/list  

### Description

Get a list of all categories of a space.

### Headers

| Header                 | Type     | Description    	       |                                |
|:-----------------------|:---------|:-------------------------|:-------------------------------|
| Api-Key                | string   | Unique API key           | Required                       |


### Parameters

| Parameter      |Type     |Description                        |                |
|:---------------|:--------|:----------------------------------|:---------------|
| spaceId        |integer  |ID of space                        |Required        |
| lang           |string   |language code, default = `de`      |Optional        |


### Example Request

```
curl -H "Api-Key:xxxxxx" https://api.muva-app.ch/v1/category/list?spaceId=1
```

### Example Response
```
{
    "status": 200,
    "result": [
        {
            "id": 1,
            "name": "Theater",
            "icon": "https://api.muva-app.ch/icon/stage.svg"
        },
        {
            "id": 2,
            "name": "Tanz",
            "icon": "https://api.muva-app.ch/icon/exhibit.svg"
        },
        {
            "id": 3,
            "name": "Ausstellung",
            "icon": "https://api.muva-app.ch/icon/canvas.svg"
        },
        {
            "id": 4,
            "name": "Literatur",
            "icon": "https://api.muva-app.ch/icon/book.svg"
        },
        {
            "id": 5,
            "name": "Musik",
            "icon": "https://api.muva-app.ch/icon/music.svg"
        }
    ]
}
```

### Response Remarks

| Parameter      |Type     |Description                          |
|:---------------|:--------|:------------------------------------|
| icon           |string   |URL to SVG icon                      |


## <a name="get-location-list"></a>GET location/list  

Get a list of all locations of a space.

### Headers

| Header                 | Type     | Description    	       |                                |
|:-----------------------|:---------|:-------------------------|:-------------------------------|
| Api-Key                | string   | Unique API key           | Required                       |


### Parameters

| Parameter      |Type     |Description                                                                                                    |                |
|:---------------|:--------|:--------------------------------------------------------------------------------------------------------------|:---------------|
| spaceId        |integer  |ID of space                                                                                                    |Required        |
| lang           |string   |language code, default = `de`                                                                                  |Optional        |
| detailed       |boolean  |`1` or `0` whether a detailed result is required (as in [GET location/:id](#get-location)), default = `0`      |Optional        |


### Example Request

```
curl -H "Api-Key:xxxxxx" https://api.muva-app.ch/v1/location/list?spaceId=1
```

### Example Response
```
{
    "status": 200,
    "result": [
        {
            "id": 1,
            "name": "Bündner Kunstmuseum"
        },
        {
            "id": 2,
            "name": "Bündner Naturmuseum"
        },
        {
            "id": 3,
            "name": "Chur Tourismus"
        },
        {
            "id": 4,
            "name": "CUADRO22"
        }
    ]
}
```

## <a name="get-location"></a>GET location/:id

### Example Request

Get location infos by location ID.


### Headers

| Header                 |Type     |Description    	         |                                |
|:-----------------------|:--------|:------------------------|:-------------------------------|
| Api-Key                |string   |Unique API key           |Required                        |

### Parameters

| Parameter      |Type     |Description                                                                 |                |
|:---------------|:--------|:---------------------------------------------------------------------------|:---------------|
| id             |integer  |ID of location                                                              |Required        |
| lang           |string   |language code, default = `de`                                               |Optional        |
| imgSize        |string   |`small`, `medium` or `large`, default = `medium`                            |Optional        |

### Example Request

```
curl -H "Api-Key:xxxxxx" https://api.muva-app.ch/v1/location/1
```

### Example Response
```
{
    "status": 200,
    "result": {
		"id": 1,
		"name": "Bündner Kunstmuseum",
		"description": "Lorem ipsum dolor sit amet, consectetur adipiscing elit...",
		"img": "https://api.muva-app.ch/img/space/1200/langer-samstag.jpg",
		"street": "Bahnhofstrasse",
		"streetNumber": "35",
		"addressAddition": false,
		"postalCode": 7000,
		"city": "Chur",
		"email": false,
		"phone": "+41 81 257 28 70",
		"coordinates": [46.851348, 9.532254],
		"gastro": {
			"description": "Lorem ipsum dolor sit amet, consectetur adipiscing elit...",
			"timetableInfo": "14.00 bis 17.00 Uhr"
		},
		"links": {
			"info": {
				"url": "https://buendner-kunstmuseum.ch/",
				"text": "buendner-kunstmuseum.ch"
			},
			"googleMaps": {
				"url": "https://goo.gl/maps/ru5B57LoVCTorLQW8",
				"text": "Google Maps"
			}
		}
	}
}
```

### Response Remarks

| Parameter          |Type     |Description                                                                                |
|:-------------------|:--------|:------------------------------------------------------------------------------------------|
| links.googleMaps   |obj      |Link to Google Maps (useful for directions feature in GoogleMaps)                          |


## <a name="get-program-list"></a>GET program/list  

### Description

Get a program list of an space.

### Headers

| Header                 | Type     | Description    	       |                                |
|:-----------------------|:---------|:-------------------------|:-------------------------------|
| Api-Key                | string   | Unique API key           | Required                       |


### Parameters

| Parameter          |Type     |Description                                                                                                    |                |
|:-------------------|:--------|:--------------------------------------------------------------------------------------------------------------|:---------------|
| spaceId            |integer  |ID of space                                                                                                    |Required        |
| categoryIds        |csv      |Comma-separated list of category IDs                                                                           |Optional        |
| locationIds        |csv      |Comma-separated list of location IDs                                                                           |Optional        |
| forKids            |boolean  |`1` or `0` whether a program is for kids, default = `0`                                                        |Optional        |
| start              |integer  |Unix timestamp, start time >= than this value.                                                                 |Optional        |
| end                |string   |Unix timestamp, start time <= than this value.                                                                 |Optional        |
| lang               |string   |language code, default = `de`                                                                                  |Optional        |
| detailed           |boolean  |`1` or `0` whether a detailed result is required (as in [GET program/:id](#get-program)), default = `0`        |Optional        |
| imgSize            |string   |`small`, `medium` or `large`, default = `small`                                                                |Optional        |

### Example Request

```
curl -H "Api-Key:xxxxxx" https://api.muva-app.ch/v1/program/list?spaceId=1
```

### Example Response
```
{
    "status": 200,
    "result": [
        {
            "id": 1,
            "programGuideId": 12,
            "name": "Bündnerland, allerhand – Museumstour mal anders",
            "icon": "https://api.muva-app.ch/icon/tour.svg",
            "img": "https://api.muva-app.ch/img/space/600/museumstour.jpg",
            "startDate": "2023-11-11",
            "endDate": "2023-11-11",
            "timetableInfo": "13.00, 17.00, 19.00 Uhr",
            "duration": "30 Min.",
            "category": "Musik",
            "location": {
				"id": 1,
				"name": "Bündner Kunstmuseum",
				"city": "Chur",
				"coordinates": [46.851348, 9.532254]
			}
        },
        {
            "id": 1,
            "programGuideId": 14,
            "name": "Stumm und Kurz für Kids ",
            "icon": "https://api.muva-app.ch/icon/film.svg",
            "img": "https://api.muva-app.ch/img/space/600/stumm.jpg",
           	"startDate": "2023-11-11",
			"endDate": "2023-11-11",
            "timetableInfo": "13.00, 17.00, 19.00 Uhr",
            "duration": "30 Min.",
            "category": "Film",
            "location": {
				"id": 10,
				"name": "Klibühni, Das Theater",
				"city": "Chur",
				"coordinates": [46.851348, 9.532254]
			}
        }
    ]
}
```

### Response Remarks

| Parameter      |Type          |Description                                                                                  |
|:---------------|:-------------|:--------------------------------------------------------------------------------------------|
| programGuideId |integer       |ID shown in the program guide of the event (`false` if no program guide)                     |


## <a name="get-program-timeline"></a>GET program/timeline  

### Description

Get a program list of a space.

### Headers

| Header                 | Type     | Description    	       |                                |
|:-----------------------|:---------|:-------------------------|:-------------------------------|
| Api-Key                | string   | Unique API key           | Required                       |


### Parameters

| Parameter          |Type     |Description                                                                                                    |                |
|:-------------------|:--------|:--------------------------------------------------------------------------------------------------------------|:---------------|
| spaceId            |integer  |ID of space                                                                                                    |Required        |
| categoryIds        |csv      |Comma-separated list of category IDs                                                                           |Optional        |
| locationIds        |csv      |Comma-separated list of location IDs                                                                           |Optional        |
| forKids            |boolean  |`1` or `0` whether a program is for kids, default = `0`                                                        |Optional        |
| start              |integer  |Unix timestamp, start time >= than this value.                                                                 |Optional        |
| end                |string   |Unix timestamp, start time <= than this value.                                                                 |Optional        |
| lang               |string   |language code, default = `de`                                                                                  |Optional        |

### Example Request

```
curl -H "Api-Key:xxxxxx" https://api.muva-app.ch/v1/program/timeline?spaceId=1
```

### Example Response
```
{
    "status": 200,
    "result": [
        {
        	"location": {
				"id": 1,
				"name": "Bündner Kunstmuseum",
				"city": "Chur"
			},
			"program": [
				{
					"id": 1,
					"programGuideId": 12,
					"name": "Bündnerland, allerhand – Museumstour mal anders",
					"icon": "https://api.muva-app.ch/icon/tour.svg",
					"start": "2023-11-11T13:00:00+01:00",
					"end": "2023-11-11T13:30:00+01:00"				
				},
				{
					"id": 2,
					"programGuideId": 15,
					"name": "Stick mit! Tauche ein in die Welt der Stickerei!",
					"icon": "https://api.muva-app.ch/icon/workshop.svg",
					"start": "2023-11-11T13:30:00+01:00",
					"end": "2023-11-11T14:00:00+01:00"				
				},
				{
					"id": 3,
					"programGuideId": 16,
					"name": "Ausstellung «Venedigsche Sterne. Kunst und Stickerei»",
					"icon": "https://api.muva-app.ch/icon/fuehrung.svg",
					"start": "2023-11-11T14:30:00+01:00",
					"end": "2023-11-11T15:00:00+01:00"				
				}
			]
        },
        {
        	"location": {
				"id": 10,
				"name": "Klibühni, Das Theater",
				"city": "Chur"
			},
			"program": [
				{
					"id": 4,
					"programGuideId": 13,
					"name": "Stumm und Kurz für Kids ",
					"icon": "https://api.muva-app.ch/icon/workshop.svg",
					"start": "2023-11-11T12:00:00+01:00",
					"end": "2023-11-11T12:30:00+01:00"				
				},
				{
					"id": 5,
					"programGuideId": 20,
					"name": "Stumm und Kurz",
					"icon": "https://api.muva-app.ch/icon/workshop.svg",
					"start": "2023-11-11T13:00:00+01:00",
					"end": "2023-11-11T13:30:00+01:00"				
				},
				{
					"id": 4,
					"programGuideId": 21,
					"name": "Stumm und Kurz für Kids ",
					"icon": "https://api.muva-app.ch/icon/workshop.svg",
					"start": "2023-11-11T16:00:00+01:00",
					"end": "2023-11-11T16:30:00+01:00"				
				},
				{
					"id": 5,
					"programGuideId": 22,
					"name": "Stumm und Kurz",
					"icon": "https://api.muva-app.ch/icon/workshop.svg",
					"start": "2023-11-11 17:00:00+01:00",
					"end": "2023-11-11 17:30:00+01:00"				
				}
			]
        }
    ]
}
```

### Response Remarks

| Parameter      |Type          |Description                                                                                  |
|:---------------|:-------------|:--------------------------------------------------------------------------------------------|
| programGuideId |integer       |ID shown in the program guide of the event (`false` if no program guide)                     |
| program.start  |string        |ISO 8601 Date and time format incl. time zone offset. Let discuss: Better Unix timestamp?    |
| program.end    |string        |ISO 8601 Date and time format incl. time zone offset. Let discuss: Better Unix timestamp?    |


## <a name="get-program"></a>GET program/:id

### Example Request

Get program infos by program ID.


### Headers

| Header                 |Type     |Description    	         |                                |
|:-----------------------|:--------|:------------------------|:-------------------------------|
| Api-Key                |string   |Unique API key           |Required                        |

### Parameters

| Parameter      |Type     |Description                                                                 |                |
|:---------------|:--------|:---------------------------------------------------------------------------|:---------------|
| id             |integer  |ID of program                                                               |Required        |
| lang           |string   |language code, default = `de`                                               |Optional        |
| imgSize        |string   |`small`, `medium` or `large`, default = `large`                             |Optional        |

### Example Request

```
curl -H "Api-Key:xxxxxx" https://api.muva-app.ch/v1/program/1
```

### Example Response
```
{
    "status": 200,
    "result": {
		"id": 1,
		"programGuideId": 12,
		"name": "Bündnerland, allerhand – Museumstour mal anders",
		"description": "Lorem ipsum dolor sit amet, consectetur adipiscing elit...",
		"icon": "https://api.muva-app.ch/icon/tour.svg",
		"img": "https://api.muva-app.ch/img/space/1600/museumstour.jpg",
		"startDate": "2023-11-11",
		"endDate": "2023-11-11",
		"timetableInfo": "13.00, 17.00, 19.00 Uhr",
		"duration": "30 Min.",
		"category": "Musik",
		"location": {
            "id": 1,
            "name": "Bündner Kunstmuseum",
            "description": "Lorem ipsum dolor sit amet, consectetur adipiscing elit...",
            "img": "https://api.muva-app.ch/img/test.jpg",
            "street": "Bahnhofstrasse",
            "streetNumber": "35",
            "addressAddition": false,
            "postalCode": 7000,
            "city": "Chur",
            "email": false,
            "phone": "+41 81 257 28 70",
            "coordinates": [
                46.851348,
                9.532254
            ],
            "gastro": {
                "description": "Lorem ipsum dolor sit amet, consectetur adipiscing elit...",
                "timetableInfo": "14.00 bis 17.00 Uhr"
            },
            "links": {
                "info": {
                    "url": "https://buendner-kunstmuseum.ch/",
                    "text": "buendner-kunstmuseum.ch"
                },
                "googleMaps": {
                    "url": "https://goo.gl/maps/ru5B57LoVCTorLQW8",
                    "text": "Google Maps"
                }
            }
        },
		"categories": [
			{
				"id": 1,
				"name": "Musik",
				"main": true
			},
			{
				"id": 2,
				"name": "Gesang",
				"main": false
			}
		],
		 "audios": [
            {
                "name": "Test Audio File 1",
                "description": "Lorem Ipsum...",
                "url": "https://api.muva-app.ch/audio/program/test.mp3"
            },
            {
                "name": "Test Audio File 2",
                "description": "Lorem Ipsum...",
                "url": "https://api.muva-app.ch/audio/program/test-2.mp3"
            }
        ],
        "videos": false,
		"links": {
			"info": [
				{
					"url": "https://buendner-kunstmuseum.ch/",
					"text": "buendner-kunstmuseum.ch"
				},
				{
					"url": "https://kuenstlerin.ch/",
					"text": "kuenstlerin.ch"
				}
			],
			"tickets": false
		}
	}
}
```

### Response Remarks

| Parameter      |Type     |Description                                                                |
|:---------------|:--------|:--------------------------------------------------------------------------|
| programGuideId |integer  |ID shown in the program guide of the event (`false` if no program guide)   |
| links.info     |obj      |Multiple info links possible (for example, if there are multiple artists)  |



## <a name="get-public-transport-list"></a>GET public-transport/list  

### Description

Get a list of public transport stops of a space.

### Headers

| Header                 | Type     | Description    	       |                                |
|:-----------------------|:---------|:-------------------------|:-------------------------------|
| Api-Key                | string   | Unique API key           | Required                       |


### Parameters

| Parameter      |Type     |Description                        |                |
|:---------------|:--------|:----------------------------------|:---------------|
| spaceId        |integer  |ID of space                        |Required        |
| lang           |string   |language code, default = `de`      |Optional        |


### Example Request

```
curl -H "Api-Key:xxxxxx" https://api.muva-app.ch/v1/public-transport/list?spaceId=1
```

### Example Response
```
{
    "status": 200,
    "result": [
        {
            "id": 1,
            "name": "Alexanderplatz",
            "icon": "https://api.muva-app.ch/icon/bus.svg",
            "timetableInfo": "11.32 / .47 / .02 / .17 / 00.32 Uhr",
            "coordinates": [46.851348, 9.532254],
            "links": {
				"sbb": false,
				"googleMaps": {
					"url": "https://goo.gl/maps/ru5B57LoVCTorLQW8",
					"text": "Google Maps"
				}
			}
		},
        {
            "id": 2,
            "name": "Bahnhofplatz",
            "icon": "https://api.muva-app.ch/icon/bus.svg",
            "timetableInfo": "11.30 / .45 / .00 / .15 / 00.30 Uhr",
            "coordinates": [46.851348, 9.532254],
            "links": {
				"sbb": {
					"url": "https://www.sbb.ch/de/kaufen/pages/fahrplan/fahrplan.xhtml?nach=Bahnhofplatz%20Chur",
					"text": "SBB"
				},
				"googleMaps": {
					"url": "https://goo.gl/maps/ru5B57LoVCTorLQW8",
					"text": "Google Maps"
				}
			}
		}
    ]
}
```

### Response Remarks

| Parameter          |Type     |Description                                                                                |
|:-------------------|:--------|:------------------------------------------------------------------------------------------|
| icon               |string   |URL to SVG icon                                                                            |
| links.sbb          |obj      |Link to SBB timetable (not in use for Langer Samstag, but may be useful in the future)     |
| links.googleMaps   |obj      |Link to Google Maps (useful for directions feature in GoogleMaps in the future)            |

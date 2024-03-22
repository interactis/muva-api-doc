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

### Artist
[GET artist/list](#get-artist-list)  
[GET artist/:id](#get-artist)  

### Gastro
[GET gastro/list](#get-gastro-list)  
[GET gastro/:id](#get-gastro)  

### Public Transport
[GET public-transport/list](#get-public-transport-list)  

### Soundwalk
[GET soundwalk](#get-soundwalk) 

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
| lang           |string   |language code: `de`, `fr`, `it`, `rg` or `en`, default = `de`        |optional        |


### Example Request

```
curl -H "Api-Key:xxxxxx" https://api.muva-app.ch/v1/app/messages
```

### Example Response
```
{
    "status": 200,
    "result": {
        "Start": "Start",
        "Home": "Home",
        "Overview": "Übersicht",
        "Bookmarks": "Merkzettel",
        "Bookmark": "Merken",
        "Bookmarked": "Gemerkt",
        "Share": "Teilen",
        "Filter": "Filter",
        "Locations": "Häuser",
        "Location": "Haus",
        "Categories": "Kategorien",
        "Category": "Kategorie",
        "Time": "Zeit",
        "Date": "Datum",
        "Time / Date": "Zeit / Datum",
        "View": "Ansicht",
        "List": "Liste",
        "Map": "Karte",
        "Schedule": "Zeitplan",
        "Info": "Info",
        "Event info": "Event Info",
        "Event details": "Event Programm",
        "Program list": "Programm Liste",
        "Program map": "Programm Karte",
        "Program schedule": "Programm Zeitplan",
        "Go to program": "Zum Programm",
        "Listen": "Anhören",
        "Contact": "Kontakt",
        "For kids": "Für Kinder",
        "Please go to the starting point": "Bitte begebe dich zum Startpunkt",
        "Back": "Zurück",
        "Starts in": "Start in",
        "days": "Tagen",
        "day": "Tag",
        "hrs.": "Std.",
        "hr": "Std.",
        "mins.": "Min.",
        "min.": "Min.",
        "secs.": "Sek.",
        "sec.": "Sek.",
        "Image": "Bild",
        "Video": "Video",
        "Audio": "Audio",
        "Clear filters": "Filter zurücksetzen",
        "Gastro": "Gastro"
    }
}
```

### Response Remarks

The key is always in English and serves as an identifier for the corresponding string.

## <a name="get-space-list"></a>GET space/list  

### Description

MUVA is organized by spaces. Spaces are virtual exhibition spaces within the MUVA App. It can be a physical event or a virtual tour (or any kind of other virtual space type in the future).

### Headers

| Header                 | Type     | Description    	       |                                |
|:-----------------------|:---------|:-------------------------|:-------------------------------|
| Api-Key                | string   | Unique API key           | Required                       |


### Parameters

| Parameter      |Type     |Description                                                                                              |                |
|:---------------|:--------|:--------------------------------------------------------------------------------------------------------|:---------------|
| detailed       |boolean  |`1` or `0` whether a detailed result is required (as in [GET space/:id](#get-space)), default = `0`      |Optional        |
| imgSize        |string   |`small`, `medium`, `large` or `xlarge`, default = `small`                                                |Optional        |
| lang           |string   |language code, default = `de`                                                                            |Optional        |


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
            "latestVersion": 29,
            "color": "#BF66FF",
            "type": "event",
            "label": "Event",
            "name": "Langer Samstag",
            "city": "Chur",
            "intro": "Lorem ipsum  dolor sit amet, consectetur adipiscing elit, sed do eiusmoddamet, consec, sed do eiusmoddolor sit amet",
            "description": "Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.",
            "img": "https://staging-api.muva-app.ch/img/space/crop/500/_test-img.jpg",
            "status": "preview",
            "fromToDate": "11.11.2023",
            "startDate": "2023-11-11",
            "startTime": 1699700400,
            "endDate": "2023-11-12",
            "endTime": 1699754400,
            "languages": [
                "de"
            ],
            "sponsor": {
                "logo": "https://staging-api.muva-app.ch/img/space/sponsor/1.svg",
                "logoWidth": 180,
            	"logoHeight": 50,
                "text": "Presented by"
            },
            "showTimeSlider": true,
            "showMap": true,
            "showCategories": true,
            "showLocations": true,
            "showKidsFilter": true
        },
        {
            "id": 2,
            "latestVersion": 29,
            "color": "#39BF5B",
            "type": "soundwalk",
            "label": "SoundWalk",
            "name": "Türmer von Luca Sisera",
            "city": "Chur",
            "intro": "Lorem ipsum dolor sit amet. Lorem ipsum dolor sit amet, consectetur adipiscing elit.",
            "description": "Lorem ipsum dolor sit amet. Lorem ipsum dolor sit amet, consectetur adipiscing elit. Lorem ipsum dolor sit amet. Lorem ipsum dolor sit amet, consectetur adipiscing elit.",
            "img": "https://staging-api.muva-app.ch/img/placeholder/500/placeholder.jpg",
            "status": "preview",
            "fromToDate": "11.11.2023 - 31.01.2024",
            "startDate": "2023-11-11",
            "startTime": 1699698600,
            "endDate": "2024-01-31",
            "endTime": 1706741940,
            "languages": [
                "de"
            ],
            "sponsor": {
                "logo": "https://staging-api.muva-app.ch/img/space/sponsor/2.svg",
                "logoWidth": 0,
            	"logoHeight": 0,
                "text": "Presented by"
            },
            "showTimeSlider": false,
            "showMap": false,
            "showCategories": false,
            "showLocations": false,
            "showKidsFilter": false
        },
        {
            "id": 3,
            "latestVersion": 29,
            "color": "#FFA826",
            "type": "audio",
            "label": "Audio",
            "name": "Türmer: Historischer Hintergrund",
            "city": "",
            "intro": "Lorem ipsum dolor sit amet, consectetur adipiscing elit. Lorem ipsum dolor sit amet, consectetur adipiscing elit.",
            "description": "Lorem ipsum dolor sit amet, consectetur adipiscing elit. Lorem ipsum dolor sit amet, consectetur adipiscing elit. Lorem ipsum dolor sit amet, consectetur adipiscing elit. Lorem ipsum dolor sit amet, consectetur adipiscing elit.",
            "img": "https://staging-api.muva-app.ch/img/placeholder/500/placeholder.jpg",
            "status": "active",
            "fromToDate": "23.10.2023 - 31.01.2024",
            "startDate": "2023-10-23",
            "startTime": 1698033600,
            "endDate": "2024-01-31",
            "endTime": 1706741940,
            "languages": [
                "de",
                "fr",
                "it",
                "rg",
                "en"
            ],
            "sponsor": {
                "logo": "https://staging-api.muva-app.ch/img/space/sponsor/3.svg",
                "logoWidth": 0,
            	"logoHeight": 0,
                "text": "Presented by"
            },
            "showTimeSlider": false,
            "showMap": false,
            "showCategories": false,
            "showLocations": false,
            "showKidsFilter": false
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
| id             |integer  |ID of space                                                                 |Required        |
| lang           |string   |language code, default = `de`                                               |Optional        |
| imgSize        |string   |`small`, `medium`, `large` or `xlarge`, default = `large`                   |Optional        |

### Example Request

```
curl -H "Api-Key:xxxxxx" https://api.muva-app.ch/v1/space/1
```

### Example Response
```
{
    "status": 200,
    "result": {
        "id": 3,
        "latestVersion": 29,
        "color": "#FFA826",
        "type": "audio",
        "label": "Audio",
        "name": "Türmer: Historischer Hintergrund",
        "city": "",
        "intro": "Lorem ipsum dolor sit amet, consectetur adipiscing elit. Lorem ipsum dolor sit amet, consectetur adipiscing elit.",
        "description": "Lorem ipsum dolor sit amet, consectetur adipiscing elit. Lorem ipsum dolor sit amet, consectetur adipiscing elit. Lorem ipsum dolor sit amet, consectetur adipiscing elit. Lorem ipsum dolor sit amet, consectetur adipiscing elit.",
        "img": "https://staging-api.muva-app.ch/img/placeholder/1400/placeholder.jpg",
        "status": "active",
        "fromToDate": "23.10.2023 - 31.01.2024",
        "startDate": "2023-10-23",
        "startTime": 1698033600,
        "endDate": "2024-01-31",
        "endTime": 1706741940,
        "languages": [
            "de",
            "fr",
            "it",
            "rg",
            "en"
        ],
        "sponsor": {
            "logo": "https://staging-api.muva-app.ch/img/space/sponsor/3.svg",
            "logoWidth": 180,
            "logoHeight": 50,
            "text": "Presented by"
        },
        "showTimeSlider": false,
    	"showMap": false,
    	"showCategories": false,
        "showLocations": false,
    	"showKidsFilter": false,
        "center": [
            9.528257532,
            46.849757569
        ],
        "audios": [
            {
                "name": "Test 1 DE",
                "description": "Lorem ipsum dolor sit amet. Lorem ipsum dolor sit amet.",
                "url": "https://staging-api.muva-app.ch/audio/de/TestAudio.mp3"
            },
            {
                "name": "Test 2 DE",
                "description": "Lorem ipsum dolor sit amet. Lorem ipsum.",
                "url": "https://staging-api.muva-app.ch/audio/de/2-TestAudio.mp3"
            }
        ],
        "videos": [],
        "youtube": {
        	"url": "https://www.youtube.com/watch?v=2wH7JPtzvfE&t",
        	"thumb": "https://api.muva-app.ch/img/video/ratio/900/thumb-making-of.png"
        },
        "links": {
            "info": {},
            "tickets": {}
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
| startTime      |integer  |Unix timestamp                                                                   |
| endTime        |integer  |Unix timestamp                                                                   |
| center         |array    |Coordinates on which the map should be centered (if type `event`)                |

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
            "id": 4,
            "name": "Ausstellung",
            "icon": "https://staging-api.muva-app.ch/img/icons/Exhibition.svg"
        },
        {
            "id": 3,
            "name": "Comedy",
            "icon": "https://staging-api.muva-app.ch/img/icons/Comedy-1.svg"
        },
        {
            "id": 7,
            "name": "Film",
            "icon": "https://staging-api.muva-app.ch/img/icons/Film-1.svg"
        },
        {
            "id": 5,
            "name": "Führung",
            "icon": "https://staging-api.muva-app.ch/img/icons/Tourguide-2.svg"
        },
        {
            "id": 9,
            "name": "Literatur",
            "icon": "https://staging-api.muva-app.ch/img/icons/Literature-1.svg"
        },
        {
            "id": 11,
            "name": "Musik",
            "icon": "https://staging-api.muva-app.ch/img/icons/Music-1.svg"
        },
        {
            "id": 12,
            "name": "Performance",
            "icon": "https://staging-api.muva-app.ch/img/icons/Theater.svg"
        },
        {
            "id": 10,
            "name": "Poetry Slam",
            "icon": "https://staging-api.muva-app.ch/img/icons/Poetry-2.svg"
        },
        {
            "id": 2,
            "name": "Tanz",
            "icon": "https://staging-api.muva-app.ch/img/icons/Dancing-1.svg"
        },
        {
            "id": 1,
            "name": "Theater",
            "icon": "https://staging-api.muva-app.ch/img/icons/Theater.svg"
        },
        {
            "id": 6,
            "name": "Vortrag",
            "icon": "https://staging-api.muva-app.ch/img/icons/Presentation-2.svg"
        },
        {
            "id": 8,
            "name": "Workshop",
            "icon": "https://staging-api.muva-app.ch/img/icons/Workshop-1.svg"
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
| imgSize        |string   |`small`, `medium`, `large` or `xlarge`, default = `small`                                                      |Optional        |

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
            "id": 25,
            "name": "Rhätische Bahn",
            "city": "Chur",
            "coordinates": [
                9.530525184,
                46.853884904
            ]
        },
        {
            "id": 29,
            "name": "Street Art Festival Chur",
            "city": "",
            "coordinates": [
                9.530814015,
                46.851395999
            ]
        },
        {
            "id": 31,
            "name": "Werkstatt Chur",
            "city": "Chur",
            "coordinates": [
                9.530649194,
                46.84860886
            ]
        },
        {
            "id": 27,
            "name": "Kantonsbibliothek & Staatsarchiv Graubünden@Grossratsgebäude",
            "city": "Chur",
            "coordinates": [
                9.533844347,
                46.851792267
            ]
        },
        {
            "id": 9,
            "name": "Bündner Kunstmuseum",
            "city": "Chur",
            "coordinates": [
                9.532375932,
                46.851245771
            ]
        },
        {
            "id": 8,
            "name": "Ausstellung Urgeschichte",
            "city": "",
            "coordinates": [
                9.526069013,
                46.862610267
            ]
        },
        {
            "id": 23,
            "name": "Postremise",
            "city": "Chur",
            "coordinates": [
                9.52926394,
                46.849735585
            ]
        },
        {
            "id": 17,
            "name": "ibW Schule für Gestaltung Graubünden",
            "city": "Chur",
            "coordinates": [
                9.529642863,
                46.854989853
            ]
        },
        {
            "id": 13,
            "name": "Forum Würth Chur",
            "city": "Chur",
            "coordinates": [
                9.528769757,
                46.860103913
            ]
        },
        {
            "id": 19,
            "name": "JazzChur@Marsoel Saal",
            "city": "Chur",
            "coordinates": [
                9.533899582,
                46.848195404
            ]
        },
        {
            "id": 24,
            "name": "Rätisches Museum",
            "city": "Chur",
            "coordinates": [
                9.533483505,
                46.848099153
            ]
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
| imgSize        |string   |`small`, `medium`, `large` or `large`, default = `medium`                   |Optional        |

### Example Request

```
curl -H "Api-Key:xxxxxx" https://api.muva-app.ch/v1/location/1
```

### Example Response
```
{
    "status": 200,
    "result": {
        "id": 25,
        "name": "Rhätische Bahn",
        "description": "",
        "img": "https://staging-api.muva-app.ch/img/placeholder/900/placeholder.jpg",
        "street": "Arosa Gleisfeld am Bahnhof (Gleis 2)",
        "streetNumber": "",
        "addressAddition": "",
        "postalCode": "7000",
        "city": "Chur",
        "email": "",
        "phone": "",
        "coordinates": [
            9.530525184,
            46.853884904
        ],
        "remarks": "",
        "gastro": {},
        "links": {
            "info": {},
            "googleMaps": {
                "url": "https://goo.gl/maps/xUVAitGy1czeYjFa8",
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
| programIds         |csv      |Comma-separated list of program IDs                                                                            |Optional        |
| forKids            |boolean  |`1` or `0` whether a program is for kids, default = `0`                                                        |Optional        |
| start              |integer  |Unix timestamp, start time >= than this value.                                                                 |Optional        |
| end                |string   |Unix timestamp, start time <= than this value.                                                                 |Optional        |
| lang               |string   |language code, default = `de`                                                                                  |Optional        |
| detailed           |boolean  |`1` or `0` whether a detailed result is required (as in [GET program/:id](#get-program)), default = `0`        |Optional        |
| imgSize            |string   |`small`, `medium`, `large` or `xlarge`, default = `small`                                                      |Optional        |

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
            "id": 101,
            "programGuideId": 25,
            "name": "10 Jahre Fotostiftung Graubünden – Glanzlichter unserer Sammlung",
            "icon": "https://staging-api.muva-app.ch/img/icons/Exhibition.svg",
            "img": "https://staging-api.muva-app.ch/img/program/crop/500/FSGR_1156.jpg",
            "timetableInfo": "12:00, 12:30, 13:00, 13:30, 14:00, 14:30, 15:00, 15:30, 16:00, 16:30, 17:00, 17:30, 18:00, 18:30, 19:00, 19:30, 20:00, 20:30, 21:00, 21:30, 22:00, 22:30, 23:00, 23:30, 00:00, 00:30, 01:00, 01:30, 02:00, 02:30",
            "duration": "12 Std.",
            "categories": [
                "Ausstellung"
            ],
            "location": {
                "id": 14,
                "name": "Fotostiftung Graubünden",
                "city": "Chur",
                "coordinates": [
                    9.533576963,
                    46.850293567
                ]
            }
        },
        {
            "id": 75,
            "programGuideId": 26,
            "name": "1848: Eine Verfassung verändert die Schweiz",
            "icon": "https://staging-api.muva-app.ch/img/icons/Exhibition.svg",
            "img": "https://staging-api.muva-app.ch/img/program/crop/500/Gian-Rupf-Bundesverfassung.jpg",
            "timetableInfo": "15:30, 18:00, 20:00",
            "duration": "30 Min.",
            "categories": [
                "Ausstellung",
                "Literatur",
                "Poetry Slam"
            ],
            "location": {
                "id": 27,
                "name": "Kantonsbibliothek & Staatsarchiv Graubünden@Grossratsgebäude",
                "city": "Chur",
                "coordinates": [
                    9.533844347,
                    46.851792267
                ]
            }
        },
        {
            "id": 91,
            "programGuideId": null,
            "name": "Albin & Eisenschmid / Elektro-Pop aus der Surselva",
            "icon": "",
            "img": "https://staging-api.muva-app.ch/img/program/crop/500/Leander-Albin.jpg",
            "timetableInfo": "21:00, 22:00",
            "duration": "30 Min.",
            "categories": [
                "Musik"
            ],
            "location": {
                "id": 23,
                "name": "Postremise",
                "city": "Chur",
                "coordinates": [
                    9.52926394,
                    46.849735585
                ]
            }
        },
        {
            "id": 58,
            "programGuideId": null,
            "name": "Alte Filmschätze «Wildheuen in Graubünden»",
            "icon": "",
            "img": "https://staging-api.muva-app.ch/img/program/crop/500/AVGR11998_8.png",
            "timetableInfo": "13:30, 16:00, 19:00",
            "duration": "30 Min.",
            "categories": [
                "Film"
            ],
            "location": {
                "id": 20,
                "name": "Kantonsbibliothek & Staatsarchiv Graubünden",
                "city": "Chur",
                "coordinates": [
                    9.534081206,
                    46.849929826
                ]
            }
        },
        {
            "id": 89,
            "programGuideId": null,
            "name": "\"Am Hummelwald\" - Miniaturen einer Kindheit auf dem Land",
            "icon": "",
            "img": "https://staging-api.muva-app.ch/img/program/crop/500/Vera-und-Isa.jpg",
            "timetableInfo": "19:00, 20:00",
            "duration": "30 Min.",
            "categories": [
                "Musik"
            ],
            "location": {
                "id": 23,
                "name": "Postremise",
                "city": "Chur",
                "coordinates": [
                    9.52926394,
                    46.849735585
                ]
            }
        },
        {
            "id": 106,
            "programGuideId": null,
            "name": "Ausstellung der Visionär*innen: Das Elisium",
            "icon": "",
            "img": "https://staging-api.muva-app.ch/img/program/crop/500/image-1.jpg",
            "timetableInfo": "12:00",
            "duration": "10 Std.",
            "categories": [
                "Ausstellung"
            ],
            "location": {
                "id": 26,
                "name": "Sinnhof ",
                "city": "Chur",
                "coordinates": [
                    9.534741791,
                    46.849007608
                ]
            }
        },
        {
            "id": 65,
            "programGuideId": null,
            "name": "Ausstellung Kunst und Handwerk",
            "icon": "",
            "img": "https://staging-api.muva-app.ch/img/program/crop/500/64746F88-F3B8-4AF6-BD46-A21E7B527FBC.jpg",
            "timetableInfo": "12:00",
            "duration": "6 Std.",
            "categories": [
                "Ausstellung"
            ],
            "location": {
                "id": 17,
                "name": "ibW Schule für Gestaltung Graubünden",
                "city": "Chur",
                "coordinates": [
                    9.529642863,
                    46.854989853
                ]
            }
        },
        {
            "id": 86,
            "programGuideId": null,
            "name": "Bündner Spitzbueba",
            "icon": "",
            "img": "https://staging-api.muva-app.ch/img/program/crop/500/Bundner-Spitzbueba4.jpg",
            "timetableInfo": "20:00, 21:00, 22:00",
            "duration": "30 Min.",
            "categories": [
                "Musik"
            ],
            "location": {
                "id": 24,
                "name": "Rätisches Museum",
                "city": "Chur",
                "coordinates": [
                    9.533483505,
                    46.848099153
                ]
            }
        },
        {
            "id": 33,
            "programGuideId": null,
            "name": "Button-Aktion",
            "icon": "",
            "img": "https://staging-api.muva-app.ch/img/program/crop/500/buttonmaschine.jpg",
            "timetableInfo": "14:00, 14:30, 15:00, 15:30, 16:00, 16:30",
            "duration": "3 Std.",
            "categories": [
                "Ausstellung",
                "Workshop"
            ],
            "location": {
                "id": 13,
                "name": "Forum Würth Chur",
                "city": "Chur",
                "coordinates": [
                    9.528769757,
                    46.860103913
                ]
            }
        },
        {
            "id": 98,
            "programGuideId": null,
            "name": "Coirason",
            "icon": "",
            "img": "https://staging-api.muva-app.ch/img/program/crop/500/coirason_langersamstag23.png",
            "timetableInfo": "19:30, 21:00, 23:00",
            "duration": "30 Min.",
            "categories": [
                "Comedy",
                "Musik"
            ],
            "location": {
                "id": 21,
                "name": "Klibühni, Das Theater",
                "city": "Chur",
                "coordinates": [
                    9.533143366,
                    46.84793411
                ]
            }
        },
        {
            "id": 40,
            "programGuideId": null,
            "name": "Cynthia Gutiérrez | Ausstellung \"Wo unsere Welt endet\"",
            "icon": "",
            "img": "https://staging-api.muva-app.ch/img/program/crop/500/01_CG_estratos-I-III_2019-Kopie.jpg",
            "timetableInfo": "12:00",
            "duration": "20 Min.",
            "categories": [
                "Ausstellung"
            ],
            "location": {
                "id": 11,
                "name": "CUADRO22",
                "city": "Chur",
                "coordinates": [
                    9.513595258,
                    46.851775277
                ]
            }
        },
        {
            "id": 41,
            "programGuideId": null,
            "name": "Cynthia Gutiérrez | Führung durch die Ausstellung |EN/SP",
            "icon": "",
            "img": "https://staging-api.muva-app.ch/img/program/crop/500/-CG_retrato.jpg",
            "timetableInfo": "16:00, 19:00, 21:00",
            "duration": "20 Min.",
            "categories": [
                "Führung"
            ],
            "location": {
                "id": 11,
                "name": "CUADRO22",
                "city": "Chur",
                "coordinates": [
                    9.513595258,
                    46.851775277
                ]
            }
        }
    ]
}
```

### Response Remarks

| Parameter      |Type          |Description                                                    |
|:---------------|:-------------|:--------------------------------------------------------------|
| programGuideId |integer       |ID shown in the program guide of the event                     |


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
| programIds         |csv      |Comma-separated list of program IDs                                                                            |Optional        |
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
                "id": 9,
                "name": "Bündner Kunstmuseum",
                 "coordinates": [
                    9.532246113,
                    46.851327203
                ]
            },
            "program": [
                {
                    "id": 17,
                    "programGuideId": 25,
                    "name": "Ich immer andres. Auf den Spuren von Alberto Giacometti",
                    "icon": "https://staging-api.muva-app.ch/img/icons/Exhibition.svg",
                    "startTime": 1699700400,
                    "endTime": 1699702200
                },
                {
                    "id": 18,
                    "programGuideId": 26,
                    "name": "Führung Ausstellung \"Alberto Giacometti. Porträt des Künstlers als junger Mann\"",
                    "icon": "https://staging-api.muva-app.ch/img/icons/Exhibition.svg",
                    "startTime": 1699700400,
                    "endTime": 1699702200
                },
                {
                    "id": 17,
                    "programGuideId": 25,
                    "name": "Ich immer andres. Auf den Spuren von Alberto Giacometti",
                    "icon": "https://staging-api.muva-app.ch/img/icons/Exhibition.svg",
                    "startTime": 1699702200,
                    "endTime": 1699704000
                },
                {
                    "id": 20,
                    "programGuideId": 27,
                    "name": "Künstlergespräch über künstlerische Anfänge mit Bündner Kunstschaffenden",
                    "icon": "",
                    "startTime": 1699704000,
                    "endTime": 1699705800
                },
                {
                    "id": 17,
                    "programGuideId": 25,
                    "name": "Ich immer andres. Auf den Spuren von Alberto Giacometti",
                    "icon": "https://staging-api.muva-app.ch/img/icons/Exhibition.svg",
                    "startTime": 1699704000,
                    "endTime": 1699705800
                },
                {
                    "id": 17,
                    "programGuideId": 25,
                    "name": "Ich immer andres. Auf den Spuren von Alberto Giacometti",
                    "icon": "https://staging-api.muva-app.ch/img/icons/Exhibition.svg",
                    "startTime": 1699705800,
                    "endTime": 1699707600
                },
                {
                    "id": 20,
                    "programGuideId": 30,
                    "name": "Künstlergespräch über künstlerische Anfänge mit Bündner Kunstschaffenden",
                    "icon": "https://staging-api.muva-app.ch/img/icons/Exhibition.svg",
                    "startTime": 1699707600,
                    "endTime": 1699709400
                },
                {
                    "id": 17,
                    "programGuideId": null,
                    "name": "Ich immer 25. Auf den Spuren von Alberto Giacometti",
                    "icon": "https://staging-api.muva-app.ch/img/icons/Exhibition.svg",
                    "startTime": 1699707600,
                    "endTime": 1699709400
                },
                {
                    "id": 17,
                    "programGuideId": 25,
                    "name": "Ich immer andres. Auf den Spuren von Alberto Giacometti",
                    "icon": "https://staging-api.muva-app.ch/img/icons/Exhibition.svg",
                    "startTime": 1699709400,
                    "endTime": 1699711200
                },
                {
                    "id": 17,
                    "programGuideId": 25,
                    "name": "Ich immer andres. Auf den Spuren von Alberto Giacometti",
                    "icon": "https://staging-api.muva-app.ch/img/icons/Exhibition.svg",
                    "startTime": 1699711200,
                    "endTime": 1699713000
                },
                {
                    "id": 20,
                    "programGuideId": 26,
                    "name": "Künstlergespräch über künstlerische Anfänge mit Bündner Kunstschaffenden",
                    "icon": "https://staging-api.muva-app.ch/img/icons/Exhibition.svg",
                    "startTime": 1699711200,
                    "endTime": 1699713000
                }
            ]
        },
        {
            "location": {
                "id": 10,
                "name": "Bündner Naturmuseum",
                "coordinates": [
                    9.534372464,
                    46.854276027
                ]
            },
            "program": [
                {
                    "id": 52,
                    "programGuideId": null,
                    "name": "Führung durch die Sonderausstellung «Die Katze. Unser wildes Haustier»",
                    "icon": "",
                    "startTime": 1699702200,
                    "endTime": 1699704000
                },
                {
                    "id": 47,
                    "programGuideId": null,
                    "name": "Figurentheater «Der Müllersbub und das Kätzchen»",
                    "icon": "",
                    "startTime": 1699702200,
                    "endTime": 1699704000
                },
                {
                    "id": 47,
                    "programGuideId": null,
                    "name": "Figurentheater «Der Müllersbub und das Kätzchen»",
                    "icon": "",
                    "startTime": 1699705800,
                    "endTime": 1699707600
                },
                {
                    "id": 54,
                    "programGuideId": null,
                    "name": "Führung: Der Luchs – Heimlicher Bewohner unserer Wälder",
                    "icon": "",
                    "startTime": 1699705800,
                    "endTime": 1699707600
                },
                {
                    "id": 47,
                    "programGuideId": null,
                    "name": "Figurentheater «Der Müllersbub und das Kätzchen»",
                    "icon": "",
                    "startTime": 1699709400,
                    "endTime": 1699711200
                },
                {
                    "id": 53,
                    "programGuideId": null,
                    "name": "Von der Wildkatze zum Stubentiger – die Haustierwerdung am Beispiel der Hauskatze",
                    "icon": "",
                    "startTime": 1699709400,
                    "endTime": 1699711200
                },
                {
                    "id": 52,
                    "programGuideId": null,
                    "name": "Führung durch die Sonderausstellung «Die Katze. Unser wildes Haustier»",
                    "icon": "",
                    "startTime": 1699713000,
                    "endTime": 1699714800
                },
                {
                    "id": 55,
                    "programGuideId": null,
                    "name": "Film: Von Katzen und ihrer Magie",
                    "icon": "",
                    "startTime": 1699713000,
                    "endTime": 1699714800
                },
                {
                    "id": 47,
                    "programGuideId": null,
                    "name": "Figurentheater «Der Müllersbub und das Kätzchen»",
                    "icon": "",
                    "startTime": 1699716600,
                    "endTime": 1699718400
                },
                {
                    "id": 53,
                    "programGuideId": null,
                    "name": "Von der Wildkatze zum Stubentiger – die Haustierwerdung am Beispiel der Hauskatze",
                    "icon": "",
                    "startTime": 1699716600,
                    "endTime": 1699718400
                },
                {
                    "id": 54,
                    "programGuideId": null,
                    "name": "Führung: Der Luchs – Heimlicher Bewohner unserer Wälder",
                    "icon": "",
                    "startTime": 1699720200,
                    "endTime": 1699722000
                },
                {
                    "id": 55,
                    "programGuideId": null,
                    "name": "Film: Von Katzen und ihrer Magie",
                    "icon": "",
                    "startTime": 1699720200,
                    "endTime": 1699722000
                },
                {
                    "id": 52,
                    "programGuideId": null,
                    "name": "Führung durch die Sonderausstellung «Die Katze. Unser wildes Haustier»",
                    "icon": "",
                    "startTime": 1699723800,
                    "endTime": 1699725600
                },
                {
                    "id": 56,
                    "programGuideId": null,
                    "name": "Vortrag: Katzenverhalten und die Mensch-Katze-Beziehung",
                    "icon": "",
                    "startTime": 1699723800,
                    "endTime": 1699726800
                },
                {
                    "id": 55,
                    "programGuideId": null,
                    "name": "Film: Von Katzen und ihrer Magie",
                    "icon": "",
                    "startTime": 1699727400,
                    "endTime": 1699729200
                },
                {
                    "id": 57,
                    "programGuideId": null,
                    "name": "Drei Bündner mit Tiger im Tank! – eine musikalische Lesung",
                    "icon": "",
                    "startTime": 1699727400,
                    "endTime": 1699729200
                },
                {
                    "id": 56,
                    "programGuideId": null,
                    "name": "Vortrag: Katzenverhalten und die Mensch-Katze-Beziehung",
                    "icon": "",
                    "startTime": 1699731000,
                    "endTime": 1699734000
                },
                {
                    "id": 54,
                    "programGuideId": null,
                    "name": "Führung: Der Luchs – Heimlicher Bewohner unserer Wälder",
                    "icon": "",
                    "startTime": 1699731000,
                    "endTime": 1699732800
                },
                {
                    "id": 57,
                    "programGuideId": null,
                    "name": "Drei Bündner mit Tiger im Tank! – eine musikalische Lesung",
                    "icon": "",
                    "startTime": 1699734600,
                    "endTime": 1699736400
                },
                {
                    "id": 52,
                    "programGuideId": null,
                    "name": "Führung durch die Sonderausstellung «Die Katze. Unser wildes Haustier»",
                    "icon": "",
                    "startTime": 1699738200,
                    "endTime": 1699740000
                },
                {
                    "id": 57,
                    "programGuideId": null,
                    "name": "Drei Bündner mit Tiger im Tank! – eine musikalische Lesung",
                    "icon": "",
                    "startTime": 1699741800,
                    "endTime": 1699743600
                }
            ]
        },
        {
            "location": {
                "id": 11,
                "name": "CUADRO22",
                "coordinates": [
                    9.513595258,
                    46.851775277
                ]
            },
            "program": [
                {
                    "id": 40,
                    "programGuideId": null,
                    "name": "Cynthia Gutiérrez | Ausstellung \"Wo unsere Welt endet\"",
                    "icon": "",
                    "startTime": 1699700400,
                    "endTime": 1699701600
                },
                {
                    "id": 41,
                    "programGuideId": null,
                    "name": "Cynthia Gutiérrez | Führung durch die Ausstellung |EN/SP",
                    "icon": "",
                    "startTime": 1699714800,
                    "endTime": 1699716000
                },
                {
                    "id": 42,
                    "programGuideId": null,
                    "name": "Marco Luca Castelli | Soll mir lieber Goya den Schlaf rauben als irgendein Arschloch ",
                    "icon": "",
                    "startTime": 1699718400,
                    "endTime": 1699720500
                },
                {
                    "id": 41,
                    "programGuideId": null,
                    "name": "Cynthia Gutiérrez | Führung durch die Ausstellung |EN/SP",
                    "icon": "",
                    "startTime": 1699725600,
                    "endTime": 1699726800
                },
                {
                    "id": 42,
                    "programGuideId": null,
                    "name": "Marco Luca Castelli | Soll mir lieber Goya den Schlaf rauben als irgendein Arschloch ",
                    "icon": "",
                    "startTime": 1699729200,
                    "endTime": 1699731300
                },
                {
                    "id": 43,
                    "programGuideId": null,
                    "name": "Kumbia Boruka | Konzert Cumbia ",
                    "icon": "",
                    "startTime": 1699732800,
                    "endTime": 1699736400
                },
                {
                    "id": 41,
                    "programGuideId": null,
                    "name": "Cynthia Gutiérrez | Führung durch die Ausstellung |EN/SP",
                    "icon": "",
                    "startTime": 1699732800,
                    "endTime": 1699734000
                },
                {
                    "id": 42,
                    "programGuideId": null,
                    "name": "Marco Luca Castelli | Soll mir lieber Goya den Schlaf rauben als irgendein Arschloch ",
                    "icon": "",
                    "startTime": 1699736400,
                    "endTime": 1699738500
                },
                {
                    "id": 43,
                    "programGuideId": null,
                    "name": "Kumbia Boruka | Konzert Cumbia ",
                    "icon": "",
                    "startTime": 1699740000,
                    "endTime": 1699743600
                },
                {
                    "id": 44,
                    "programGuideId": null,
                    "name": "Manuel Fischer | Langer Ausklang",
                    "icon": "",
                    "startTime": 1699743600,
                    "endTime": 1699754400
                }
            ]
        }
    ]
}
```

### Response Remarks

| Parameter          |Type          |Description                                                    |
|:-------------------|:-------------|:--------------------------------------------------------------|
| programGuideId     |integer       |ID shown in the program guide of the event                     |
| program.startTime  |integer       |Unix timestamp                                                 |
| program.endTime    |integer       |Unix timestamp                                                 |


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
| imgSize        |string   |`small`, `medium`, `large` or `xlarge`, default = `large`                   |Optional        |

### Example Request

```
curl -H "Api-Key:xxxxxx" https://api.muva-app.ch/v1/program/1
```

### Example Response
```
{
    "status": 200,
    "result": {
        "id": 89,
        "programGuideId": null,
        "name": "\"Am Hummelwald\" - Miniaturen einer Kindheit auf dem Land",
        "description": "«Am Hummelwald» mit dem Duo Vera Kappeler / Isa Wiss ist ein poetisch-heiter-trauriges Konzert über DAS KIND, dessen Wahrnehmungen und Erlebniswelten. In ihrer ganz eigenen musikalischen Sprache stellen die Musikerinnen den berührenden Texten deutschsprachige Lieder, Abzählreime und experimentelle Klänge gegenüber.",
        "icon": "https://staging-api.muva-app.ch/img/icons/Exhibition.svg",
        "img": "https://staging-api.muva-app.ch/img/program/crop/1400/Vera-und-Isa.jpg",
        "timetableInfo": "19:00, 20:00",
        "duration": "30 Min.",
        "categories": [
            {
                "id": 11,
                "name": "Musik",
                "icon": "https://staging-api.muva-app.ch/img/icons/Music-1.svg"
            }
        ],
        "location": {
            "id": 23,
            "name": "Postremise",
            "description": "Die Postremise ist so etwas wie das heimliche Kulturzentrum von Chur. Mit zwei Bühnen und über 100 Veranstaltungen pro Jahr ist der Ort eine erfrischende Alternative in der städtischen Kulturlandschaft. Offen für professionelle Programme wie für die Amateurkultur, hat sich das Haus überregional und national einen Namen gemacht. Mit seinen Schwerpunkten Kammerkonzerte, Jazz, zeitgenössische Musik und Musiktheater ist das Kulturzentrum experimentell, bewahrend und ermöglichend zugleich. ",
            "img": "https://staging-api.muva-app.ch/img/location/crop/1400/Banner-DJ-Fiedel-2022.jpg",
            "street": "Engadinstrasse ",
            "streetNumber": "43",
            "addressAddition": "",
            "postalCode": "7000",
            "city": "Chur",
            "email": "info@postremise.ch",
            "phone": "",
            "coordinates": [
                9.52926394,
                46.849735585
            ],
            "gastro": {
                "description": "Wieso ändern, wenn es so gut schmeckt?! Seit über zehn Jahren gibt es am Langen Samstag in der Postremise Holzofenpizza von Don Giovanni. Das bleibt auch so! Die Drinks dazu gibt’s an der Postremisen-Bar.\r\n12.00-03.00 durchgehend warme und kalte Getränke\r\n12.00-ca. 16.00 Kaffee und Kuchen\r\n12.00-ca. 24.00 Pizza ",
                "timetableInfo": "12.00 bis 03.00 Uhr"
            },
            "links": {
                "info": {
                    "url": "https://www.postremise.ch",
                    "text": "postremise.ch"
                },
                "googleMaps": {
                    "url": "https://goo.gl/maps/1NqZ6pbT9SctnX9F9",
                    "text": "Google Maps"
                }
            }
        },
        "performanceLocation": "",
        "audios": [],
        "videos": [],
        "links": {
            "tickets": {},
            "info": [
                {
                    "url": "https://www.isawiss.ch/buehne.htm",
                    "text": "isawiss.ch"
                }
            ]
        }
    }
}
```

### Response Remarks

| Parameter      |Type     |Description                                                                |
|:---------------|:--------|:--------------------------------------------------------------------------|
| programGuideId |integer  |ID shown in the program guide of the event                                 |
| links.info     |obj      |Multiple info links possible (for example, if there are multiple artists)  |


## <a name="get-artist-list"></a>GET artist/list  

Get a list of all artists of a space.

### Headers

| Header                 | Type     | Description    	       |                                |
|:-----------------------|:---------|:-------------------------|:-------------------------------|
| Api-Key                | string   | Unique API key           | Required                       |


### Parameters

| Parameter      |Type     |Description                                                                                                    |                |
|:---------------|:--------|:--------------------------------------------------------------------------------------------------------------|:---------------|
| spaceId        |integer  |ID of space                                                                                                    |Required        |
| lang           |string   |language code, default = `de`                                                                                  |Optional        |
| detailed       |boolean  |`1` or `0` whether a detailed result is required (as in [GET artist/:id](#get-artist)), default = `0`      |Optional        |
| imgSize        |string   |`small`, `medium`, `large` or `xlarge`, default = `small`                                                      |Optional        |

### Example Request

```
curl -H "Api-Key:xxxxxx" https://api.muva-app.ch/v1/artist/list?spaceId=1
```

### Example Response
```
{
    "status": 200,
    "result": [
        {
            "id": 1,
            "name": "Luca Sisera",
            "img": "https://api.muva-app.ch/img/artist/crop/500/_test-img-1.jpg"
        },
        {
            "id": 1,
            "name": "Marc Jenny",
            "img": "https://api.muva-app.ch/img/artist/crop/500/_test-img-2.jpg"
        }
    ]
}
```

## <a name="get-artist"></a>GET artist/:id

### Example Request

Get artist infos by artist ID.


### Headers

| Header                 |Type     |Description    	         |                                |
|:-----------------------|:--------|:------------------------|:-------------------------------|
| Api-Key                |string   |Unique API key           |Required                        |

### Parameters

| Parameter      |Type     |Description                                                                 |                |
|:---------------|:--------|:---------------------------------------------------------------------------|:---------------|
| id             |integer  |ID of location                                                              |Required        |
| lang           |string   |language code, default = `de`                                               |Optional        |
| imgSize        |string   |`small`, `medium`, `large` or `large`, default = `medium`                   |Optional        |

### Example Request

```
curl -H "Api-Key:xxxxxx" https://api.muva-app.ch/v1/artist/1
```

### Example Response
```
{
    "status": 200,
    "result": {
        "id": 1,
        "name": "Luca Sisera",
        "description": "Lorem Ipsum",
        "img": "https://api.muva-app.ch/img/artist/crop/1400/_test-img-1.jpg",
        "links": {
            "info": {
                "url": "https://luca-sisera.ch",
                "text": "Homepage Luca Sisera"
            }
        }
    }
}
```

## <a name="get-gastro-list"></a>GET gastro/list  

Get a list of all gastro locations of a space.

### Headers

| Header                 | Type     | Description    	       |                                |
|:-----------------------|:---------|:-------------------------|:-------------------------------|
| Api-Key                | string   | Unique API key           | Required                       |


### Parameters

| Parameter      |Type     |Description                                                                                                    |                |
|:---------------|:--------|:--------------------------------------------------------------------------------------------------------------|:---------------|
| spaceId        |integer  |ID of space                                                                                                    |Required        |
| lang           |string   |language code, default = `de`                                                                                  |Optional        |
| detailed       |boolean  |`1` or `0` whether a detailed result is required (as in [GET gastro/:id](#get-gastro)), default = `0`      |Optional        |
| imgSize        |string   |`small`, `medium`, `large` or `xlarge`, default = `small`                                                      |Optional        |

### Example Request

```
curl -H "Api-Key:xxxxxx" https://api.muva-app.ch/v1/gastro/list?spaceId=1
```

### Example Response
```
{
    "status": 200,
    "result": [
        {
            "id": 1,
            "name": "Restaurant XY",
            "img": "https://api.muva-app.ch/img/gastro/crop/500/_test-img-1.jpg"
        },
        {
            "id": 2,
            "name": "Restaurant YZ",
            "img": "https://api.muva-app.ch/img/gastro/crop/500/_test-img-2.jpg"
        }
    ]
}
```

## <a name="get-gastro"></a>GET gastro/:id

### Example Request

Get gastro infos by gastro ID.


### Headers

| Header                 |Type     |Description    	         |                                |
|:-----------------------|:--------|:------------------------|:-------------------------------|
| Api-Key                |string   |Unique API key           |Required                        |

### Parameters

| Parameter      |Type     |Description                                                                 |                |
|:---------------|:--------|:---------------------------------------------------------------------------|:---------------|
| id             |integer  |ID of location                                                              |Required        |
| lang           |string   |language code, default = `de`                                               |Optional        |
| imgSize        |string   |`small`, `medium`, `large` or `large`, default = `medium`                   |Optional        |

### Example Request

```
curl -H "Api-Key:xxxxxx" https://api.muva-app.ch/v1/gastro/1
```

### Example Response
```
{
    "status": 200,
    "result": {
        "id": 1,
        "name": "Restaurant XY",
        "description": "Lorem Ipsum",
        "icon": "https://api.muva-app.ch/img/icons/Comedy-2.svg",
        "img": "https://api.muva-app.ch/img/gastro/crop/1400/_test-img-1.jpg",
        "street": "Il Stutz",
        "streetNumber": "12b",
        "addressAddition": "",
        "postalCode": "7018",
        "city": "Flims Waldhaus",
        "email": "",
        "phone": "",
        "coordinates": [
            9.525985576,
            46.862496694
        ],
        "links": {
            "info": {}
        }
    }
}
```

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
            "icon": "https://staging-api.muva-app.ch/img/icons/Bus.svg",
            "timetableInfo": ".00 / .15 / .30 / .45 Uhr",
            "coordinates": [
                9.526554752,
                46.859520225
            ],
            "links": {
                "sbb": {},
                "googleMaps": {
                    "url": "https://goo.gl/maps/fkBs4dvqTYaXfSja9",
                    "text": "Google Maps"
                }
            }
        },
        {
            "id": 2,
            "name": "Bahnhofsplatz",
            "icon": "https://staging-api.muva-app.ch/img/icons/Bus.svg",
            "timetableInfo": ".00 / .15 / .30 / .45 Uhr",
            "coordinates": [
                9.529475371,
                46.862308643
            ],
            "links": {
                "sbb": {},
                "googleMaps": {
                    "url": "https://goo.gl/maps/fkBs4dvqTYaXfSja9",
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


## <a name="get-soundwalk"></a>GET soundwalk  

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
curl -H "Api-Key:xxxxxx" https://api.muva-app.ch/v1/soundwalk?spaceId=2
```

### Example Response
```
{
    "status": 200,
    "result": {
        "startingPoint": {
            "name": "Hegisplatz",
            "googleMaps": {
                "url": "https://maps.app.goo.gl/f5oeTJ7nBGXQ4ByK7",
                "text": "Google Maps"
            },
            "coordinates": [
                9.53405,
                46.84911
            ]
        },
        "route": [
            [
                9.53405,
                46.84911
            ],
            [
                9.53413,
                46.84907
            ],
            [
                9.5342671,
                46.848935
            ],
            [
                9.5345127,
                46.8490753
            ],
            [
                9.5346276,
                46.8489881
            ],
            [
                9.5347585,
                46.8489008
            ],
            [
                9.5348959,
                46.8487947
            ],
            [
                9.5349371,
                46.8487528
            ],
            [
                9.5349327,
                46.8487147
            ],
            [
                9.5347896,
                46.8486443
            ],
            [
                9.5346239,
                46.8485575
            ],
            [
                9.5345249,
                46.8484901
            ],
            [
                9.53445,
                46.84843
            ],
            [
                9.53437,
                46.84838
            ],
            [
                9.53429,
                46.84834
            ],
            [
                9.5338,
                46.84809
            ],
            [
                9.53347,
                46.848
            ],
            [
                9.53342,
                46.84799
            ],
            [
                9.53329,
                46.84799
            ],
            [
                9.53257,
                46.84805
            ],
            [
                9.53247,
                46.84808
            ],
            [
                9.53247,
                46.84809
            ],
            [
                9.5325,
                46.84821
            ],
            [
                9.53251,
                46.84827
            ],
            [
                9.53253,
                46.84834
            ],
            [
                9.53259,
                46.84858
            ],
            [
                9.53265,
                46.84878
            ],
            [
                9.53289,
                46.84937
            ],
            [
                9.53299,
                46.84959
            ],
            [
                9.53336,
                46.84962
            ],
            [
                9.53342,
                46.84975
            ],
            [
                9.5339,
                46.84968
            ],
            [
                9.53387,
                46.84961
            ],
            [
                9.53382,
                46.84951
            ],
            [
                9.5337,
                46.84938
            ],
            [
                9.5337,
                46.84928
            ],
            [
                9.533655,
                46.8490366
            ],
            [
                9.5337264,
                46.8490359
            ],
            [
                9.5338354,
                46.8490389
            ],
            [
                9.5339373,
                46.8490895
            ],
            [
                9.53399,
                46.84914
            ],
            [
                9.53404,
                46.84911
            ],
            [
                9.53405,
                46.84911
            ]
        ],
        "situations": [
            {
                "polygon": [
                    [
                        9.53423,
                        46.849857
                    ],
                    [
                        9.533533,
                        46.849157
                    ],
                    [
                        9.533564,
                        46.849157
                    ],
                    [
                        9.53423,
                        46.849857
                    ]
                ],
                "timeRange": [
                    "12:00:00",
                    "18:00:00"
                ],
                "TemperaturRange": [
                    "0",
                    "26"
                ],
                "actions": [
                    {
                        "file": "https://url-to-file.mp3",
                        "loop": true,
                        "delay": false,
                        "repeat": false,
                        "panning": false,
                        "triggers": {
                            "start": "move",
                            "end": "halt"
                        },
                        "fadeIn": false,
                        "fadeOut": 3000
                    },
                    {
                        "file": "https://url-to-file.mp3",
                        "loop": false,
                        "delay": 300,
                        "repeat": 3,
                        "panning": {
                            "directional": true,
                            "panning": -23
                        },
                        "triggers": false,
                        "fadeIn": 3000,
                        "fadeOut": false
                    }
                ],
                "hints": [
                    "Verbinde deine Kopfhörer.",
                    "Folge der Linie auf der Karte."
                ]
            }
        ]
    }
}
```
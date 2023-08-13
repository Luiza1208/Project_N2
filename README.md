# Описание методов 


## 1.  Метод принимает идентификатор geonameid и возвращает информацию о городе.
<code>GET /api/cities/\<int:value></code> - вернет полную информацию о населенном пункте

### Пример запроса
<code>http://127.0.0.1:8000/api/cities/451747</code>

### Ответ
Успешный ответ приходит с кодом <code>200 OK</code> и содержит тело:
```json
{
    "name": "Zyabrikovo",
    "asciiname ": "Zyabrikovo",
    "alternatenames": NaN,
    "latitude": 56.84665,
    "longitude": 34.7048,
    "feature class": "P",
    "feature code": "PPL",
    "country code": "RU",
    "cc2": NaN,
    "admin1 code": 77,
    "admin2 code": NaN,
    "admin3 code": NaN,
    "admin4 code": NaN,
    "population": 0,
    "elevation": NaN,
    "dem ": 204,
    "timezone": "Europe/Moscow",
    "modification date": "2011-07-09"
}
```

## 2.	Метод принимает страницу и количество отображаемых на странице городов и возвращает список городов с их информацией. 
<code>GET /api/pages/page\<int:page>&items\<int:items></code> - вернет список населенных пунктов с полной информацией о них

### Пример запроса
<code>http://127.0.0.1:8000/api/pages/page3&items2</code>

### Ответ
Успешный ответ приходит с кодом <code>200 OK</code> и содержит тело:
```json
{
    "451752": {
        "name": "Zhelezovo",
        "asciiname ": "Zhelezovo",
        "alternatenames": NaN,
        "latitude": 57.02591,
        "longitude": 34.51886,
        "feature class": "P",
        "feature code": "PPL",
        "country code": "RU",
        "cc2": NaN,
        "admin1 code": 77,
        "admin2 code": NaN,
        "admin3 code": NaN,
        "admin4 code": NaN,
        "population": 0,
        "elevation": NaN,
        "dem ": 192,
        "timezone": "Europe/Moscow",
        "modification date": "2011-07-09"
    },
    "451753": {
        "name": "Zel\u00ebntsyno",
        "asciiname ": "Zelentsyno",
        "alternatenames": NaN,
        "latitude": 56.73452,
        "longitude": 34.92011,
        "feature class": "P",
        "feature code": "PPL",
        "country code": "RU",
        "cc2": NaN,
        "admin1 code": 77,
        "admin2 code": NaN,
        "admin3 code": NaN,
        "admin4 code": NaN,
        "population": 0,
        "elevation": NaN,
        "dem ": 159,
        "timezone": "Europe/Moscow",
        "modification date": "2011-07-09"
    },
    "451754": {
        "name": "Zel\u00ebnaya Niva",
        "asciiname ": "Zelenaya Niva",
        "alternatenames": NaN,
        "latitude": 57.1711,
        "longitude": 34.76977,
        "feature class": "P",
        "feature code": "PPL",
        "country code": "RU",
        "cc2": NaN,
        "admin1 code": 77,
        "admin2 code": NaN,
        "admin3 code": NaN,
        "admin4 code": NaN,
        "population": 0,
        "elevation": NaN,
        "dem ": 160,
        "timezone": "Europe/Moscow",
        "modification date": "2011-07-09"
    }
}


```

## 3. Метод принимает названия двух городов (на русском языке) и получает информацию о найденных городах, а также дополнительно: какой из них расположен севернее и одинаковая ли у них временная зона, показывать пользователю не только факт различия временных зон, но и на сколько часов они различаются
<code>GET /api/comparison/citie1\<name1>&citie2\<name2></code> - вернет полную информацию о сравниваемых населенных пунктах, а также информацию о временной зоне, и о том какой населенный пункт севернее. Дополнительно выдаст разницу во времени между таймзонами

Парметры <code>?city1</code> - первый населенный пункт и <code>?city2</code> - второй населенный пункт

### Пример запроса
<code>http://127.0.0.1:8000//api/comparison/citie1знаменка&citie2гора%20татарская</code>

### Ответ
Успешный ответ приходит с кодом <code>200 OK</code> и содержит тело:
```json
[
    {
        "name": "Znamenka",
        "asciiname ": "Znamenka",
        "alternatenames": "Kukuyevka,Znamenka,\u0417\u043d\u0430\u043c\u0435\u043d\u043a\u0430",
        "latitude": 52.89789,
        "longitude": 35.97703,
        "feature class": "P",
        "feature code": "PPL",
        "country code": "RU",
        "cc2": NaN,
        "admin1 code": 56,
        "admin2 code": NaN,
        "admin3 code": NaN,
        "admin4 code": NaN,
        "population": 11995,
        "elevation": NaN,
        "dem ": 157,
        "timezone": "Europe/Moscow",
        "modification date": "2014-06-27"
    },
    {
        "name": "Gora Tatarskaya",
        "asciiname ": "Gora Tatarskaya",
        "alternatenames": "Gora Tatarskaja,Gora Tatarskaya,\u0413\u043e\u0440\u0430 \u0422\u0430\u0442\u0430\u0440\u0441\u043a\u0430\u044f",
        "latitude": 54.9656,
        "longitude": 93.6151,
        "feature class": "T",
        "feature code": "MT",
        "country code": "RU",
        "cc2": NaN,
        "admin1 code": 91.0,
        "admin2 code": NaN,
        "admin3 code": NaN,
        "admin4 code": NaN,
        "population": 0,
        "elevation": NaN,
        "dem ": 792,
        "timezone": "Asia/Krasnoyarsk",
        "modification date": "2012-08-05"
    },
    "northern city: Gora Tatarskaya",
    "Timezone is different",
    "time difference: 4"
]
```




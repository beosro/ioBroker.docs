---
translatedFrom: en
translatedWarning: Если вы хотите отредактировать этот документ, удалите поле «translationFrom», в противном случае этот документ будет снова автоматически переведен
editLink: https://github.com/ioBroker/ioBroker.docs/edit/master/docs/ru/adapterref/iobroker.coronavirus-statistics/README.md
title: ioBroker.coronavirus-статистика
hash: oTIhUDP9XRjsxpNs7s5q8OIxCSwDQeG2kZFHzz6bpk4=
---
![Версия NPM](http://img.shields.io/npm/v/iobroker.coronavirus-statistics.svg)
![Загрузки](https://img.shields.io/npm/dm/iobroker.coronavirus-statistics.svg)
![Количество установок (последняя)](http://iobroker.live/badges/coronavirus-statistics-installed.svg)
![Количество установок (стабильно)](http://iobroker.live/badges/coronavirus-statistics-stable.svg)
![Статус зависимости](https://img.shields.io/david/iobroker-community-adapters/iobroker.coronavirus-statistics.svg)
![Известные уязвимости](https://snyk.io/test/github/iobroker-community-adapters/ioBroker.coronavirus-statistics/badge.svg)
![NPM](https://nodei.co/npm/iobroker.coronavirus-statistics.png?downloads=true)
![Трэвис-CI](http://img.shields.io/travis/iobroker-community-adapters/ioBroker.coronavirus-statistics/master.svg)

! (Логотип) [админ / коронавирус-statistics.png]

# IoBroker.coronavirus-statistics
## Адаптер живой статистики Coronavirus для ioBroker
Адаптер для отображения информации о вирусе глобальной короны и текущих отчетов

Конфигурация не требуется, после установки:

- Получать глобальную информацию по всему миру и записывать ее в «global_totals»
- Создайте папку для каждой страны со всей соответствующей информацией, касающейся COVID-19
- Обновлять информацию каждые 15 минут

Доступна следующая информация:

| Datapoint | Детали |
|--|--|
| активный | Количество текущих инфицированных людей |
| случаи | Количество полностью известных случаев |
| критический | Сумма критической ситуации (Госпитализирована) |
| смерти | Количество зарегистрированных зарегистрированных смертей |
| выздоровел | Количество полностью известных восстановленных случаев |
| TodayCases | Новые случаи на сегодня |
| сегодня смерти | Количество полностью известных людей умерло сегодня |

Обратите внимание, что этот адаптер использует как можно больше актуальной информации, но в зависимости от отчета страны может быть задержка на несколько часов.
Источник: https://coronavirus-19-api.herokuapp.com

## Добавить недостающие страны
Может случиться, что страны не распознаются правильно, потому что API предоставляет названия некоторых стран, не соответствующих ISO. В таком случае вы получите предупреждение в журнале, которое выглядит следующим образом

```
coronavirus-statistics.0	2020-03-21 09:05:31.328	warn	(22937) Timor-Leste not found in lib! Must be added to the country name translator.
```

Используя точку данных `coronavirus-statistics.0.countryTranslator`, вы можете назначить страну самостоятельно. Ищите название соответствующей страны здесь:

[Список с названиями стран](https://github.com/i-rocky/country-list-js/blob/master/data/names.json)

С выбранным названием страны необходимо создать строку JSON и ввести ее в точку данных `coronavirus-statistics.0.countryTranslator`.
Строка JSON выглядит следующим образом, например:

```
{
	"Cabo_Verde": "Cape Verde",
	"Timor-Leste": "East Timor"
}
```

В качестве первого значения имя из предупреждающего сообщения должно быть взято из журнала. Название страны из [Список с названиями стран](https://github.com/i-rocky/country-list-js/blob/master/data/names.json) затем присваивается этому.

## Changelog

### 0.3.3
* (DutchmanNL) Improved configuration page
* (DutchmanNL) Make country list in configuration variable	
* (DutchmanNL) Implement choice if non-selected countrys should be deleted from states (if already there, default No!) 

### 0.3.1
* (DutchmanNL) Enable configuration

### 0.3.0 (2020-03-22)
* (bluefox) The number of data points was reduced by selection of countries
 
### 0.2.5 
* (Scrounger) Bugfix : Cabo_Verde not found in lib! Must be added to the country name translator

### 0.2.4
* (Scrounger) Grouping by continents implemented

### 0.2.3
* (DutchmanNL) Error message for new attribute solved

### 0.2.2
* (GermanBluefox) fixed widget countries

### 0.2.1
* (DutchmanNL) Fixed error "State attribute definition missing"
* (DutchmanNL) Moved "_Laste_Update" to updated within global_totals tree
* (GermanBluefox) fix logo size

### 0.2.0 Code optimized & released
* (DutchmanNL) Stable release
* (DutchmanNL) Added retry if API does not provide correct information
* (DutchmanNL) Added last time stamp of data collection
* (AlCalzone) Code optimized

### 0.1.6 Adapter renamed
* (@DutchmanNL) Adapter renamed

### 0.1.2 Widgets added & code improvements
* (DutchmanNL) code improvements
* (GermanBluefox) add widgets

### 0.1.0
* (DutchmanNL) initial release

## License
MIT License

Copyright (c) 2020 DutchmanNL <rdrozda86@gmail.com>

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
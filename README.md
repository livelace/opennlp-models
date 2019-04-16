#### Автоматически обновляемые модели [OpenNLP](https://opennlp.apache.org/) для русского языка.

Модели созданы на общедоступном материале новостных агентств:  
  
1. [Ведомости](https://www.vedomosti.ru/)
2. [ИА REGNUM](https://regnum.ru)  
3. [Известия](https://iz.ru/) 
4. [Интерфакс](http://www.interfax.ru/) 
5. [РИА Новости](https://ria.ru/)
6. [ТАСС](http://tass.ru)  

  

Сбор данных осуществляется с помощью [mosquito](https://github.com/livelace/mosquito).  
Разметка тегов осуществляется с помощью [ner-tagger](https://github.com/livelace/ner-tagger).
<br>

# Быстрый старт:

Отображение справки:

```bash
user@localhost ~ $ docker run -ti --rm livelace/opennlp-models:1.8.4
This container intended for quick evaluation of OpenNLP models for Russian language whose based on various news feeds.

For more details see: https://github.com/livelace/opennlp-models

Usage:

--type news. Model type.
--lang ru. Model language.
--entity combined|date|event|facility|geopolitical|location|money|organization|person|time. Entity type.

Example:

docker run -ti --rm livelace/opennlp-models:1.8.4 --type news --lang ru --entity combined

... write your sentence
```

Непосредственный запуск TokenNameFinder:

```bash
user@localhost ~ $ docker run -ti --rm livelace/opennlp-models:1.8.4 --type news --lang ru --entity combined
INFO: Entities information:

date: 3286
event: 405
facility: 500
geopolitical: 5726
location: 693
money: 577
organization: 4760
person: 4582
time: 51
sentence: 9057

Loading Token Name Finder model ... done (0.365s)
Ранее МВД по региону сообщало, что около 6.00 мск в Орске на перекрестке улиц Талалихина и Деповской столкнулись легковой автомобиль "Лада Ларгус" и маршрутная "Газель".
Ранее <START:ORG> МВД по региону <END> сообщало, что около <START:TIME> 6.00 мск <END> в <START:GPE> Орске <END> <START:LOC> на перекрестке улиц Талалихина и Деповской <END> столкнулись легковой автомобиль "Лада <START:PER> Ларгус" <END> и маршрутная "Газель"
```
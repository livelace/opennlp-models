Обновления (08.10.2018):

1. Теперь все модели распространяются в [Docker контейнере](https://hub.docker.com/r/livelace/opennlp-models/).
2. Модели собираются для всех версии OpenNLP (быстрое сравнение качества распознавания между версиями).

#### Автоматически обновляемые модели [OpenNLP](https://opennlp.apache.org/) для русского языка.

Модели созданы на общедоступном материале новостных агентств:  
  
1. [Ведомости](https://www.vedomosti.ru/)
2. [Известия](https://iz.ru/) 
3. [Интерфакс](http://www.interfax.ru/) 
4. [РИА Новости](https://ria.ru/)
5. [ТАСС](http://tass.ru)  
  

Сбор данных осуществляется с помощью [mosquito](https://github.com/livelace/mosquito).  
Разметка тегов осуществляется с помощью [ner-tagger](https://github.com/livelace/ner-tagger).
<br><br><br>

| Название модели | Краткое описание | Примеры сущностей |
|----------|----|----|
|common_combined.txt.bin |Модель для распознавания всех типов сущностей. |- |
|common_date.txt.bin |Модель для распознавания дат. |9 мая 1945<br>2018<br>декабре прошлого года |
|common_location.txt.bin |Модель для распознавания месторасположений. |Россия<br>Парасельские острова<br>деревня Альбибен |
|common_money.txt.bin |Модель для распознавания денежных единиц. |2,5 млрд рублей<br>15 миллиардов долларов<br>2$ млн |
|common_organization.txt.bin |Модель для распознавания организаций. |Госдума<br>ФКУ Упрдор "Тамань"<br>South China Morning Post |
|common_person.txt.bin |Модель для распознавания персон. |Хуан Антонио Пицци<br>Вайнштейн<br>Афанасьев-Кадомцев |
|common_sentence.txt.bin |Модель для распознавания границ предложений. |- |
|common_time.txt.bin |Модель для распознавания времени. |20:30<br>16:30 мск<br>00:00 |


# Быстрый старт:

Отображение справки:

```bash
user@localhost ~ $ docker run -ti --rm livelace/opennlp-models
This container intended for quick evaluation of OpenNLP models for Russian language whose based on various news feeds.

For more details see: https://github.com/livelace/opennlp-models

Usage:

--version 1.5.3|1.6.0|1.7.0|1.7.1|1.7.2|1.8.0|1.8.2|1.8.3|1.8.4|1.9.0. Set version of OpenNLP.
--lang ru|en. Set language of a model.
--entity combined|date|location|money|organization|person|time. Set entity type.

Example:

docker run -ti --rm livelace/opennlp-models --version 1.8.4 --lang ru --entity combined

... write your sentence
```

Непосредственный запуск TokenNameFinder:

```bash
user@localhost ~ $ docker run -ti --rm livelace/opennlp-models --version 1.8.4 --lang ru --entity combined
Loading Token Name Finder model ... done (0.276s)
Центральный комитет Коммунистической партии Китая официально объявил о расследовании в отношении главы Интерпола и по совместительству замминистра общественной безопасности КНР Мэна Хунвэя, которого подозревают в нарушении закона.
<START:organization> Центральный комитет Коммунистической партии Китая <END> официально объявил о расследовании в отношении главы <START:organization> Интерпола <END> и по совместительству замминистра общественной безопасности <START:location> КНР <END> <START:person> Мэна Хунвэя, <END> которого подозревают в нарушении закона.
```
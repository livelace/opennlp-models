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

**Отображение справки:**

```bash
user@localhost ~ $ docker run -ti --rm livelace/opennlp-models:1.8.4
This container intended for quick evaluation of OpenNLP models for Russian language whose based on various news feeds.

For more details see: https://github.com/livelace/opennlp-models

Usage:

--mode sentence|ner Mode type.
--type news. Model type.
--lang ru. Model language.

'ner' specific options:

--entity combined|date|event|facility|geopolitical|location|money|organization|person|time. Entity type.


Named entities recognition mode:

docker run -ti --rm livelace/opennlp-models:1.8.4 --mode ner --type news --lang ru --entity combined

... write sentences


Sentence detection mode:

docker run -ti --rm livelace/opennlp-models:1.8.4 --mode sentence --type news --lang ru

... write sentences
```

**Распознавание именовынных сущностей:**

```bash
user@localhost ~ $ docker run -ti --rm livelace/opennlp-models:1.8.4  --mode ner --type news --lang ru --entity combined
INFO: Entities information:

date: 3433
event: 419
facility: 517
geopolitical: 5887
location: 713
money: 596
organization: 4919
person: 4758
time: 55
sentence: 9380

Loading Token Name Finder model ... done (0.383s)
Приговор Марии Бутиной имеет антиправовой характер, он доказывает, что США ради геополитических интересов готовы нарушать фундаментальные принципы построения своей правовой системы, заявил РИА Новости председатель комитета Совета Федерации по конституционному законодательству Андрей Клишас.
<START:PER> Приговор Марии Бутиной <END> имеет антиправовой характер, он доказывает, что <START:GPE> США <END> ради геополитических интересов готовы нарушать фундаментальные принципы построения своей правовой системы, заявил <START:ORG> РИА Новости <END> председатель комитета <START:ORG> Совета Федерации <END> по конституционному законодательству <START:PER> Андрей Клишас. <END>
```

**Распознавание границ предложений:**
```bash
user@localhost ~ $ docker run -ti --rm livelace/opennlp-models:1.8.4  --mode sentence --type news --lang ru             
INFO: Entities information:

date: 3433
event: 419
facility: 517
geopolitical: 5887
location: 713
money: 596
organization: 4919
person: 4758
time: 55
sentence: 9380

Loading Sentence Detector model ... done (0.030s)
В середине апреля суд в Киеве признал незаконной национализацию ПриватБанка и недействительным договор купли-продажи банка. Решение было принято по иску Коломойского, который был основным владельцем банка до его национализации в конце 2016 года. Кроме того, суды приняли еще несколько решений по делу ПриватБанка в пользу Коломойского. Минфин и Нацбанк готовятся их обжаловать. В пятницу стало известно о подаче Коломойским еще пяти исков — он оспаривает законность кредитов рефинансирования и свое личное поручительство по ним.

В середине апреля суд в Киеве признал незаконной национализацию ПриватБанка и недействительным договор купли-продажи банка.
Решение было принято по иску Коломойского, который был основным владельцем банка до его национализации в конце 2016 года.
Кроме того, суды приняли еще несколько решений по делу ПриватБанка в пользу Коломойского.
Минфин и Нацбанк готовятся их обжаловать.
В пятницу стало известно о подаче Коломойским еще пяти исков — он оспаривает законность кредитов рефинансирования и свое личное поручительство по ним.
```
#### Автоматически обновляемые модели [OpenNLP](https://opennlp.apache.org/) для русского языка.

Модели созданы на общедоступном материале новостных агентств:  
  
1. [Ведомости](https://www.vedomosti.ru/)
2. [ИА REGNUM](https://regnum.ru)  
3. [Известия](https://iz.ru/) 
4. [Интерфакс](http://www.interfax.ru/) 
5. [РИА Новости](https://ria.ru/)
6. [ТАСС](http://tass.ru)  

  

Сбор данных осуществляется с помощью [gosquito](https://github.com/livelace/gosquito).  
Разметка тегов осуществляется с помощью [digator](https://github.com/livelace/digator).
<br>

# Быстрый старт:

**Отображение справки:**

```bash
user@localhost ~ $ docker run -ti --rm ghcr.io/livelace/opennlp-models:1.8.4
This container intended for quick evaluation of OpenNLP models for Russian language whose based on various news feeds.

For more details see: https://github.com/livelace/opennlp-models

Usage:

--type news. Model type.
--lang ru. Model language.
--entity all|date|event|fac|gpe|loc|money|org|per|time. Entity type.

Named entities recognition mode:

docker run -ti --rm ghcr.io/livelace/opennlp-models:1.8.4 --type news --lang ru --entity all

... write sentences
```

**Распознавание именованных сущностей:**

```bash
user@localhost ~ $ docker run -ti --rm ghcr.io/livelace/opennlp-models:1.8.4 --type news --lang ru --entity all
INFO: Type here: 
Loading Token Name Finder model ... done (0.312s)
Приговор Марии Бутиной имеет антиправовой характер, он доказывает, что США ради геополитических интересов готовы нарушать фундаментальные принципы построения своей правовой системы, заявил РИА Новости председатель комитета Совета Федерации по конституционному законодательству Андрей Клишас.
<START:PER> Приговор Марии Бутиной <END> имеет антиправовой характер, он доказывает, что <START:GPE> США <END> ради геополитических интересов готовы нарушать фундаментальные принципы построения своей правовой системы, заявил <START:ORG> РИА Новости <END> председатель комитета <START:ORG> Совета Федерации <END> по конституционному законодательству <START:PER> Андрей Клишас. <END>
```
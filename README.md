# PTE

 Проект для октрывания 2 дверей домофона и брелка шлагбаума.  

 Схема работы:
 1. Уличный домоф,звонок происходит на домофон по нажатию кнопки, Дверь1 открывается в вебинтерфейсе срабатывают пины D5 D6.  
 2. Внутренний домоф,звонок происходит на домофон по нажатию кнопки, Дверь2 открывается в вебинтерфейсе срабатывает пин D7.  
 3. Брелок шлагбаума. Срабатывает после нажатия на кнопку шлагбаума и активен 30 секунд. 

 Звонок не передается в веб среду или хоум ассистент. 

Общие характеристики:  
Напряжение 5V, Поднятое состояния пина 3.3V. Для срабатывания кнопки на домофоне необхоимо пробросить пин на кнопку после неё и землю на плату в любое место.Перед прошивкой можно указать wifi имя сети или пароль, либо ввести после включения устрояства через точку доступа.  

## Распиновка ethernet разъема:
    1.Белооранжевый D5 (GPIO14)
    2.Оранжевый D6 (GPIO12)
    3.белозеленый D7 (GPIO13)
    4.Синий D8  (GPIO15)
    5-8 Земля Gnd.
 
## Прошивка
Для того что бы прошить устроства необходим docker.
Если прошивать по USB:  
```docker run --rm --net=host -it -p 6052:6052 -v "${PWD}"/config/:/config --device=/dev/ttyUSB0 esphome/esphome:dev```  
Прошивка по воздуху OTA:  
```docker run --rm --net=host -it -p 6052:6052 -v "${PWD}"/config/:/config esphome/esphome:dev```  
После этого доступен веб интерфейс для прошивки, на устройсве где вы запустили esphome dashboard http://127.0.0.1:6052.


## Фото
![Устройство](https://github.com/ilkarataev/PTE/blob/master/img/board.jpg)  

![Схема](https://github.com/ilkarataev/PTE/blob/master/img/schem.png)  

![Схема](https://github.com/ilkarataev/PTE/blob/master/img/schem1.png)  

Устройство версия 2.
т.к. шлагбаум долеко не получилось использовать оптопару для упраления брелок.Решил развести все на своей плате на модуле esp12e.
К сожелению фото платы не сделал. Основные компоненты работают также. + добавил вывод для звонка который можно использовать для подключения через оптопару.
Ссылка на проект платы.
https://easyeda.com/karvet89/PTE_domofon



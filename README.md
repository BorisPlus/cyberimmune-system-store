# Система учёта, контроля остатков и поиска товара на складе

_Исследование в рамках изучения методологии кибериммунной разработки - [п. 7.1.](https://github.com/sergey-sobolev/cyberimmune-systems/wiki/%D0%98%D0%B4%D0%B5%D0%B8-%D0%B4%D0%BB%D1%8F-%D1%83%D1%87%D0%B5%D0%B1%D0%BD%D1%8B%D1%85-%D0%BF%D1%80%D0%B8%D0%BC%D0%B5%D1%80%D0%BE%D0%B2)_  

Пример выбран в качестве наиболее наглядного и доступного для понимания с целью исследования [методологии кибериммунной разработки](https://github.com/sergey-sobolev/cyberimmune-systems/wiki/).
 
## Артефакты

Активы: 
* товары;

Угрозы: 
* поступающий на склад товар не учитывается;
* повторный учет товара;
* учитываемый поступающий на склад товар размещается в неусановленном месте;
* отпускаемые со склада товары не снимаются с учета;
* сведения об осавободившемся на складе месте не обновляются при отпуске товара со склада;

Цель:
* ни при каких обстоятельсвах не должно быть расхождений между учтенным товаром и заимаемым товаром местом на складе;

Подцели:
* поступающий на склад товар будет учтен с корректным его меторасположением;
* отпускаемый со склада товар будет снят с учета, а место высвобождено;

Предположения безопасности:
*

Допущения:
* рассматриваемая модель работает в рамках авторизованого складского работника
* роли "учетчика" и "продовца" реализуются одним складским работником
* товары поступают отдельно, одна упаковка - это один товар
* оборот денежных средств моделью не рассматривается 

Домены:
* Поставщик;
* Потребитель;
* Грузчик;
* Книга учета;
* Склад;
* Кладовщик - это доверенный "менеджер" в терминах методологии;
* Инвентаризация (инвентаризационная комиссия) - этот доверенный домен сличает данные Книги учета и фактические сведения со Склада, принимает решение об отсуствии расхождений: 1) весь товар в из Книги учета располаегается на своих местах на Складе, 2) товара, присуствующего на Складе и сведения о котором в Книге отсуствут, нет.

## Схемы

Пока опустил схему работы с "Потребителем", дорисую в случае одобрения преподавателем схемы работы с "Поставщиком".

Нагляднее будет нарисовать ниспадающий сценарий учета товара в хронологии последовательности действий (запросов\ответов) доменов.

### Схема работы с "Поставщиком"

![](./README.files/Работа_с_поставщиком.PNG)
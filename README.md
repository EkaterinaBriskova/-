# TMP
# Практика 0
```
@startuml
left to right direction
skinparam packageStyle rect

actor эксперт
actor соискатель_грантов
actor держатель_фонда

rectangle информационная_система_технической_экспертизы {
  
  соискатель_грантов--(подача заявки)
  соискатель_грантов--(выгодная презентация)

  (подача заявки) .> (независимая экспертиза)

  эксперт--(рассмотрение заявок)
  эксперт--(независимая экспертиза)
  
  (независимая экспертиза).> (выдача гранта)

  держатель_фонда--(оценка результата экспертизы)
  держатель_фонда--(выдача гранта)

}
@enduml

```

![0](https://user-images.githubusercontent.com/90749103/228903594-21f3ed13-3d28-4063-9bfd-51d4dd4d576c.png)


# Практика 1
```
@startuml
left to right direction
title Система технической экспертизы
actor Эксперт
actor Соискатель_грантов
actor держатель_фонда
rectangle Система {
держатель_фонда -- (организация мероприятия)
(организация мероприятия) ..>(подача заявки):<<include>>
(организация мероприятия) ..> (независимая экспертиза):<<include>>
(организация мероприятия) ..> (оценка результатов экспертизы):<<include>>

Соискатель_грантов -- (подача заявки)
(подача заявки) ..> (Выдача гранта):<<include>>
(независимая экспертиза) ..> (Выдача гранта):<<include>>
(оценка результатов экспертизы) ..> (Выдача гранта):<<include>>
Эксперт -- (независимая экспертиза)
}
@enduml

```
![2](https://user-images.githubusercontent.com/90749103/229521524-06e654d7-3475-4ac8-8c26-bf9e14a7e7f4.png)

```
@startuml
class Эксперт{
+Паспортные данные
+ФИО
+Должность
Проверка()

}

class Соискатель_грантов{
+Паспортные данные
+ФИО соискателя
+Номер гранта
Регистрация Гранта()
}

class Грант{
+Номер гранта
+ФИО Представителя гранта
+Презентация Гранта
}

class Держатель_фонда{
+ФИО
+Должность
Оценка результата экспертизы()
Выдача гранта()
}

class СтатусГранта{
+Номер гранта
+Статус Гранта
+Отчет об экспертизе
}

class Выполнено{
+Грант проверен
}

Эксперт --> Грант:Проверяет
Соискатель_грантов --> Грант:Регистрация гранта
Держатель_фонда --> Грант:Выдает
Эксперт --> СтатусГранта:Изменяет статус
Держатель_фонда --> СтатусГранта:Оценивает результат экспертизы
СтатусГранта --> Выполнено
Грант --> Выполнено
Выполнено --> ВыдачаГранта

```
![1](https://user-images.githubusercontent.com/90749103/228903511-2f07ff60-7900-4260-9e43-feb364c0cf87.png)

# Практика 2

```
@startuml
title Информационная система технической экспертизы: диаграмма последовательности
skinparam backgroundcolor AntiqueWhite/Gold
participant Соискатель
participant Заявка
participant Эксперт 
participant Держатель_фонда
participant Грант
activate Соискатель
Соискатель -> Заявка: подает заявку
activate Заявка
Заявка -> Эксперт : Выдает заявку
deactivate Соискатель
activate Эксперт 
Эксперт -> Заявка:Оценивает заявку
Заявка-> Держатель_фонда:Заявка одобрена
deactivate Заявка
activate Держатель_фонда
Держатель_фонда -> Грант:Принимает решение о выдаче грантов
deactivate Держатель_фонда
activate Грант
Грант-> Соискатель:Выдает грант
deactivate Эксперт 
activate Соискатель
@enduml 


```
![3](https://user-images.githubusercontent.com/90749103/230009514-26a74119-2cde-485e-aaf2-a51ba4fe1fe7.png)

```
@startuml
left to right direction
title Система технической экспертизы: диаграмма развертывания
skinparam backgroundcolor AntiqueWhite/Gold
database Заявка
node ПК_Эксперт
node ПК_Соискатель
node ПК_Держатель_фонда
node Грант
node Система_экспертизы

ПК_Эксперт - Заявка: Проверяют
ПК_Соискатель - Заявка: Подают
ПК_Эксперт - Система_экспертизы: Используют
ПК_Держатель_фонда - Заявка: Оценивает
ПК_Держатель_фонда - Грант: принимает решение
Грант - ПК_Соискатель: Выдает грант
@enduml

```
![4](https://user-images.githubusercontent.com/90749103/230009572-e9958a7e-6609-4a9c-add0-32f196de38e1.png)

# Практика 3
# Стратегия
```
@startuml
title Пратическая работа 3: Strategy
class Variant{
selection()
}
class Game{
strategy: Variant
init()
play()
}

class Paper{
selection()
}
class Rock{
selection()
}
class Scissors{
selection()
}
class Pencil{
selection()
}
class Fire{
selection()
}
class main{
int n
str vibor
playtime()
player1.play(player2)
}
note right of main::"playtime()"
player1 = playtime(vibor)
player2 = playtime(vibor)
end note

Paper --> Variant
Rock --> Variant
Scissors --> Variant
Pencil --> Variant
Fire --> Variant
main *--> Variant
main --Game
@enduml
```

![]<img width="672" alt="5" src="https://user-images.githubusercontent.com/90749103/235784363-54e507ab-6e44-4410-93b3-247e59987c20.png">

# Шаблонный метод
```
@startuml
title Пратическая работа 3: Template Method
class Algorithm{
template_method()
flagstock()
draw_1()
draw_2()
draw_3()
final()
printer()
}
note right of Algorithm::"template_method()"
self.flagstock()
self.draw_1()
self.draw_2()
self.draw_3()
self.final()
self.printer()
end note

class colors{
painwhite()
painred()
painblue()
}

class RussianFlag{
z = colors
z.pain
draw_1()
draw_2()
draw_3()
final()
}
class  Austria{
z = colors
z.pain
draw_1()
draw_2()
draw_3()
}

Algorithm <|-- Austria :Немецкий флаг
Algorithm <|-- RussianFlag : Российский флаг

RussianFlag -  Austria
(RussianFlag, Austria) - colors:Задает цвет
@enduml

```
![Alt text](скриншоты/6.png)


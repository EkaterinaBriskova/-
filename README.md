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

![Alt text](диаграммы/0.png)

# Практика 1
```
Диаграмма классов
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

![Alt text](диаграммы/1.png)

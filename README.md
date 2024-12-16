# АНАЛИЗ ДАННЫХ И ИСКУССТВЕННЫЙ ИНТЕЛЛЕКТ [in GameDev]
Отчет по лабораторной работе #5 выполнил(а):
- Соловьева Ольга Павловна
- РИ-230942

Отметка о выполнении заданий (заполняется студентом):

| Задание | Выполнение | Баллы |
| ------ | ------ | ------ |
| Задание 1 | * | 60 |
| Задание 2 | * | 20 |
| Задание 3 | * | 20 |

знак "*" - задание выполнено; знак "#" - задание не выполнено;

Работу проверили:
- к.т.н., доцент Денисов Д.В.
- к.э.н., доцент Панов М.А.
- ст. преп., Фадеев В.О.

[![N|Solid](https://cldup.com/dTxpPi9lDf.thumb.png)](https://nodesource.com/products/nsolid)

[![Build Status](https://travis-ci.org/joemccann/dillinger.svg?branch=master)](https://travis-ci.org/joemccann/dillinger)

## Цель работы
Познакомиться с программными средствами для создания системы машинного обучения и ее интеграции в Unity.


## Задание 1
### Найдите внутри C# скрипта “коэффициент корреляции ” и сделать выводы о том, как он влияет на обучение модели.

Я предположила, что в данном случае коэффициентом корреляции будет максимальное расстояние, на котором агент должен оказаться от цели, в исходном скрипте это 1.42. То есть это то значение, по которому можно соотнести ожидаемый от агента результат и его итог в цикле обучения. Логирование при исходных значениях выглядит так:
![task 1](https://github.com/kurlyushonok/DA-in-GameDev-lab5/blob/main/images/distance1.jpg)

Если уменьшить максимальную дистанцию до 1, то обучение проходит немного медленнее. До 270000 шага значение среднего вознаграждения намного меньше, то есть агент в меньшем количестве случаев достигает цели. Также увеличивается среднее отклонение от цели. Ко всему прочему, если наблюдать работу обученной с таким значением модели, то будет заметно, что рядом с кубом шарик начинает кружить и выискивать нужную точку, что увеличивает время поиска цели и выглядит не очень хорошо. Скрин логирования при значении максимальной дистанции 1:
![task 1](https://github.com/kurlyushonok/DA-in-GameDev-lab5/blob/main/images/originalValues.jpg)

Если увеличить максимальную дистанцию до 3, то значение среднего вознаграждения резко возрастает и в течение всего обучения держится очень близко к 1, иногда даже равняется 1. При этом результаты обученной модели не очень хорошие: шарик может не достигать кубика, и при этом будет считаться, что он попал в цель, хотя визуально был далеко от нее. Скрин логирования при значении максимальной дистанции 1:

![task 1](https://github.com/kurlyushonok/DA-in-GameDev-lab5/blob/main/images/distance3.jpg)

Подводя итоги, можно сказать, что коэффициент коррелляции в данном случае будет влиять на то, насколько сильно агент будет стремиться к своей цели и выискивать идеальную точку попадания, минимизируя среднее отклонение от нее.

## Задание 2
### Изменить параметры файла yaml-агента и определить какие параметры и как влияют на обучение модели. Привести описание не менее трех параметров.

В первую очередь я попробовала изменить значение batch_size, то есть размер одного батча с 10 до 50. В основном это повлияло только на время обучения, которое уменьшилось почти в 2 раза:

![task 2](https://github.com/kurlyushonok/DA-in-GameDev-lab5/blob/main/images/batch50.jpg)

Следующим я пробовала изменить количество эпох обучения с 3 на 1. В целом ничего не изменилось, тоже уменьшилось общее время обучения, возросло среднее значение вознаграждения. Значения среднего отклонения колеблются. Количество эпох обучения может влиять на финальную точность работы модели, но в данном случае видимых изменений нет, так как изначально модель не требует большого количества эпох для обучения.

![task 2](https://github.com/kurlyushonok/DA-in-GameDev-lab5/blob/main/images/epochs1.jpg)

И последнее, что я поменяла - максимальное количество шагов при обучении. Обучение завершается в разы быстрее, но в итоге модель работает очень медленно - при запуске агент довольно долго ищет цель, а не идет напрямую в ее сторону. Логирование при таком параметре:

![task 2](https://github.com/kurlyushonok/DA-in-GameDev-lab5/blob/main/images/steps20000.jpg)

## Задание 3
### Приведите примеры, для каких игровых задачи и ситуаций могут использоваться примеры 1 и 2 с ML-Agent’ом. В каких случаях проще использовать ML-агент, а не писать программную реализацию решения? 




## Выводы

Было установленно и протестировано на функциональность необходимое ПО. Все работает 👍


## Powered by

**BigDigital Team: Denisov | Fadeev | Panov**

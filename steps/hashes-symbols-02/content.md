# Много билетов пассажиров 

А теперь составьте массив хэшей с несколькими пассажирами в вагоне.

Индекс хэша в массиве — место пассажира в вагоне.

Затем выведите все билеты на экран.

**Например:**

```sh
> ruby passenger.rb
Пассажиры поезда Москва — Петушки

* * * Место № 1 * * *
Билет № РМ2010398 050298
Маршрут: Москва -> Петушки
Пассажир: Венедикт В. Ерофеев
Паспорт: 45 99 505281

* * * Место № 2 * * *
Билет № РМ2010399 050298
Маршрут: Павловский Посад -> Орехово-Зуево
Пассажир: Иннокентий П. Шниперсон
Паспорт: 46 01 192872

* * * Место № 3 * * *
Билет № РМ2010399 050298
Маршрут: Москва -> Владимир
Пассажир: Иван В. Бунша
Паспорт: 47 33 912876
```

<div class="rubyrush-task-hint">

Вы уже видели, что массив в руби может хранить любые элементы.

Запишите ассоциативные массив через запятую в общий массив также, как мы записывали другие элементы (строки, числа).

А затем запустите цикл по всем элементам этого общего массива с помощью метода `each_with_index`.

https://ruby-doc.org/core-2.4.0/Enumerable.html#method-i-each_with_index

</div>


<div class="rubyrush-task-answer">


<ul>
<li><a href="https://github.com/aristofun/rubyrush-path/blob/master/steps/hashes-symbols-02/solution/passengers.rb" class="rubyrush-task-solution-link">Файл с решением</a></li></ul>

</div>
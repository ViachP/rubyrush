# Конвертор рублей в доллары 

Напишите конвертер валют рубли-доллары: программу, которая спрашивает курс, потом спрашивает у пользователя, сколько у него рублей, а потом выдает результат в долларах.

**Например:**

```ruby
Сколько сейчас стоит 1 доллар в рублях?
> 41.23
Сколько  у вас рублей?
> 30000

Ваши запасы равны: $ 727.63
```

<div class="rubyrush-task-hint">

Для преобразования строки в дробное число используйте метод `to_f`. 

Для округления дробного числа до двух знаков после запятой (чтобы правильно получать копейки и центы) используйте [метод](http://www.ruby-doc.org/core-2.1.2/Float.html#method-i-round) `round(2)` у числа с плавающей точкой (также как использовали метод `to_f`).

Также помните, чтобы добавить к строке число, у числа нужно вызвать еще и метод `to_s`.

</div>


<div class="rubyrush-task-answer">


<ul>
<li><a href="https://github.com/aristofun/rubyrush-path/blob/master/steps/gets-butovo-02/solution/currency_converter.rb" class="rubyrush-task-solution-link">Наш вариант решения</a></li></ul>

</div>
# Отладка программ, дебаггер 

 До сих пор, если вы все внимательно повторяли за нами, вы скорее всего избежали серьезных проблем и ошибок. Но это только потому, что мы готовились к каждому уроку и тщательно проверяли каждую нашу программу. 

В реальной работе никогда не бывает все так гладко. Пора уже научиться находить и уничтожать баги. Это неотъемлемая часть работы программиста, и для этого существуют специальные инструменты. 

![Дебаггер](http://goodprogrammer.ru/system/rich_texts/000/000/38775f03ddbc998f327e789ab9bb87d25cde5a1f3fc/01-debugger-for-text.jpg?1440878140 "Дебаггер")

### План урока

1. Дебагер — что это и как работает?
2. Как дебажить в RubyMine
3. Как дебажить без RubyMine


<!-- youtube starts here -->
<script>
var videoPlan = {}
</script>

<div class="embed-responsive embed-responsive-16by9 rubyrush-video" id="video-0">
<iframe src="https://www.youtube.com/embed/YT26qsoEAqc" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
<script>
videoPlan["video-0"] = [{"begin":"0:06","comment":"Приветствие и план урока"},{"begin":"0:44","comment":"Идея дебагера: как залезть под капот"},{"begin":"3:48","comment":"Дебаг в RubyMine: ставим гемы"},{"begin":"7:49","comment":"Дебаг в RubyMine: пишем «Корни квадратного уравнения»"},{"begin":"8:58","comment":"Дебаг в RubyMine: breakpoint и дебаг-режим"},{"begin":"11:42","comment":"Дебаг в RubyMine: evaluate expression"}]
</script>
</div>


<div class="embed-responsive embed-responsive-16by9 rubyrush-video" id="video-1">
<iframe src="https://www.youtube.com/embed/X5VuEUd_Oe8" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
<script>
videoPlan["video-1"] = [{"begin":"0:04","comment":"Исправляем ошибки в программе «Корни квадратного уравнения»"},{"begin":"3:22","comment":"Рефакторинг в RubyMine"},{"begin":"5:18","comment":"Особенности работы программы в дебаг режиме"},{"begin":"6:35","comment":"Когда нужно пользоваться дебагером"},{"begin":"8:04","comment":"Итоги урока"}]
</script>
</div>

 <!-- youtube ends here --> 

### Что такое дебаггер?

И вновь, вот уже в который раз вспомним нашу метафору с дорогой и машинкой.

![Обещаем, этот раз — последний :)](http://goodprogrammer.ru/system/rich_texts/000/000/38894e50d47f4b2a3bac8a54c3939bb47a86bfa1e78/02-road-with-a-stone-for-text.png?1440878140 "Обещаем, этот раз — последний :)")

Если наша машина вдруг заглохла, есть два варианта: либо проблему видно сразу, например, камень на дороге или уровень бензина на нуле, либо машина просто заглохла и всё. Жми педали, крути руль — не едет и всё тут. Приходится думать и искать поломку, залезать под капот.

Программы в компьютере обычно выполняются очень быстро, процессор старается выполнить код программы с максимальной скоростью, чтобы освободить ресурсы для следующей программы. 

Эта скорость иногда мешает понять, в чём проблема и в какой момент случилась загвоздка. Тогда хочется программу остановить или замедлить.

Подобно тому, как спортивные машины на испытаниях обвешивают специальным оборудованием, которое в режиме реального времени снимает все возможные показания (температуру мотора, нагрузку на карданный вал, давление жидкостей и так далее), нам тоже хочется запустить нашу программу и в любой момент иметь возможность остановить её и посмотреть значения каких-то переменных и выражений.

Это можно сделать с помощью дебаггера — специальной программы, которая позволяет погрузиться внутрь работающей программы, наблюдать за ее выполнением и даже вмешиваться в ее выполнение.

![А если не пользоваться дебаггером, багов станет больше](http://goodprogrammer.ru/system/rich_texts/000/000/389781860c7ba244ccd015f30fc5934a98e8b27764b/03-bugs-for-text.jpg?1440878140 "А если не пользоваться дебаггером, багов станет больше")

### Как работает дебаггер (отладчик)

Главная задача дебаггера — помочь найти [баг](http://lurkmore.to/%D0%91%D0%B0%D0%B3) (ошибку), поэтому он так и называется. 

Если вы обнаружили ошибку, но не знаете ее причину, ваша задача — сделать какие-то предположения. И запустить программу с помощью дебаггера для проверки этих предположений.

Для дебага программа запускается в специальном режиме, в котором вы можете поставить в любой точке «брейкпоинт», инструкцию для дебаггера остановить выполнение программы на каком-то конкретном шаге и передать управление вам.

Как только программа дошла до брейкпойнта, она останавливается. Дальше вы можете рулить машиной «step-by-step», шаг за шагом выполняя программу строчку за строчкой и анализируя все ее переменные. 

Давайте попробуем отдебажить что-нибудь из написанного нами ранее.

### Установка дебаггера для RubyMine

В RubyMine довольно просто запустить программу в режиме отладки, для этого рядом с кнопкой Run всегда есть кнопка с зеленым жучком:

![Кнопка Debug в RubyMine](http://goodprogrammer.ru/system/rich_texts/000/000/524880235bdf42a29056afaec1479b9d997d719c8d2/debug_button.png?1445011935 "Кнопка Debug в RubyMine")

При первом запуске дебаггера RubyMine может попросить вас разрешения установить дополнительные гемы:

![RubyMine просит установить debase для отладки](http://goodprogrammer.ru/system/rich_texts/000/000/390dd1d6474bd1a2d8502c38424103be1e2a94dfcb5/04-ruby-mine-warning-for-text.jpg?1440878140 "RubyMine просит установить debase для отладки")

Гемы лучше установить предварительно самостоятельно. Давайте установим основной гем, нужный для дебага:

```sh
gem install ruby-debug-ide
```

(если это не получится в обычной консоли, запустите Dev-Kit-овскую, `c:\dev\msys.bat`, см. как мы это делаем на видео)

Теперь давайте напишем программу, которую мы будем дебажить.


### Программа для решения квадратных уравнений

Пишем программу, которая решает квадратные уравнения.

**`equation.rb`**:

```ruby
puts 'Solve equation: A * x^2 + B * x + C = 0'

puts 'Enter A:'
a = gets.to_f

puts 'Enter B:'
b = gets.to_f

puts 'Enter C:'
c = gets.to_f


# считаем дискриминант
discr = b*b - 4*a*c;

# первый корень
x1 = (-b + Math::sqrt(discr))/(2*a)

# второй корень
x2 = (-b - Math::sqrt(discr))/(2*a)


puts 'Solution 1:'
puts x1

puts 'Solution 2:'
puts x2

```

Если мы попробуем запустить эту программу с параметрами `a=0, b=4, c=2` или `a=3, b=2, c=1`, то программа выдаст либо какую-то фигню, либо вообще упадет с ошибкой. 

Давайте разбираться. Поставим брейкоинт вот на этой строчке:

```ruby
discr = b*b - 4*a*c;
```

И запустим программу ещё раз:

![Процесс отладки](http://goodprogrammer.ru/system/rich_texts/000/000/3920dce6ce29eb57c304bcd558c4f3c59eac59e82d2/06-debugging-for-text.jpg?1440878140 "Процесс отладки")

Когда программа остановится, давайте попробуем вычислить дискриминант отдельно: нажмите `Alt+F8` (или иконку с калькулятором), у вас появилось окно **Evaluate expression**.

Это окно, которое позволяет выполнять любой код (и видеть результат), как если бы он был написан перед той строчкой, на которой остановилось ваше приложение.

![Вычисляем значение выражения](http://goodprogrammer.ru/system/rich_texts/000/000/3930b0c1fcc9459e22e9950fe368b8bcb589dac6437/07-evaluate-for-text.jpg?1440878140 "Вычисляем значение выражения")

Если мы вычислим дискриминант, то увидим, что всё хорошо, дискриминант равен 4-м. Идём дальше (нажимаем `F8`). Это называется **Step Over**, означает «выполнить следующую строчку и остановиться». Так можно строчка за строчкой пройти всю программу в любом нужном вам темпе.

Давайте на следующем шаге вычислим первый корень, снова нажмите `Alt+F8` и вычислите значение первого корня:

![Наш первый баг](http://goodprogrammer.ru/system/rich_texts/000/000/3947d8ada57f9f5e31abe4fb648cb1623b9730e5430/08-bug-one-for-text.jpg?1440878140 "Наш первый баг")

Оп-па! Результат выходит не числом. Тут уже легко разобраться, что раз у нас `a=0`, то делить на эту переменную другие нельзя. Это исключение надо обработать отдельно.

Давайте разберёмся со вторым случаем. Снова запускаем нашу программу в режиме отладки, но уже с новыми значениями `a=3, b=2, c=1` и снова останавливаем:

![Наш второй баг](http://goodprogrammer.ru/system/rich_texts/000/000/3956b4c41b90d50a95643dd20c05b98d2470d8f2c40/09-bug-two-for-text.jpg?1440878140 "Наш второй баг")

Мы попытались взять квадратный корень из отрицательного числа. В этом случае корней в действительных числах нет. 

Можно написать в программе, что в таком случае корней нет и выйти. А можно сделать умней — добавить в программу поддержку [комплексных чисел](http://ru.wikipedia.org/wiki/%D0%9A%D0%BE%D0%BC%D0%BF%D0%BB%D0%B5%D0%BA%D1%81%D0%BD%D0%BE%D0%B5_%D1%87%D0%B8%D1%81%D0%BB%D0%BE), тогда корень из отрицательного числа обретет новый смысл. 

Вот так будет выглядеть наша исправленная программа:

```ruby
# Метод, выводящий решение на экран
def print_root(x_real, x_complex)
  puts 'Solution:'
  print x_real
  print ' +' if x_complex > 0
  print " #{x_complex} * i" if x_complex != 0
  puts
end

puts 'Solve equation: A * x^2 + B * x + C = 0'

puts 'Enter A:'
a = gets.to_f

puts 'Enter B:'
b = gets.to_f

puts 'Enter C:'
c = gets.to_f

if a == 0
  abort "It is linear equation! x = #{-c/b}"
end

# считаем дискриминант
discr = b*b - 4*a*c;

if discr < 0 # комплексные числа пошли

  x1_real = -b/(2*a)
  x1_complex = Math::sqrt(-discr)/(2*a)

  x2_real = -b/(2*a)
  x2_complex = -Math::sqrt(-discr)/(2*a)

else
  # первый корень
  x1_real = (-b + Math::sqrt(discr))/(2*a)
  x1_complex = 0

  # второй корень
  x2_real = (-b - Math::sqrt(discr))/(2*a)
  x2_complex = 0
end

print_root(x1_real, x1_complex)
print_root(x2_real, x2_complex)
```

### Нюансы при отладке

Если наша программа работает с несколькими потоками, то при остановке одного из потоков, другие могут продолжить выполняться или остановиться в непредсказуемых местах. 

Также во время остановки могут протухнуть внешние ресурсы (удаляться какие-нибудь временные файлы, пропадёт сеть и так далее), так что очень сложная программа в режиме отладки может вести себя не совсем так, как она ведёт себя в обычном режиме.

Ещё один нюанс: во время отладки может так выйти, что вы забредёте в код сторонних библиотек или языка руби. Не стоит бояться заглянуть и изучить чужой код, особенно если он хорош.

### Как дебажить без RubyMine (byebug)

Если дебаг в RubyMine по каким-то причинам не для вас, то есть другие способы. Например с помощью специальной библиотеки `byebug`:

```sh
gem install byebug
```

Чтобы вашу программу можно было отдебажить с помощью «байбага», вам нужно добавить его в список подключённых библиотек в коде программы:

```ruby
require byebug
```

А вместо брейкпоинта вам просто нужно написать в интересном вам месте волшебное слово

```ruby
byebug
```

Дойдя до этой строчки, программа остановится и передаст вам управление прямо в консоли. Вы сможете выполнять там команды, также как в окне **Evaluate Expression** рубимайна, и смотреть значение выражений:

![Пример работы byebug](http://goodprogrammer.ru/system/rich_texts/000/000/396536ae460be19f5ed1a4521905288d0b159166df7/10-byebug-for-text.jpg?1440878140 "Пример работы byebug")

### Зачем и когда дебажить?

Когда пользоваться дебагером, а когда нет, решать вам. В конечном итоге ошибку всё равно ищете вы, дебаггер лишь помогает проверять предположения. 

Но вот несколько советов, когда вам стоит вспомнить про дебагер:

* Если вы столкнулись с неочевидным, сложным багом
* Нужно исследовать сложное и неочевидное поведение какой-то части программы
* Чтобы лучше понять как работает собственный код
* Чтобы наконец понять как работает чужой код :)

Мы очень надеемся, что теперь вы перестанете бояться ошибок в ваших приложениях, какими бы сложными они ни были.

Дальше научимся делать так, чтобы сложные ошибки появлялись в наших программах как можно реже!
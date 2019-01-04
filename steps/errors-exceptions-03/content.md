# Виселица с обработкой исключений 

Добавьте в программу Виселица обработку исключений при открытии файла со списком слов и при загрузке картинок-виселиц. 

При ошибке открытия списка слов завершите программу. Если не хватает файлов–картинок, используйте вместо незагрузившихся картинок какую-нибудь строку. 

При открытии файла для чтения единственная легко воспроизводимая ошибка это отсутствие файла. Погуглите какой тип исключения нужно ловить в этом случае. Переименуйте нужные файлы и проверьте, что ваша программа правильно работает.

<div class="rubyrush-task-hint">

Ошибки при открытии файла, если вы предварительно проверили его существование с помощью `File.exist?` — маловероятны. Поэтому, чтобы убедиться, что ваша обработка ошибок работает, сперва удалите такую проверку. Она нам будет не нужна.

Затем поместите открытие файла в блок `begin ... rescue ... end` и поймайте ошибку `SystemCallError` (подробнее см. [доки](http://www.ruby-doc.org/core-2.1.2/SystemCallError.html)).

Обратите внимание, что мы ловим `SystemCallError` чтобы обработать все возможные ошибки связанные с открытием файла. Не только отсутствие файла, но и всевозможные системные ошибки доступа к нему. 

Этим мы с одной стороны расширяем группу отлавливаемых ошибок (что не очень хорошо), с другой — остаемся в рамках определенной группы (вызовы ОС), что уместно поскольку единственный вызов, который делаем — чтение файла.

http://stackoverflow.com/questions/11457795/how-to-rescue-all-exceptions-under-a-certain-namespace
 


</div>


<div class="rubyrush-task-answer">

Скачайте наши исходники и посмотрите, как мы открываем файлы в классах word_reader.rb и result_printer.rb.

Для работы программы нужно также установить библиотеку unicode_utils:

```sh
gem install unicode_utils
```

<ul>
<li><a href="https://github.com/aristofun/rubyrush-path/blob/master/steps/errors-exceptions-03/solution/03_viselitsa.zip" class="rubyrush-task-solution-link">Распакуйте и запустите viselitsa.rb</a></li></ul>

</div>
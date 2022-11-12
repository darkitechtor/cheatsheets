|Задача|Команда|Пример|Комментарии|
|-|-|-|-|
|высветить рабочую директорию|`pwd`|||	
|изменить директорию (переместиться)|`cd`|||		
|корневая директория|`cd ~`||Корневая - не root!|
|назад|`cd -`|||	
|наверх|`cd ..`|||	
|высветить содержимое директории|`ls`|`ls -R -F ~`|`-R` - опция рекурсивного высвечивания директорий (содержания текущей и всех вложенных);</br>`-F` - опция подсветки папок и приложений"|
|перемесить файл|`mv`|`mv dag.py ~/airflow/dags`|Переписывает файл, если файл с таким именем существовал|
|переименовать файл||`mv course.txt old-course.txt`|Переписывает файл, если файл с таким именем существовал|
|копировать файл|`cp`|`cp seasonal/summer.csv backup/summer.bck`|Пример для копирования в другую директорию с переименованием|
|удалить файл|`rm`|`rm thesis.txt`||
|удалить директорию|`rmdir`||сперва нужно удалить все файлы из директории|
|создать директорию|`mkdir`|`mkdir ~/yearly`||
|открыть файл|`cat`|||	
||`less`|`less seasonal/spring.csv seasonal/summer.csv`|**Один файл**:</br>пробел - прокрутить</br>`q` - выход</br>**Несколько файлов**:</br>`:n` - перейти к следующему файлу</br>`:p`  - перейти к предыдущему файлу</br>`:q` - выход|
|Посмотреть начало файла|`head`|`head -n 3 seasonal/summer.csv`|`-n` число - сколько строк высветить.</br>По умолчанию (без `-n`) - 10|
|Посмотреть определенные столбцы|`cut`|`cut -f 2-5, 8 -d , everyone.csv`|`-f` - выбирает столбцы (счет начинается с единицы)</br>`-d` - указывает разделитель столбцов (в примере - запятая)
|Завершает строку|**TAB**||если вариантов несколько, то повторное нажатие высветит все варианты|
|Справка по функциям|`man`|`man head`|зачастую выводит справку в less-формате|
|Повторить команду|`!`|`!head`</br>`!3`|Удобно использовать вместо стрелки вверх для копирования одной из предыдущих команд|
|Высветить список использованных команд|`history`||Можно использовать в связке с, например, `!3`|
|Аналог LIKE|`grep`|`grep -n -v molar seasonal/spring.csv`</br>`grep -c incisor seasonal/autumn.csv seasonal/winter.csv`|У него дохрена опций - нужно смотреть мануал|
||`egrep`|`egrep 'Sydney Carton \| Charles Darnay'`|Если нужно найти одно из двух. Аналог:</br>`grep -E 'Sydney Carton \| Charles Darnay'`</br>или</br>`grep 'Sydney Carton \\| Charles Darnay'`|
|Сохранить результат в файл|`>`|`head -n 5 seasonal/summer.csv > top.csv`||
|pipe|`\|`|`head -n 5 seasonal/summer.csv \| tail -n 3`|Выполняет второй запрос из результата первого|
|Счетчик|`wc`|`grep 2017-07 seasonal/spring.csv \| wc -l`|Опции `-c`, `-w`, `-l` - для подсчета, соответственно, characters, words, and lines|
|Wildcards (регулярки)|`*`</br>`?`|`head -n 3 seasonal/*.csv	`|`*` - много символов</br>`?` - один символ</br>`[...]` - один из символов в скобках</br>`{...}` matches any of the comma-separated patterns inside the curly brackets, so {*.txt, *.csv} matches any file whose name ends with .txt or .csv, but not files whose names end with .pdf|
|Сортировка|`sort`||`-n` - numerical</br>`-r` - reverse</br>и т.д.|
|Убрать дубли|`uniq`|`uniq -c`|Убирает только те дубли, что находятся по соседству друг с другом (нужно делать sort перед ним)</br>`-c` - считает количество упоминаний каждого уникального значения|
|Прервать выполнение программы|**Ctrl+C**</br>**^C**||||		
|Вывод содержания переменной|`echo`|`echo $OSTYPE`|||
|Создание внутренней переменной||`testing=seasonal/winter.csv`|Потом можно использовать, например, в `head -n 1 $testing`|
|Цикл||`for filetype in gif jpg png; do echo $filetype; done`</br>`for f in $files; do echo $f; done`||	
|Редактировать файл|`nano`|`nano filename`|Создает файл, если файла с таким имененм не было.</br>**Ctrl + K**: delete a line</br>**Ctrl + U**: un-delete a line</br>**Ctrl + O**: save the file ('O' stands for 'output'). You will also need to press Enter to confirm the filename!</br>**Ctrl + X**: exit the editor|
|Запустить скрипт|`bash`|`bash headers.sh`</br>`bash count-records.sh seasonal/*.csv`|Можно передавать названия файлов, которые заменят $@ в скрипте|
|Пример скрипта||<pre># Print the first and last data records of each file.</br>for filename in $@</br>do</br>    head -n 2 $filename \| tail -n 1</br>    tail -n 1 $filename</br>done</pre>||
|Разархивировать|`unzip`|`unzip SpotifyData.zip`||
|Скачать файл|`curl`|`curl -O https://websitename.com/datafilename[001-100:10].txt`|`-o` - скачать, указав имя|
|Скачать файл|`wget`|`wget --wait=1 -i url_list.txt`</br>`wget --limit-rate=2500k -i url_list.txt`||	
|Выполнить вторую команду в том случае, если первая завершилась успешно|`&&`|`csvlook Spotify_Popularity.csv && csvstat Spotify_Popularity.csv`||
|Заменить значения в файле, не открывая его|`sed`|`sed 's/Cherno/Cherno City/g'`|*s/что_заменять/на_что_заменять/опции* - замена символов, поддерживаются регулярные выражения;</br>`g` - заменить содержимое буфера шаблона, содержимым дополнительного буфера|
|Создать файл|`touch`|`touch test-2-2-3.txt`||
||`>`|`> test-20.txt`||
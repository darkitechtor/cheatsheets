|Задача|Пример|Комментарии|
|-|-|-|
|Установить csvkit|`pip install csvkit`||
|Обновить csvkit|`pip install --upgrade csvkit`||
|Конвертировать xlsx-файл в csv-файл|`in2csv SpotifyData.xlsx --sheet "Worksheet1_Popularity" > Spotify_Popularity.csv`||
|Превью|`csvlook SpotifyData.csv`||
|Статистика|`csvstat SpotifeData.csv`||
|Выбрать столбцы|`csvcut -c 1,3,5 Spotify_MusicAttributes.csv`|`-c` - колонка|
|Выбрать по условию|`csvgrep -c "danceability" -m 0.812`|`-m` - *match* - совпадение, то есть, *что именно найти*|
|Объединить файлы - Аналог `UNION` в SQL|`csvstack -g "Sep2018","Oct2018" "date" -n SpotifyData_PopularityRank6.csv SpotifyData_PopularityRank7.csv > SpotifyPopularity.csv`|`-g` - *group*</br>`-n` - *name*
|Обращаться с помощью SQL sql2csv|`sql2csv --db "sqlite:///SpotifyDatabase.db" --query "SELECT * FROM Spotify_Popularity LIMIT 5" > Spotify_Popularity_5Rows.csv`|Текст sql-запроса должен быть записан в одну строчку|
|Обращаться с помощью SQL csvsql|`csvsql --query "SELECT * FROM Spotify_MusicAttributes ORDER BY duration_ms LIMIT 1" Spotify_MusicAttributes.csv"`|Текст sql-запроса должен быть записан в одну строчку|
||`sqlquery="SELECT * FROM Spotify_MusicAttributes ORDER BY duration_ms LIMIT 1"`</br>`csvsql --query "$sqlquery" Spotify_MusicAttributes.csv`|для удобства можно присвоить текст запроса переменной и сделать так|
|Загрузить csv-файл в БД|`csvsql --db "sqlite:///SpotifyDatabase.db" --insert Spotify_MusicAttributes.csv`||	
|Играться с локальными csv-файлами на SQL|`sqlquery_union="SELECT * FROM SpotifyMostRecentData UNION ALL SELECT * FROM Spotify201812"`</br>`csvsql --query ""$sqlquery_union"" SpotifyMostRecentData.csv Spotify201812.csv > UnionedSpotifyData.csv`||
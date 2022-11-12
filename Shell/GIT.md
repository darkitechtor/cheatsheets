|Задача|Команда|Пример|Комментарии|
|-|-|-|-|					
|показать текущее состояние репозитория|`git status`|||
|увидеть изменения|`git diff`|`git diff`</br>`git diff data/northern.csv`</br>`git diff -r HEAD data/northern.csv`|- во всем репозитории</br>- в отдельном файле</br>`-r` - сравнить с конкретной ревизией</br>`HEAD` - самый последний коммит|
|добавить в staging|`git add`|`git add report.txt`||
|закоммитить изменения|`git commit`|`git commit -m "Program appears to have become self-aware."`</br>`git commit --amend - m "new message"`|`-m "..."` - комментарий к коммиту</br>- откорректировать комментарий|			
|посмотреть историю изменений|`git log`|`git log data/southern.csv`|посмотреть историю изменений конкретного файла|
|посмотреть детали определенного коммита|`git show`|`git show 0da2f7`|Например, *0da2f7* - начало хэша коммита|
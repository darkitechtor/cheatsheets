|Задача|Пример|Комментарии|
|-|-|-|
|Вывести список задач в расписании|`crontab -l`||	
|Добавить задачу в расписание|`echo "* * * * * python hello_world.py" \| crontab`|Add as job that runs every minute on the minute to crontab|
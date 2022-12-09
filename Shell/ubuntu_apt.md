### Установка через apt-get
|Задача|Команда|Пример|Комментарии|
|-|-|-|-|
|Установить пакет|`sudo apt-get install`|`sudo apt-get install ffmpeg`</br>`sudo apt-get install ffmpeg=7:4.2.7-0ubuntu0.1`|`ffmpeg=7:4.2.7-0ubuntu0.1` - установка пакета ffmpeg определенной версии|
|Посмотреть установленные пакеты|`apt list --installed`|||
|Посмотреть доступные пакеты|`apt-cache pkgnames`|`apt-cache pkgnames \| grep php`||
|Посмотреть информацию о пакете перед его установкой|`apt-cache search`|`apt-cache search vsftpd`|Собирает информацию обо всех пакетах, содержащих в названии искомое слово.</br>Для точного совпадения нужно использовать, например, такую конструкцию: `"^vsftpd$"`|
|Посмотреть более подробную информацию о пакете перед его установкой|`apt-cache show`|`apt-cache show netcat`||
|Посмотреть зависимости пакета перед его установкой|`apt-cache showpkg`|`apt-cache showpkg postgresql`||
|Посмотреть changelog пакета перед его установкой|`sudo apt-get changelog`|`sudo apt-get changelog postgresql`||
|Посмотреть общую статистику apt|`apt-cache stats`|||
|Обновить список пакетов и сами пакеты|`sudo apt-get update`</br>`sudo apt-get upgrade`||`apt-get update` обновляет список доступных пакетов и их версий, но не устанавливает и не обновляет какие-либо пакеты.</br>`apt-get upgrade` фактически устанавливает более новые версии имеющихся у вас пакетов.|
|Удалить пакет|`sudo apt-get remove`|`sudo apt-get remove ffmpeg`||
|Удалить пакет вместе с настройками|`sudo apt-get purge`|`sudo apt-get purge ffmpeg`||
### Установка из deb-файлов
|Задача|Команда|Пример|Комментарии|
|-|-|-|-|
|Установка из deb-файла||`sudo apt install ./google-chrome-stable_current_amd64.deb`</br>`sudo apt install -f`|`sudo apt install -f` - обязательная команда для установки зависимостей|
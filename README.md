##### Скрипт для загрузки фотографий товаров из МойСклад в Insales

###### Алгоритм работы
- находим в МС все товары с фотографиями;
- находим соответствующие товары в InSales;
- если в InSales фотографий нет, загружаем их;
- если InSales фото уже есть, ничего не делаем.

###### Инструкция по установке
1. Поместите файлы скрипта в отдельную папку, например /home/user/script. ВАЖНО:
  * Не помещайте файлы в общедоступные папки, например, директории веб-сервера, это небезопасно.
  * Не удаляйте папку temp (изначально пустую), она нужна для сохранения лога и файлов для отладки.

2. Python3 должен быть установлен на сервере:
```bash
user@sever:$ which python3
/usr/local/bin/python3
```
Точная версия не важна: скрипт должен работать с любой версией интерпретатора Python 3.x

3. Создайте виртуальную среду:
```bash
user@sever:$ python3 -m venv /path/to/environment
```
Проще всего разместить её в самой папке со скриптом. Для этого замените /path/to/ на полный путь к папке.

4. Активируйте виртуальную среду:
```bash
user@sever:$ source /path/to/environment/bin/activate
(environment) user@sever:$
```

5. Установите менеджер пакетов pip, если он не установлен:
```bash
(environment) user@sever:$ python3 -m ensurepip --default-pip
```

6. Скрипт требует для работы единственного дополнительного пакета requests. Установите его:
```bash
(environment) user@sever:$ pip install requests
```

7. Создайте (измените) shell-скрипт для удобного запуска скрипта по расписанию:
```run_script.sh
#!/bin/bash
cd /path/to/script
source environment/bin/activate
python3 main.py
```

8. Добавьте в crontab строку для запуска скрипта каждый час:
```crontab
* 0-23 * * * /path/to/script/run_script.sh
```

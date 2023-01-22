# Scraping
Рабочий проект сбора данных из открытых источников.

Примечание : ***Из уважения к компании вся информация о конкретных регистрационных номерах ~~стерта из кода~~***


## Используемые библиотеки 
```ruby
import pandas as pd
from selenium.webdriver import Chrome
from selenium.webdriver.common.keys import Keys
from selenium.webdriver.support.ui import WebDriverWait
from selenium.webdriver.support import expected_conditions as EC
from selenium.common.exceptions import NoSuchElementException
from selenium.webdriver.common.by import By
from bs4 import BeautifulSoup
from time import sleep
from tqdm import tqdm
```

## Chrome Driver
Должен мэтчиться с вашей версией хрома, нужно периодически его обновлять

## Краткий принцип работы
Данные, которые нам нужно парсить находятся **внутри** каждой строчки выгружаемых данных. Так как мы физически не можем сразу заполучить все URL из кода страницы, первая часть моего кода сперва собирает данные для их преобразования. Проанализировав ряд URL, я отметила специфику, которую позволит сгенерировать ссылки самостоятельно. В столбце "номер свидетельства" есть набор символов, последние 9 из которых мы сможем использовать для склеивания наших ID с шаблоном. Так мы получим URL каждой позиции. Важно постоянно проверять соответствие элементов на запрашиваемых страницах и результатов парсинга. 

Вторая часть кода уже выгружает нужные нам данные из каждой отдельной страницы-ссылки и записывать данные в excel-файл.




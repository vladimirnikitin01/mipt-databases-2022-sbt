# mipt-databases-2022-sbt_HW_1
#*Отчет домашняя работа №1. MongoDB*


1.  Для начала мы установили MongoDB и MongoDB Compass, последний понадобится для визуализации нашей работы. 

Затем нам надо заполнить ее каким-то датасетом. Возьмем игрушечный датасет из пары строчек и попробуем вывести максимальный возраст или заменить возраст только у одного человека, кототорого отберем по имени.

![image.png](https://github.com/vladimirnikitin01/mipt-databases-2022-sbt_HW_1/blob/screenshots/1.png)
![image.png](https://github.com/vladimirnikitin01/mipt-databases-2022-sbt_HW_1/blob/screenshots/2.png)
![image.png](https://github.com/vladimirnikitin01/mipt-databases-2022-sbt_HW_1/blob/screenshots/3.png)
#Теперь 2 пункт.

Скажем классический датасет https://www.cs.toronto.edu/~delve/data/boston/bostonDetail.html и скачаем его здесь https://www.kaggle.com/puxama/bostoncsv/version/1

![image.png](https://github.com/vladimirnikitin01/mipt-databases-2022-sbt_HW_1/blob/screenshots/4.png)
#Написать несколько запросов на выборку и обновление данных;

В данном датасете набор данных о жилье в Бостоне основан на информации, собранной Службой переписи населения США о жилье в районе Бостона, Массачусетс.

Тут есть довольно интересный параметр CRIM (уровень преступности на душу населения по городам). Давайте найдем самый криминальный район и выведем информацию о нем.



![image.png](https://github.com/vladimirnikitin01/mipt-databases-2022-sbt_HW_1/blob/screenshots/5.png)
А вот самый некриминальный 


![image.png](https://github.com/vladimirnikitin01/mipt-databases-2022-sbt_HW_1/blob/screenshots/6.png)
Сразу видна разница, две величины довольно хорошо иллюстрирует возможную причину в разных уровнях криминала. Это INDUS и AGE - proportion of owner-occupied units built prior to 1940. Это пример того, что в районе с менее высоким уровнем криминала у нас меньше доля зданий, построенных до 1940 года, а также меньше доля неторговых площадей. (чем больше торговли+новых зданий, тем лучше)


Давайте более подробно посмотрим на RAD - индекс доступности к радиальным магистралям. Сначала выведем все строчки(id+значение rad)

![image.png](https://github.com/vladimirnikitin01/mipt-databases-2022-sbt_HW_1/blob/screenshots/7.png)
А затем давайте поймем какие максимальные и минимальные принимает значения.


![image.png](https://github.com/vladimirnikitin01/mipt-databases-2022-sbt_HW_1/blob/screenshots/8.png)

![image.png](https://github.com/vladimirnikitin01/mipt-databases-2022-sbt_HW_1/blob/screenshots/9.png)

Всего таких 306 элементов

![image.png](https://github.com/vladimirnikitin01/mipt-databases-2022-sbt_HW_1/blob/screenshots/10.png)

Теперь выведем только те, у кого меньше или равно 2, то мы присвоим значение 3. 


![image.png](https://github.com/vladimirnikitin01/mipt-databases-2022-sbt_HW_1/blob/screenshots/11.png)

В итоге получили вот такой результат


![image.png](https://github.com/vladimirnikitin01/mipt-databases-2022-sbt_HW_1/blob/screenshots/12.png)


4. Создать индексы и сравнить производительность.


Давайте выберем не самую тривиальную работу, возмем запрос, где мы выводили, если нужный нам признак был зажат между 2 значениями.

![image.png](https://github.com/vladimirnikitin01/mipt-databases-2022-sbt_HW_1/blob/screenshots/13.png)



Вот такой результат мы получили без создания индексов. 
Давайте создадим их и заново посчитаем, в таком случае мы получим вот такой результат. 



![image.png](https://github.com/vladimirnikitin01/mipt-databases-2022-sbt_HW_1/blob/screenshots/14.png)


![image.png](https://github.com/vladimirnikitin01/mipt-databases-2022-sbt_HW_1/blob/screenshots/15.png)
Посмотрим на параметр executionTimeMillis. Без индексов он был равен 4, во втором уже 0(понятно, что это около 0). Также по другим параметрам хорошо видно, что индексирование уменьшает время запросов 


# mipt-databases-2022-sbt_HW_4
## Отчет домашняя работа №4, Jackrabbit 

В данно домашей задаче нам надо разобраться с данной СУБД и подробно ответить на множество вопросов, которые помогут составить более подробное описание нашей СУБД. Давайте, начнем.

**a)История развития СУБД**

 хранилище содержимого с открытым исходным кодом для платформы Java. Проект Jackrabbit был начат 28 августа 2004 года (но первые идеи были еще в 2002), когда компания Day Software начала разработку реализации API хранилища содержимого для Java (JCR). Jackrabbit также был использован как пример реализации JSR-170 и JSR-283. Проект вышел из «инкубатора» Apache 15 марта 2006 года и сейчас является проектом верхнего уровня в Apache Software Foundation. Надо отметить, что примерно каждые 2 недели появляются новые выпуски, причем некоторые из них являются нестабильными или выпусками дополнительны функций, так что разработчики постоянно занимимаются расширением и улучшением нынешних версий. Последняя стабильная версия вышла 2 марта 2022 г.


[Загрузка и версии Apache Jackrabbit](https://jackrabbit.apache.org/jcr/downloads.html)

**b)Инструменты для взаимодействия с СУБД**

На официальном сайте написано следующее: разработчики используют различные инструменты для помощи в работе, такие как IntelliJ IDEA или Eclipse. Большинство инструментов не требуют указания атрибуции, но некоторые требуют (YourKit Java Profiler). Хотелось бы немного рассказать про каждую из выше перечисленных. [Eclipse](https://www.eclipse.org/) служит в первую очередь платформой для разработки расширений, чем он и завоевал популярность: любой разработчик может расширить Eclipse своими модулями. [IntelliJ IDEA](https://www.jetbrains.com/opensource/idea/) — интегрированная среда разработки программного обеспечения для многих языков программирования, в частности Java, JavaScript, Python, разработанная компанией JetBrains. [YourKit Java Profiler](https://www.yourkit.com/benefits/#:~:text=YourKit%20Java%20Profiler%20is%20the,simply%20unrivaled%20but%20absolutely%20unique.) — это ведущий инструмент профилирования на рынке Java, предоставляющий самые инновационные, мощные и интеллектуальные возможности анализа производительности.

**c)Какой database engine используется в вашей СУБД?**

Приложения контента взаимодействуют через API JSR-170 с реализацией репозитория контента. Существует множество приложений, доступных для репозиториев JSR-170, некоторые из них очень общие (например, сервер WebDAV), другие приложения могут быть очень специфичными и использовать репозиторий контента в качестве хранилища информации, используемой приложениями.Java-приложения могут использовать репозиторий содержимого JSR-170 в качестве замены чего угодно, от файлов свойств, XML-конфигурации, определенных частей функциональности реляционной базы данных до прямой файловой системы или управления большими двоичными объектами.

Репозиторий на основе контента — это иерархическое хранилище контента, в котором собраны структурированный и неструктурированный контент, полнотекстовый поиск, наблюдение за транзакциями управления версиями и многое другое.

![image](https://user-images.githubusercontent.com/58188954/166662155-21b750df-6b9a-4676-b70b-51b1542f27fc.png)

Также давайте более подробно рассмотрим [архитектуру](https://jackrabbit.apache.org/jcr/jackrabbit-architecture.html)

![image](https://user-images.githubusercontent.com/58188954/166662841-8c44eec7-0795-4637-bda4-2a8e0177129c.png)

**d)Как устроен язык запросов в вашей СУБД? Разверните БД с данными и выполните ряд запросов. **

Язык запросов - JCR (в примерах буду использовать именно его), также есть версии Jackrabbit для работы с JCR-SQL2(вот тут будет уже обычный удобный и привычный для синтаксис. 
Для начала для установки нам скачать [файлы](https://jackrabbit.apache.org/jcr/downloads.html) или можно установить через терминал (мы поступим именно так)![image](https://user-images.githubusercontent.com/58188954/166663782-944208f6-6235-496c-98b8-15e120db0858.png)

Как мы помним с самого начала, Jackrabbit является примером реализации jcr. Можно использовать удобные оболочки для работы с Jackrabbit, но можно писать команды и с помощью java, давайте рассмотрим самые базовые примеры.

*Создадим хранилище содержимого Jackrabbit и начнем сеанс входа в систему для доступа к нему.*

![image](https://user-images.githubusercontent.com/58188954/166677915-1ba07498-6ac7-48ad-bf5c-714833f7367f.png)

*Давайте покажем код для примера, когда мы будем сохранять "Hello, World!"+извлекать+удалять.*

![image](https://user-images.githubusercontent.com/58188954/166678578-0fd9257f-efe1-4940-b974-f2ace5800d97.png)

*Но понятно, что нам надо уметь загружать уже готовые данные, давайте создадим test.xml с рандомными числами (для этого подойдет python), а затем заимпортим данный файл*

![image](https://user-images.githubusercontent.com/58188954/166680061-3e62eef8-dd73-4afb-94f2-369fba68af58.png)

Также понятно, что из-за популярности и большой гибкости java мы можем делать почти любую обработку данных и другие манипуляции.
Хорошие примеры есть вот [тут](https://ru.bmstu.wiki/Apache_Jackrabbit#.D0.9D.D0.B0.D1.87.D0.B0.D0.BB.D0.BE_.D1.80.D0.B0.D0.B1.D0.BE.D1.82.D1.8B_.D1.81_Apache_Jackrabbit) и [тут](https://jackrabbit.apache.org/archive/wiki/JCR/ExamplesPage_115513397.html).


**e)Распределение файлов БД по разным носителям?**

На официальном сайте информации по этому вопросу не нашёл, но я нашел информацию насчет [CacheManager](https://jackrabbit.apache.org/archive/wiki/JCR/CacheManager_115513375.html).CacheManager управляет размером кешей, используемых в Jackrabbit. Общий размер всех кэшей должен быть ограничен, чтобы избежать проблем с нехваткой памяти. Без CacheManager у Jackrabbit может закончиться нехватка памяти, потому что объединенный размер различных кэшей не управляется. Этот механизм не является окончательным решением. Также максимальный размер всех кешей в CacheManager по умолчанию составляет 16 мегабайт, но его можно изменить. Доступная память динамически распределяется по кешам максимум каждую секунду. CacheManager пытается вычислить наилучшие размеры кэша, сравнивая количество обращений к каждому кэшу и используемую память. 

**f)На каком языке/ах программирования написана СУБД?**

JAVA


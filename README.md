# Анализ базы вакансий из HeadHunter

## Цель проекта
Анализ базы вакансий компании HeadHunter с целью последующего создания рекомендательной модели машинного обучения для клиентов, претендующих на позицию Data Scientist.

## Задачи проекта
Реализация поставленной цели предусматривает решение следующих задач:

1) знакомство с данными;
2) предварительный анализ данных;
3) детальный анализ вакансий;
4) анализ работодателей;
5) предметный анализ.


## Реализация проекта

### Знакомство с данными
Данные представлены 5-ю таблицами в схеме public базы данных project_sql:
* vacancies - данные по вакансиям 
* areas - хранит код города и его название
* employers - список работодателей
* industries - сферы деятельности работодателей
* employers_industries - организует связь между работодателями и сферами их деятельности

### Предварительный анализ данных
* В базе содержится информация о 49197 вакансиях в 294 сферах деятельности. 
* Соотношение количества работодателей к количеству вакансий близко к 1:2. 
* Воспользоваться базой для поиска работы/кандидатов на должность могут предствавители более 1300 регионов.

### Детальный анализ вакансий
* Города-лидеры по количеству вакансий предсказуемо - столицы (в настоящем или прошлом) стран таможенного союза
* Из всех представленных вакансий только в половине указана информация о з/п. Для ее прогнозирования для другой половины необходим анализ выборки с указанными значениями в привязке к признаками Опыт работы, Регион, Сфера деятельности, тип трудоустройства.
* Усредненный диапазон указанных з/п для выборки составляет 71000-110000. Цифры несут мало полезной информации без привязки к опыту работы, сфере деятельности, региону. 
* Наиболее популярным сочетанием типа рабочего графика с типом трудоустройства является "Полный день/полная занятость" 
* Более половины вакансий относится к кандидатам с опытом работы 1-3 года. С точки зрения работодателя это оправданный подход, т.к. позволяет найти  кандидатов, способных со старта выполнять обязанности, при этом претендующие на меньший, по сравнению с опытными кандидатами, уровень з/п: средняя з/п у кандидатов с опытом > 6 лет превышает зарплату кандидатов с опытом 1-3 года более чем в два раза (query_tot_1/avg_total). 

### Анализ работодателей
* В среднем работодатели указывают 2 сферы деятельности, максимум: 16. 
* 35% работодателей не указали сферу деятельности. Возможно агрегатору есть смысл сделать это поле обязательным для заполнения. 
* Около 15% работодателей занимаются разработкой ПО, что подтверждает востребованность специалистов этой сферы.
* Лидерами по количеству вакансий являются крупные компании с распределенной сетью офисов: Яндекс, Ростелеком, Тинькофф, Сбер, Газпром нефть. Абсолютный лидер - Яндекс, на долю которого приходится около 4% всех представленнных вакансий; эта компания занимается рекрутингом во всех городах-милионниках РФ.
* Среди регионов без вакансий наибольшее количество работодателей наблюдается в крупных географических структурах уровня страны, области. Что может показаться достаточно странным и, скорее всего, говорит о нецелесообразности использования такого типа регионов для описания вакансий: указание конкретного города более информативно

### Предметный анализ
* Около 1/3 всех вакансий, касающихся данных, имеют отношение к DS - это примерно 1% всех вакансий в базе НН.
* Около 10% вакансий для DS являются подходящими для кандидатов начального уровня; относительно небольшой процент от общего количества (483) говорит о том, что в основном работодатели ориентируются на кандидатов с опытом, но не слишком опытных (отсутствует запрос на опыт > 6 лет). Показательно, что уровень з/п указан только в 13% вакансий для DS; возможно, з/п согласовывается по результату собеседования и оценки навыков кандидата, которые могут сильно варьировать у кандидатов одного уровня.
* SQL&Postgres и Python указаны в качестве ключевых навыков в 42% и 72% DS-вакансий соответственно. Высокий процент подчеркивает важность этих навыков для эффективной работы кандидатов.
* Показательно среднее количество навыков, указанных в DS-вакансиях: 6.4. Это говорит о том, что работодатели заинтересованы в найме мультипрофильных специалистов, имеющих в активе не только Python/SQL.  

## Использованные инструменты и библиотеки
* pandas 2.0.1
* psycopg2 2.9.6
* requests 2.25.1
* SQLAlchemy 2.0.17
* beautifulsoup4 4.12.2



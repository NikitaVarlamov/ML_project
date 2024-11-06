# Bike rental service. <br>Analysis of demand factors using ML
В этом проекте мы будем анализировать данные сервиса проката велосипедов в Корее с помощью методов машинного обучения, чтобы понять, от чего зависит спрос на эту услугу. 
### 1. Постановка цели и задач
#### Data

Работаем с [данными](https://raw.githubusercontent.com/obulygin/content/main/SeoulBike/seoul_bike_data.csv) сервиса проката велосипедов в Корее за год.<br>
| Column Name | Description |
|:--:|:--|
| Date | дата | 
| *Rented Bike Count* |  *сколько велосипедов было взято в прокат, целевая переменная* | 
| Hour | час дня |
| Temperature | температура воздуха в градусах Цельсия |
| Humidity | влажность воздуха |
| Wind Speed | скорость ветра в м/с |
| Visibility | мера различимости объектов на расстоянии в 10 метров |
| Dew point temperature | температура, зарегистрированная в начале дня, в градусах Цельсия |
| Solar Radiation | интенсивность солнечного света |
| Rainfall | количество осадков в мм |
| Snowfall | количество выпавшего снега в мм |
| Seasons | время года |
| Holiday | является ли день праздничным |
| Functioning Day | маркер, работал ли сервис проката в указанное время |

#### Цель
>*Изучить данные и выявить факторы влияющие на спрос велосипедов.*

#### Задачи
1) Провести предобработку данных: проверить данные на наличие выбросов, ошибочных значений, пропусков, дубликатов и некорректных типов.  
2) Провести EDA: реализовать все уровни анализа (одномерные/многомерные) с использованием визуализаций, изучить распределения и взаимосвязь признаков.  
3) Подготовить данные для построения модели (кодирование признаков, масштабирование, разбиение выборки на обучающую и тестовую).  
4) Реализовать базовую регрессионную модель прогнозирования количества велосипедов, взятых в прокат.  
5) При помощи инструментов Feature Selection и подбора гиперпараметров подобрать наилучшую прогнозную модель по adjusted R2 (основная метрика) и RMSE.

### 2. Загрузка и подготовка данных
В данной работе использованы следующие библиотеки для обработки данных, визуализации и применения инструментов машинного обучения. 

<html>
 <head>
  <meta charset="utf-8">
  <title>Изображения</title>
  <style>
   figure {
    width: 14.2%; /* Ширина */
    float: left; /* Выстраиваем элементы по горизонтали */
    margin: 0 0 0 1.5%; /* Отступ слева */
    background: #f0f0f0; /* Цвет фона */
    border-radius: 5px; /* Радиус скругления */
    padding: 2%; /* Поля */
    border: thin silver solid
   }
   figure:first-child {
    margin-left: 0; /* Убираем отступ для первого элемента */
   }
  </style>
 </head>
 <body>
  <figure>
   <img src="http://surl.li/ljrouh" alt="Pandas" width="100%">
  </figure>
    <figure>
   <img src="http://surl.li/rmmjsl" alt="NumPy" width="100%">
  </figure>
    <figure>
   <img src="http://surl.li/dglobo" alt="Matplotlib" width="100%">
  </figure>
  <figure>
   <img src="http://surl.li/ogsgxq" alt="Seaborn" width="100%">
  </figure>
  <figure>
   <img src="http://surl.li/dzlrpp" alt="Scikitlearn" width="100%">
  </figure>
 </body>
</html>

&nbsp;
Теперь приступим к подготовке данных.
В первую очередь выведем значения в момент, когда прокат не работал и увидим следующее:
```python
За время наблюдений сервис проката не работал 295 часов
      Rented Bike Count Functioning Day
3144                  0              No
3145                  0              No
3146                  0              No
3147                  0              No
3148                  0              No
...                 ...             ...
8251                  0              No
8252                  0              No
8253                  0              No
8254                  0              No
8255                  0              No

[295 rows x 2 columns]
```
Целевая переменная в этот период равна нулю, т.о. данные не информативны и при дальнейшем анализе датасета могут привести к искажению результатов. Нулевое значение целевой переменной приведет к смещению средней в меньшую сторону. Удалим эти строчки.

Также заметим, что датасет содержит информацию о дате аренды транспорта в формате DD/MM/YYYY, что затруднит дальнейший анализ данных - разобьём его на отдельные признаки (год, месяц, день, день недели).



### Workflow stages

The competition solution workflow goes through seven stages described in the Data Science Solutions book.
1. Question or problem definition
2. Wrangle, prepare, cleanse the data
3. Exploratory Data Analysis
4. Acquire training and testing data
5. Model, predict and solve the problem

### 1. Question or problem definition

The competition is simple: Use the Titanic passenger data (name, age, price of ticket, etc.) to try to predict who will survive and who will die. This is a binary classification.

Binary classification is the task of classifying the elements of a set into two groups on the basis of a classification rule.

The values in the second column (“Survived”) can be used to determine whether each passenger survived or not:
if it’s a “1”, the passenger survived.
if it’s a “0”, the passenger died.


### 2. Wrangle, prepare, cleanse the data
Here is my workflow for cleaning the data. I am not going to show all the step here, you can check my Kaggle for full code. Check my Kaggle and GitHub to took a look at all my projects🍀

### 3. Exploratory Data Analysis
Analyze, identify patterns, and explore the data Analysis
![alt text](https://miro.medium.com/max/630/1*xzS2rilv6HeCRGVx8CN_bQ.png)

Only 350 out of 891 passengers (38.4%) survived in the training set.
![alt text](https://miro.medium.com/max/630/1*y8pxlriPY1hXTGQIuuPhzQ.png)
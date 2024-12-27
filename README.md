# Bike rental service. <br>Analysis of demand factors using ML

В этом проекте мы будем анализировать данные сервиса проката велосипедов в Корее с помощью методов машинного обучения, чтобы понять, от чего зависит спрос на эту услугу.

### Постановка цели и задач

#### Data

Работаем с данными сервиса проката велосипедов в Корее за год.<br>

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
>
>*Изучить данные и выявить факторы влияющие на спрос велосипедов.*

#### Задачи

1) Провести предобработку данных: проверить данные на наличие выбросов, ошибочных значений, пропусков, дубликатов и некорректных типов.  
2) Провести EDA: реализовать все уровни анализа (одномерные/многомерные) с использованием визуализаций, изучить распределения и взаимосвязь признаков.  
3) Подготовить данные для построения модели (кодирование признаков, масштабирование, разбиение выборки на обучающую и тестовую).  
4) Реализовать базовую регрессионную модель прогнозирования количества велосипедов, взятых в прокат.  
5) При помощи инструментов Feature Selection и подбора гиперпараметров подобрать наилучшую прогнозную модель по adjusted R2 (основная метрика) и RMSE.

#### Инструменты

В данной работе использованы следующие библиотеки для обработки данных, визуализации и применения инструментов машинного обучения.

<div style="display: flex; flex-wrap: wrap;">
  <img src="http://surl.li/ljrouh" alt="Pandas" width="100" style="border: 1px solid #7F7F7F; border-radius: 10px; padding: 5px; background-color: #f0f0f0;">

  <img src="http://surl.li/rmmjsl" alt="NumPy" width="100" style="border: 1px solid #7F7F7F; border-radius: 10px; padding: 5px; background-color: #f0f0f0; margin-left: 10px">

  <img src="http://surl.li/kwwpnj" alt="Matplotlib" width="100" style="border: 1px solid #7F7F7F; border-radius: 10px; padding: 5px; background-color: #f0f0f0; margin-left: 10px">

  <img src="https://user-images.githubusercontent.com/315810/92254613-279c8000-ee9f-11ea-9b73-5622a7d95f3f.png" alt="Seaborn" width="100" style="border: 1px solid #7F7F7F; border-radius: 10px; padding: 5px; background-color: #f0f0f0; margin-left: 10px">

  <img src="https://seeklogo.com/images/S/scikit-learn-logo-8766D07E2E-seeklogo.com.png" alt="Scikitlearn" width="100" style="border: 1px solid #7F7F7F; border-radius: 10px; padding: 5px; background-color: #f0f0f0; margin-left: 10px">
</div>
&nbsp;

### Результаты работы
В качестве целевой метрики был принят cкорректированный (adjusted) R<sup>2</sup>. 
Наилучший результат показало применение ансамблевого алгоритма Gradient Boosting в паре с инструментами Pipeline и Grid Search, а именно:
1) полиномиальная регрессия 3 степени adj.R<sup>2</sup> = 0.821
2) ансамбль GradientBoosting adj.R<sup>2</sup> = 0.917

Остатки по итоговой модели распределены нормально, что говорит о хорошем качестве построения модели.
<img src="https://i.ibb.co/xDCPRx6/output.png" alt="output" border="0">

**Подробнее с работой можно ознакомиться в формате [notebook](https://github.com/NikitaVarlamov/ML_project/blob/main/Bikerentalservice.ipynb) или [pdf](https://github.com/NikitaVarlamov/ML_project/blob/main/Bikerentalservice.pdf).**

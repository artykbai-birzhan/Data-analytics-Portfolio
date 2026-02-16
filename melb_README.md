<img width="900" height="639" alt="png-clipart-melbourne-skyline-city-building-illustration" src="https://github.com/user-attachments/assets/ea9ded3c-83d3-40a1-8110-2964b2a66d38" />


Melbourne Housing Market: Price Drivers & Predictive Analysis

Project Overview

Цель этого проекта — выявить ключевые факторы, влияющие на стоимость жилья в Мельбурне, и подготовить данные для построения прогнозных моделей. Рынок недвижимости Мельбурна характеризуется высокой волатильностью, и понимание значимых признаков (features) помогает инвесторам и покупателям принимать обоснованные решения.

Tech Stack

Language: Python 3

Libraries: Pandas, NumPy (обработка данных), Matplotlib, Seaborn (визуализация).

Key Project Stages

1. Data Cleaning & Preprocessing

Датасет содержал значительное количество пропусков и выбросов. Были выполнены следующие шаги:

Missing Values: Заполнение пропусков в числовых признаках (BuildingArea, YearBuilt) медианой, а в категориальных — модой.

Outlier Removal: Удаление аномально высоких цен (выше 99-го перцентиля) для повышения стабильности будущих моделей.

Data Formatting: Преобразование дат в формат datetime для извлечения временных признаков.

2. Feature Engineering

Для улучшения качества анализа были созданы новые производные признаки:

HouseAge: Возраст здания на момент 2025 года.

RoomDensity: Соотношение количества комнат к площади участка.

Time Features: Выделение года (SaleYear) и месяца (SaleMonth) продажи.

3. Exploratory Data Analysis (EDA)

В ходе анализа были визуализированы:

Корреляция между ценой и физическими характеристиками (Building Area, Rooms).

Распределение цен в зависимости от региона (Regionname) и типа недвижимости.

Влияние географического положения (Lattitude, Longtitude) на стоимость.

Results & Insights

Location Matters: Регион проживания и близость к центру города являются наиболее сильными предикторами цены.

Size vs Price: Обнаружена сильная положительная корреляция между жилой площадью (BuildingArea) и итоговой стоимостью.
<img width="691" height="470" alt="pp" src="https://github.com/user-attachments/assets/6bab2257-58dc-4e8f-8923-1ccd209448b6" />

Age Factor: Новые постройки и исторические здания ценятся выше, чем дома среднего возраста (U-образная зависимость).

<img width="1008" height="920" alt="HH" src="https://github.com/user-attachments/assets/3aead91a-9ea3-49d4-9bb1-7d2214bdccf4" />


Repository Structure
melbourne_housing.ipynb — основной Jupyter Notebook с процессом очистки и анализа.

melb_data.csv — исходный датасет.

Melbourne_cleaned.csv — очищенные данные, готовые для Machine Learning.

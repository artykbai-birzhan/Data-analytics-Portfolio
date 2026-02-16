<img width="300" height="168" alt="images-3" src="https://github.com/user-attachments/assets/865f4e9a-2caf-4036-a5ee-53f5249f1a3f" />

Retail Business Analytics: Customer Value & Retention Study

Project Overview
В данном проекте проведен глубокий анализ данных розничных продаж (Dataset: Superstore). Основная цель — перейти от простого отслеживания выручки к анализу Unit-экономики и поведения клиентов. Проект включает расчет ключевых метрик лояльности и долгосрочной ценности клиентов.

Tech Stack
Language: Python

Libraries: Pandas (Data Manipulation), Seaborn & Matplotlib (Data Visualization).

Key Analytics & Metrics
В ходе работы были реализованы следующие аналитические задачи:

Customer Lifetime Value (LTV): Расчет прогнозной прибыли от одного клиента на основе среднего чека, частоты покупок и жизненного цикла.
 <img width="939" height="474" alt="Screenshot 2026-02-16 at 19 17 19" src="https://github.com/user-attachments/assets/1d5ade53-f2f4-44cc-a579-9594468a98f3" />

Formula used: LTV = AOV * Purchase Frequency * Average Lifespan
 <img width="939" height="474" alt="Screenshot 2026-02-16 at 19 07 41" src="https://github.com/user-attachments/assets/af5ebc67-2e1a-41ee-ab75-8fbd8efe0fb6" />

Retention & Churn Analysis: Определение доли лояльных клиентов и расчет скорости оттока (Churn Rate).
 <img width="744" height="460" alt="Screenshot 2026-02-16 at 19 07 52" src="https://github.com/user-attachments/assets/beecd142-3fc7-4c11-9fca-c37d178fe950" />

Cohort Analysis: Анализ поведения групп клиентов во времени с использованием визуализации Heatmap.
 <img width="939" height="474" alt="Screenshot 2026-02-16 at 19 07 23" src="https://github.com/user-attachments/assets/f3c6eb35-ed5b-449e-8445-30d746031a42" />

Correlation Analysis: Исследование взаимосвязи между частотой покупок и общими затратами клиента.

Results & Insights
LTV: Средний показатель жизненного цикла клиента составил $7,939.30, что является важным ориентиром для стоимости привлечения клиента (CAC).

Retention: Уровень удержания составил рекордные 98.49%, что говорит о высокой лояльности текущей базы.

AOV: Средний чек заказа (Average Order Value) зафиксирован на уровне $458.61.

Business Recommendations
На основе полученных данных сформированы следующие рекомендации:

Loyalty Programs: Внедрение программ лояльности для сегмента клиентов с высокой частотой покупок, но средним чеком ниже среднего.

Marketing Focus: Оптимизация маркетинговых бюджетов в сторону удержания «High-Value» клиентов (топ по LTV).

Seasonal Strategies: Усиление промо-акций в периоды, когда наблюдается историческое снижение Retention Rate в когортах.

Project Structure
Superstore_python.ipynb — Jupyter Notebook с полным циклом обработки, расчетов и визуализации.

Superstore.csv — Исходный набор данных.

Superstore.md — Описание проекта.

# Анализ продаж E-Commerce маркетплейса Olist

Данный проект представляет собой комплексное исследование реальных данных бразильского 
маркетплейса Olist за 2016–2018 годы. В роли Data Analyst я провожу путь от очистки сырых данных до 
сегментации клиентов и проверки бизнес-гипотез.

## Задачи исследования
- Анализ динамики: выявить тренды выручки и определить сезонность.

- Товарная аналитика: найти самые прибыльные и дорогие категории товаров.

- Логистический аудит: оценить скорость доставки и выявить проблемные регионы.

- Сегментация клиентов: провести RFM-анализ и применить машинное обучение (K-Means) для профилирования аудитории.

- Анализ лояльности: определить влияние качества доставки на оценки пользователей.

## Стек технологий
- Язык: Python (Pandas, NumPy).

- Базы данных: SQLite (обработка данных через SQL-запросы прямо в ноутбуке).

- Визуализация: Matplotlib, Seaborn.

- Machine Learning: Scikit-learn (K-Means clustering, StandardScaler).

## Структура данных
ecommerce-analysis/
- │
- ├── olist_analysis.ipynb      # Main analysis notebook
- ├── README.md                 # Project documentation
- │
- ├── data/                     # Raw CSV files (download from Kaggle)
- │   ├── olist_orders_dataset.csv
- │   ├── olist_order_items_dataset.csv            
- │   ├── olist_customers_dataset.csv
- │   ├── olist_products_dataset.csv
- │   ├── olist_sellers_dataset.csv
- │   ├── olist_order_payments_dataset.csv
- │   ├── olist_order_reviews_dataset.csv
- │   └── product_category_name_translation.csv
- │
- ├── charts/                   # Auto-generated visualizations
- │   ├── 01_revenue_trend.png
- │   ├── 02_categories.png
- │   ├── 03_delivery.png
- │   ├── 04_delivery_dist.png
- │   ├── 05_rfm_segments.png
- │   ├── 06_elbow.png
- │   ├── 07_kmeans_clusters.png
- │   ├── 08_reviews.png
- │   └── 09_window_functions.png
- │
- └── olist.db                  # SQLite database (auto-generated)

## Структура 

- Block 1–2    Setup & Data Loading
- Block 3      Data Cleaning (dates, nulls, feature engineering)
- Block 4      SQLite Database Creation
- Block 5      Revenue Trend Analysis         ← SQL: GROUP BY, SUM
- Block 6      Product Category Analysis      ← SQL: multi-table JOIN
- Block 7      Delivery Performance           ← Histogram, geo analysis
- Block 8      RFM Customer Segmentation      ← pandas qcut, business logic
- Block 9      K-Means Clustering (ML)        ← sklearn, Elbow method
- Block 10     Review Score Analysis          ← Hypothesis testing, boxplot
- Block 11     Advanced SQL                   ← Window functions: LAG, RANK, PARTITION BY


## Основные этапы работы
1. Подготовка и SQL-трансформация
Данные были загружены в базу SQLite. Для расчёта сложных бизнес-метрик (например, Running Total и Month-over-Month рост) использовались продвинутые возможности SQL, включая оконные функции.

2. RFM-сегментация
Клиенты были разделены на группы по трем классическим метрикам:

- Recency (Давность покупки).

- Frequency (Частота заказов).

- Monetary (Суммарные траты).
Это позволило выделить сегменты "Чемпионов", "Лояльных" и "Группы риска".

3. Кластеризация (K-Means)
С помощью алгоритма машинного обучения были автоматически выделены кластеры клиентов. Для определения оптимального количества групп использовались методы Elbow Method (метод локтя) и Silhouette Score.

Ключевые выводы
- Рост бизнеса: Выявлен стабильный рост выручки с пиком в ноябре (Black Friday).

- Проблемы логистики: Около 10% заказов доставляются с опозданием, что критически снижает средний рейтинг (с 4.2 до 2.3 баллов).

- География: Северные штаты Бразилии имеют самое долгое время ожидания (до 20+ дней), что требует открытия локальных складов.

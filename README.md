# Анализ обратной связи онлайн-курсов
---

Этот проект был разработан в рамках хакатона "Цифровой прорыв: сезон ИИ" (Центральный ФО, 2023).
Он представляет собой модуль машинного обучения для анализа отзывов об онлайн-курсах GeekBrains.
---

## Основные задачи проекта

Модуль анализирует отзывы по следующим параметрам:

 - **Определение тональности**: классификация отзыва на положительный или отрицательный.

 - **Определение полезности**: выявление наличия конструктивной информации в отзыве.

 - **Определение объекта отзыва**: категоризация содержания отзыва на компоненты образовательного процесса (программа курса, преподаватель, платформа).

## Используемые технологии

1. **Предобработка текста**

 - Лемматизация и удаление стоп-слов с применением библиотек NLTK и spaCy.

 - Очистка текста от нежелательных символов и стандартизация представления данных.

2. **Векторизация текста**

 - BERT (Bidirectional Encoder Representations from Transformers) – использован для построения высокоуровневых текстовых эмбеддингов и классификации.

 - Word2Vec – применялся для обучения собственных векторных представлений слов на данных отзывов.

3. **Классификация отзывов**

 - Модель на основе BERT – дообучена на размеченных данных для предсказания тональности, полезности и тематической направленности отзыва.

 - Методы классического машинного обучения из Sklearn – использовались для базовой классификации с целью сравнения с нейросетевыми подходами.
   

## Структура пайплайна

1. Загрузка и предобработка данных.
2. Векторизация текстов (BERT или Word2Vec).
3. Обучение моделей классификации.
4. Предсказание характеристик отзывов.
5. Оценка качества модели и интерпретация результатов.

## Подход к обучению и настройке параметров

 - Обучение BERT осуществлялось с использованием Hugging Face Transformers. В рамках дообучения подбирались параметры, включая скорость обучения (learning_rate) и размер пакета (batch_size), с целью балансировки скорости сходимости и качества классификации.

 - Word2Vec применялся для представления слов в векторном пространстве. Оптимизировались гиперпараметры: размерность векторов (vector_size), минимальная частота встречаемости слов (min_count), а также размер контекстного окна (window).

 - Метрики качества включали accuracy, precision, recall и F1-score. Оценивались кривые обучения, выявлялось переобучение и возможные области для улучшения модели.

---

Проект демонстрирует применение современных методов обработки естественного языка для анализа обратной связи. Достигнутая архитектура обладает гибкостью в адаптации к различным категориям текстовых данных. Возможными направлениями улучшения являются дообучение моделей на специфических данных, использование дополнительных слоев трансформеров и внедрение методов интерпретации результатов моделей.

Для более детального изучения кода см. ноутбуки text_classification_BERT.ipynb (обучение модели is_positive) и full_pipeline.ipynb (обучение модели is_relevant и инференс).

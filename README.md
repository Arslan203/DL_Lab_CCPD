# Лабораторная курса Deep Learning

## Общее описание
Системы распознавания автомобильных номеров состоят из двух модулей: детекция и распознавание символов (Optical Character Recognition, OCR). Детектор выделяет прямоугольник с номером из изображения, а OCR конвертирует его в текст. Будем считать, что детектор уже реализован. В рамках проекта предлагается самостоятельно обучить модель OCR для автомобильных номеров.

**Пример входа:** 
![Автомобильный номер](https://algocode.ru/files/course_dlfall22/number.png)

**Пример выхода:** 皖AD16688

## Предлагаемая архитектура решения
Предлагается реализовать модель, состоящую из двух блоков: Fully-convolutional CNN (FCNN) и Bi-LSTM. На выходе предлагается использовать Cross-entropy. 

Пример архитектуры:

![Архитектура](https://algocode.ru/files/course_dlfall22/architecture.png)

## Корпус данных
Предлагается использовать корпус [CCPD2019](https://github.com/detectRecog/CCPD). В test вошли изображения из CCPD-weather. Подготовленный корпус можно скачать по [ссылке](https://disk.yandex.ru/d/adjYzzNayB1pag).

## Что включает работа
Для сдачи проекта нужно подготовить ноутбук с решением. В каждом решении должны быть описанные ниже блоки.
1. **Подготовка данных.** Реализован класс данных (наследник torch.utils.data.Dataset). Класс должен считывать входные изображения и выделять метки из имён файлов. Также реализован механизм аугментаций для повышения качества обучения.
2. **Создание и обучение модели.** Код реализован через слои стандартной библиотеки torch (torchvision.models и аналоги не использовались). Поскольку число символов в номерах фиксировано, можно использовать обычный кросс-энтропийный критерий. Цикл обучения был реализован самостоятельно.
3. **Подсчет метрик.** Качество модели оценивается по двум метрикам: accuracy и Character Error Rate (CER). Accuracy считает долю правильно распознанных номеров. CER оценивает число посимвольных ошибок.
4. **Анализ ошибок модели.** В этой секции нужно найти изображения из тестового корпуса, на которых модель ошибается сильнее всего (по loss или по CER). Выписаны возможные причины этих ошибок и пути их устранения.

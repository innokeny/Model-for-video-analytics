# Описание набора данных

В работе использовался подготовленный набор данных (https://www.kaggle.com/datasets/snehilsanyal/construction-site-safety-image-dataset-roboflow/data ), состоящий из изображений, полученный на различных промышленных объектах. 

Изображения разделены на 10 классов в соответствие с присутствием на них или отсутствие СИЗ: 
–	Hardhat (защитная каска),
–	Mask (маска),
–	NO-Hardhat (отсутствие защитной каски),
–	NO-Mask (отсутствие маски),
–	NO-Safety Vest (отсутствие жилета безопасности),
–	Person (человек),
–	Safety Cone (конус безопасности),
–	Safety Vest (жилет безопасности), 
–	Machinery (оборудование),
–	Vehicle (транспортное средство). 

При обучении и тестировании модели датасет был разделен на следующие выборки: 
–	обучающая – 2605 изображений,
–	валидационная – 114 изображений,
–	тестовая – 82 изображения. 

Разрешение используемых изображений составляет 640 на 640 пикселей.

Проведен анализ баланса классов в наборе данных для оценки распределения объектов по классам . Также был проведен анализ размеров изображений, чтобы убедиться в их однородности и возможной необходимости изменения размеров перед обучением модели. Этот анализ позволяет лучше понять данные, с которыми работает модель, и учесть особенности набора данных при обучении. Общее распределение классов между тренировочными, валидационными и тестовыми наборами данных схож, явный дисбаланс классов отсутствует.

![image](https://github.com/user-attachments/assets/97d0273a-5508-4148-bbc4-22c2526f16ea)

# Обучение моделей сверточной нейронной сети YOLOv8 Nano и Extra Large

Были обучены модели сверточной нейронной сети YOLOv8 Nano и Extra Large, достигшие метрик precision 0,86 и 0,91 соответственно. Обучение нейронной сети проводилось в среде для проведения облачных вычислений Google Collab на GPU NVIDIA Tesla T4. Было установлено 30 эпох обучения, размер пакета данных для одной итерации обучения составлял 32 изображения для YOLOv8 Nano и 16 изображений для YOLOv8 Extra Large. Для оценки качества работы модели на обучающей, валидационной и тестовой выборках использовались следующие метрики: precision, recall, mAP50 и mAP50-95.

**Nano**
![image](https://github.com/user-attachments/assets/19a32c1c-7011-4338-b036-a9eb86ccf1ac)

**Extra Large**
![image](https://github.com/user-attachments/assets/5f756f43-bca5-40b5-bd52-c9c5e5a80989)

Если система требует быстрой обработки данных с допустимыми погрешностями, предпочтение следует отдать YOLOv8 Nano. Если же приоритетом является точность распознавания объектов и можно позволить большую задержку, лучше использовать YOLOv8 Extra Large. Решение о выборе модели должно основываться на конкретных требованиях и ограничениях проекта.

# Демонстрация использования
![ezgif com-video-to-gif-converter](https://github.com/user-attachments/assets/b9a336f9-c56b-4aff-9138-c862e1aa5794)


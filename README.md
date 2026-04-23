# Underwater Plastics Detection

Лабораторная работа 1: обнаружение и распознавание объектов (мусор под водой).

## Датасет

[Underwater Plastics Pollution Dataset](https://www.kaggle.com/datasets/arnavs19/underwater-plastic-pollution-detection) — 15 классов подводного мусора: маски, банки, бутылки, шины, сети и др. 5130 изображений (train/val/test).

## Метрики

- **mAP50** — основная метрика детекции, IoU порог 0.5
- **mAP50-95** — усреднённая по порогам от 0.5 до 0.95
- **Precision / Recall** — точность и полнота

## Запуск

Ноутбук запускался в Google Colab с GPU (Tesla T4).

1. Открыть `cv_lab.ipynb` в Google Colab
2. Runtime → Change runtime type → GPU
3. Запустить все ячейки по порядку

## Зависимости

```bash
pip install ultralytics torch torchvision kaggle
```

## Структура

```
├── cv_lab.ipynb   # основной ноутбук
└── README.md
```

## Результаты

| Модель | mAP50 | mAP50-95 | Precision | Recall |
|--------|-------|----------|-----------|--------|
| Baseline (yolo11n, 5 эпох) | 0.4748 | 0.3076 | 0.7107 | 0.4011 |
| + Аугментации | 0.4474 | 0.2936 | 0.6550 | 0.4204 |
| + Крупная модель (yolo11s) | 0.5008 | 0.3174 | 0.7094 | 0.4341 |
| + Больше эпох (15) | 0.5573 | 0.3620 | 0.6496 | 0.4839 |
| Улучшенный baseline (yolo11s, 15 эпох) | 0.6435 | 0.4091 | 0.6638 | 0.6112 |
| Своя модель (15 эпох) | 0.0799 | 0.0154 | 0.0798 | 0.4979 |

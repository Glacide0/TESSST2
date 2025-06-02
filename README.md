# Классификатор грибов

Проект машинного обучения для классификации грибов с использованием PyTorch Lightning и лучших практик MLOps.

## Структура проекта

```
.
├── configs/               # Конфигурационные файлы с использованием Hydra
│   ├── preprocessing.yaml # Конфигурация предобработки данных
│   ├── model.yaml        # Конфигурация архитектуры модели
│   └── training.yaml     # Параметры обучения
├── data/                 # Директория с данными (версионируется с помощью DVC)
│   ├── raw/              # Исходные данные
│   └── processed/        # Обработанные данные
│       ├── train/
│       ├── val/
│       └── test/
├── models/               # Сохраненные модели
│   ├── checkpoints/      # Контрольные точки обучения
│   └── exported/         # Экспортированные модели (ONNX и т.д.)
├── logs/                 # Директория логов
│   ├── mlflow/           # Логи MLflow
│   └── tensorboard/      # Логи TensorBoard
├── mushroom_classifier/  # Основной пакет
│   ├── __init__.py
│   ├── data.py           # Загрузка и обработка данных
│   ├── model.py          # Определение модели
│   ├── train.py          # Код для обучения
│   ├── infer.py          # Код для вывода
│   └── utils.py          # Вспомогательные функции
├── scripts/              # Вспомогательные скрипты
│   ├── prepare_data.py   # Скрипт подготовки данных
│   ├── export_model.py   # Скрипт экспорта модели
│   └── run_server.py     # Скрипт запуска сервера вывода
├── .dvc/                 # Конфигурация DVC
├── .gitignore
├── pyproject.toml        # Зависимости проекта
├── .pre-commit-config.yaml # Хуки pre-commit
└── setup.py             # Скрипт настройки пакета
```

## Установка

```bash
# Клонирование репозитория
git clone https://github.com/username/mushroom-classifier.git
cd mushroom-classifier

# Создание виртуального окружения
python -m venv .venv
source .venv/bin/activate  # В Windows: .venv\Scripts\activate

# Установка зависимостей
pip install -e .

# Загрузка данных с помощью DVC
dvc pull
```

## Обучение

```bash
python -m mushroom_classifier.train
```

Или с пользовательской конфигурацией:

```bash
python -m mushroom_classifier.train --config-name=training.yaml +model.learning_rate=0.001
```

## Вывод

```bash
python -m mushroom_classifier.infer --image-path=path/to/image.jpg --model-path=models/exported/model.onnx
```

## Функции MLOps

- **Версионирование данных**: Использование DVC для версионирования данных и моделей
- **Отслеживание экспериментов**: Интеграция с MLflow для отслеживания экспериментов
- **Экспорт моделей**: Экспорт в ONNX/TensorRT для развертывания в продакшене
- **CI/CD**: GitHub Actions для автоматизации (линтинг, тестирование, сборка)
- **Контейнеризация**: Поддержка Docker для воспроизводимого окружения
- **Качество кода**: Хуки pre-commit для линтинга и форматирования

## Лицензия

MIT
# Mushroom Classifier

A machine learning project for mushroom classification using PyTorch Lightning and MLOps best practices.

## Project Structure

```
.
├── configs/               # Configuration files using Hydra
│   ├── preprocessing.yaml # Data preprocessing configuration
│   ├── model.yaml        # Model architecture configuration
│   └── training.yaml     # Training parameters
├── data/                 # Data directory (versioned with DVC)
│   ├── raw/              # Raw data files
│   └── processed/        # Processed data files
│       ├── train/
│       ├── val/
│       └── test/
├── models/               # Saved models
│   ├── checkpoints/      # Training checkpoints
│   └── exported/         # Exported models (ONNX, etc.)
├── logs/                 # Logs directory
│   ├── mlflow/           # MLflow logs
│   └── tensorboard/      # TensorBoard logs
├── mushroom_classifier/  # Main package
│   ├── __init__.py
│   ├── data.py           # Data loading and processing
│   ├── model.py          # Model definition
│   ├── train.py          # Training code
│   ├── infer.py          # Inference code
│   └── utils.py          # Utility functions
├── scripts/              # Utility scripts
│   ├── prepare_data.py   # Data preparation script
│   ├── export_model.py   # Model export script
│   └── run_server.py     # Inference server script
├── .dvc/                 # DVC configuration
├── .gitignore
├── pyproject.toml        # Project dependencies
├── .pre-commit-config.yaml # Pre-commit hooks
└── setup.py             # Package setup script
```

## Setup

```bash
# Clone the repository
git clone https://github.com/username/mushroom-classifier.git
cd mushroom-classifier

# Create a virtual environment
python -m venv .venv
source .venv/bin/activate  # On Windows: .venv\Scripts\activate

# Install dependencies
pip install -e .

# Pull data using DVC
dvc pull
```

## Training

```bash
python -m mushroom_classifier.train
```

Or with custom configuration:

```bash
python -m mushroom_classifier.train --config-name=training.yaml +model.learning_rate=0.001
```

## Inference

```bash
python -m mushroom_classifier.infer --image-path=path/to/image.jpg --model-path=models/exported/model.onnx
```

## MLOps Features

- **Data Versioning**: Uses DVC to version data and models
- **Experiment Tracking**: MLflow integration for tracking experiments
- **Model Export**: Exports to ONNX/TensorRT for production deployment
- **CI/CD**: GitHub Actions for automation (linting, testing, building)
- **Containerization**: Docker support for reproducible environments
- **Code Quality**: Pre-commit hooks for linting and formatting

## License

MIT

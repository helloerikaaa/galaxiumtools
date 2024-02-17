# Galaxium Tools
Minio Handler is a Python package designed to simplify interactions with Minio storage and streamline MLFlow experiments tracking. It provides easy-to-use classes for uploading, downloading, listing, and managing objects and buckets in Minio, as well as for managing MLFlow experiments and logging parameters, metrics, and artifacts.


## Installation
You can install Minio Handler via pip:

```bash
pip install galaxiumtools
```

## Features
- Minio Handler:
    * Create, list, and remove buckets in Minio storage
    * Upload, download, and list objects in Minio buckets
    * Upload entire folders to Minio storage while preserving directory structure
- MLFlow Handler:
    * Start, end, and manage MLFlow runs
    * Log parameters, metrics, and artifacts to MLFlow runs

## Usage

### Minio Handler
To use Minio Handler, import the `MinioHandler` class from the `galaxiumtools` module:
```python
from galaxiumtools.minio_handler import MinioHandler

# Initialize MinioHandler
minio_handler = MinioHandler(endpoint='minio.example.com:9000',
                             access_key='your-access-key',
                             secret_key='your-secret-key')

# Example usage
minio_handler.create_bucket('test-bucket')
minio_handler.upload_object('test-bucket', 'example.txt', '/path/to/local/file.txt')
print(minio_handler.list_buckets())
print(minio_handler.list_objects('test-bucket'))
minio_handler.remove_object('test-bucket', 'example.txt')
minio_handler.remove_bucket('test-bucket')
```

### MLFlow Handler
To use MLFlow Handler, import the `MLFlowHandler` class from the `galaxiumtools` module:
```python
from galaxiumtools.mlflow_handler import MLFlowHandler

# Initialize MLFlowHandler
mlflow_handler = MLFlowHandler(tracking_uri='http://mlflow.example.com')

# Example usage
mlflow_handler.start_run(run_name='experiment-1')
mlflow_handler.log_param('learning_rate', 0.001)
mlflow_handler.log_metric('accuracy', 0.85)
mlflow_handler.log_artifact('/path/to/local/file.txt')
mlflow_handler.end_run()
```
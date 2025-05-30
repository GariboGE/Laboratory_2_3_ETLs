# Practice: Comparison of Pandas and Spark

This repository contains a practice project comparing the **pandas** and **Spark** libraries using a dataset of Steam reviews. The goal is to analyze how both tools perform when processing large volumes of data.

## Dataset

The following dataset was used: [Steam Reviews Dataset (Kaggle)](https://www.kaggle.com/datasets/forgemaster/steam-reviews-dataset)

## Objective

Compare the performance and ease of use of pandas and Spark for:

- Data reading and loading.
- Data cleaning and preprocessing.
- Basic data analysis.
- Visualization of results.

## Docker Environment with Spark and JupyterLab

To facilitate the practice, a Docker-based environment was used, which includes:

- Apache Spark (Master + Worker)
- JupyterLab

### Prerequisites

- Docker
- Docker Compose

### Installation Instructions

1. Create the project structure:
    ```bash
    mkdir spark-jupyter-docker
    cd spark-jupyter-docker
    mkdir workspace
    ```

2. Place the configuration files in the project’s root directory.

3. Build and start the containers:
    ```bash
    docker-compose up --build
    ```

4. Access the web UIs:
    - JupyterLab: [http://localhost:8888](http://localhost:8888) (token: `token-uag`)
    - Spark Master UI: [http://localhost:8080](http://localhost:8080)
    - Spark Worker UI: [http://localhost:8081](http://localhost:8081)
    - Spark Application UI (when a Spark job is running): [http://localhost:4040](http://localhost:4040)

### Default Configuration

- Spark Master UI: [http://localhost:8080](http://localhost:8080)
- Spark Worker UI: [http://localhost:8081](http://localhost:8081)
- Spark Application UI: [http://localhost:4040](http://localhost:4040)
- Jupyter token: `token-uag`
- The workspace directory is mounted at `/workspace` in the container.
- Default Spark configuration:
  - Driver Memory: 1GB
  - Executor Memory: 1GB
  - Worker Cores: 1
  - Worker Memory: 1GB

### Basic Usage of PySpark

```python
from pyspark.sql import SparkSession

# Initialize the Spark session
spark = SparkSession.builder \
    .appName("SparkExample") \
    .master("spark://spark-master:7077") \
    .config("spark.driver.memory", "1g") \
    .config("spark.executor.memory", "1g") \
    .getOrCreate()

# Create a sample DataFrame
data = [("Alice", 25), ("Bob", 30), ("Charlie", 35)]
df = spark.createDataFrame(data, ["name", "age"])

# Show the DataFrame
df.show()
```

## Executive Report

The executive report with the findings and comparisons between pandas and Spark can be found in this repository in PDF format.

---

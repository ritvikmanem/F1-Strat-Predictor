# F1 Race Strategy Predictor

## 🚀 Overview
This project aims to predict optimal **Formula 1 race strategies** based on historical race data. It collects data from the **FastF1 API**, stores it in a **PostgreSQL database**, and trains a **PyTorch-based machine learning model** to analyze pit stops, tire strategies, and lap performance.

## 📁 Project Structure
```
f1_race_strategy/
│── data/
│   ├── raw/            # Raw CSVs from FastF1
│   ├── processed/      # Processed feature-engineered data
│── db/
│   ├── db_config.py    # Database connection settings
│   ├── create_tables.py  # Defines the PostgreSQL schema
│   ├── insert_data.py  # Loads data from CSV to PostgreSQL
│   ├── query_data.py   # Fetches data for model training
│── models/
│   ├── model.py        # PyTorch model definition
│   ├── train_model.py  # Trains the model using the database
│   ├── predict.py      # Makes predictions based on trained model
│── scripts/
│   ├── fetch_f1_data.py  # Uses FastF1 to get race data
│── main.py            # Main script to run the pipeline
│── requirements.txt   # Dependencies
│── README.md          # Project documentation
```

## 📊 Data Collection
The project fetches race data using the **FastF1 API**, including:
- Lap times
- Tire compounds
- Pit stops
- Weather conditions
- Driver performance statistics

### Setup FastF1 API
```bash
pip install fastf1 pandas
```
### Fetch Data Example
```python
import fastf1

df = fastf1.get_session(2023, 'Monza', 'R').laps
print(df.head())
```

## 🛢️ Database (PostgreSQL)
Race data is stored in a **PostgreSQL database** for structured querying and analysis.

### Setup PostgreSQL
```bash
sudo apt install postgresql
pip install psycopg2 sqlalchemy
```
### Create Database Schema
```bash
python db/create_tables.py
```
### Insert Data
```bash
python db/insert_data.py
```

## 🤖 Machine Learning Model (PyTorch)
A **PyTorch-based neural network** is trained on historical data to predict **optimal pit stop timing and tire strategy**.

### Install PyTorch
```bash
pip install torch torchvision torchaudio
```
### Train Model
```bash
python models/train_model.py
```

## 🎯 Prediction
Once trained, the model can predict **ideal pit stop strategies** for new races.
```bash
python models/predict.py
```

## 📌 Next Steps
- 🔄 **Automate data collection** after each race weekend
- 🏎️ **Feature Engineering**: Include weather conditions & track temperature
- 🧠 **Improve Model**: Try LSTMs or Transformers for time-series forecasting

## 🏁 Conclusion
This project applies **AI to motorsports**, helping teams and analysts optimize **Formula 1 race strategies**. Contributions and improvements are welcome!

# Item Sale Prediction App

This is a Flask-based web application that predicts the sale of a particular item based on the provided date and area. The app uses a trained machine learning model to make predictions and provides both individual and bulk prediction options.

## Features

- **Individual Prediction**: Enter a date, area, and item code to predict the sale of a specific item.
- **Bulk Prediction**: Upload a CSV file containing multiple records to predict sales for multiple items at once.
- **Interactive Web Interface**: User-friendly interface for input and result visualization.

## Model Overview

The machine learning model used in this application is a neural network built using Keras. The model was trained on historical sales data to predict the quantity of items sold based on the following features:

- Date (day, month, year, weekday, weekend)
- Area (encoded using `LabelEncoder`)
- Item code (encoded using `LabelEncoder`)
- Festival information (binary indicator)
- Cyclical features for the month (sine and cosine transformations)

The training process is detailed in the Jupyter notebook [`PipelineItemDatewise.ipynb`](PipelineItemDatewise.ipynb).

## Project Structure

.
├──application.py # Flask application
├──PipelineItemDatewise.ipynb # Jupyter notebook for model training
├── templates/ # HTML templates for the web interface
│ ├── file.html
│ ├── index.html
│ ├── input.html
│ ├── single.html
│ ├── uploadcsv.html
├── uploads/ # Directory for uploaded CSV files
├── item_model.pkl # Trained model file
├── item_encoder_area.pkl # Area encoder
├── item_encoder_item.pkl # Item code encoder
├── item_scaler.pkl # Scaler for feature normalization
├── festivals.pkl # Festival data
├── requirements.txt # Python dependencies
└── README.md # Project documentation

## Installation

1. Clone the repository:

   ```bash
   git clone https://github.com/your-username/item-sale-prediction.git
   cd item-sale-prediction

   ```

2. Install the required dependencies:

   ```bash
   pip install -r requirements.txt
   ```

3. Ensure the following files are present:
   - item_model.pkl: Trained model
   - item_encoder_area.pkl: Area encoder
   - item_encoder_item.pkl: Item code encoder
   - item_scaler.pkl: Scaler for feature normalization
   - festivals.pkl: Festival data

## Usage

1. Start the Flask application:

   ```bash
   python application.py
   ```

2. Open your browser and navigate to `http://127.0.0.1:5000`.

3. Use the web interface:
   - **Individual Prediction**: Enter the date, area, and item code to get the predicted sales.
   - **Bulk Prediction**: Upload a CSV file with columns ddate, area, and itemcode
     to get predictions for multiple items.

## Input Format

### Individual Prediction

- **Date**: In `DD-MM-YYYY` format.
- **Area**: Name of the area (e.g., `KOLKATA`).
- **Item Code**: Code of the item (e.g., `PB0002`).

### Bulk Prediction

Upload a CSV file with the following columns:

- ddate: Date in `DD-MM-YYYY` format.
- area: Name of the area.
- itemcode: Code of the item.

Example:

```csv
ddate,area,itemcode
30-11-2013,HOOGHLY,PB0002
17-11-2009,ASSAM,N00001
```

## Model Training

The model was trained using the data preprocessing and training pipeline defined in PipelineItemDatewise.ipynb

. Key steps include:

- Data cleaning and preprocessing.
- Encoding categorical features (area and item code).
- Adding cyclical features for the month.
- Training a neural network using Keras.

## Dependencies

- Python 3.7+
- Flask
- TensorFlow 2.19.0
- Keras 3.9.2
- Pandas
- NumPy
- Scikit-learn
- XGBoost 2.1.1

## License

This project is licensed under the MIT License. See the LICENSE file for details.

## Acknowledgments

- The dataset used for training the model is assumed to be historical sales data.
- The cyclical feature engineering approach was inspired by best practices in time-series modeling.

## Contributing

Contributions are welcome! Feel free to fork the repository and submit a pull request.

---

**Author**: Joydeep Ganguly
**Contact**: joydeepganguly32@gmail.com

```
This README provides a comprehensive overview of the project, including its purpose, features, installation steps, usage instructions, and model training details.
```

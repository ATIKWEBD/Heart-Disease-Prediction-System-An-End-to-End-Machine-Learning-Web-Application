

### **Heart Disease Prediction System: An End-to-End MLOps-Driven Flask Application for Cardiovascular Risk Prediction**

This project is a comprehensive machine learning solution for predicting a patient's 10-year risk of coronary heart disease. It demonstrates a complete MLOps pipeline, from data analysis and model training to deployment within a production-ready Flask web application.

-----

### **Technical Overview**

The core of this system is a **Random Forest Classifier** trained on the **Framingham Heart Study dataset**. The project workflow is structured into two main phases:

  * **1. Machine Learning Pipeline (`HEART DISEASE PREDICTION.ipynb`)**:

      * **Data Preprocessing**: Handled missing values through imputation (mode for categorical, median for numerical features) and removed the `education` column to streamline the feature set.
      * **Class Imbalance**: Addressed the significant class imbalance in the target variable (`TenYearCHD`) using **upsampling** on the minority class to ensure the model's predictive performance is not biased.
      * **Model Selection**: Trained and evaluated a suite of classifiers, with the Random Forest Classifier demonstrating superior performance metrics, including an accuracy of over 97% on the balanced dataset.
      * **Model Persistence**: The final trained model (`rf_classifier.pkl`) and a fitted `StandardScaler` object (`scaler.pkl`) were serialized using `pickle` for seamless deployment.

  * **2. Web Application Deployment (`app.py`, `index.html`)**:

      * **Flask Framework**: A Python-based Flask application serves as the production environment for the model.
      * **Real-Time Inference**: The application loads the serialized model and scaler at startup, enabling low-latency, real-time predictions.
      * **Feature Engineering**: The backend handles on-the-fly feature encoding and scaling of user input to match the format expected by the model.
      * **User Interface**: A responsive and user-friendly web interface, styled with Bootstrap, allows for intuitive data entry and clear display of prediction results.

-----

### **MLOps in Practice**

This project applies core MLOps principles by:

  * **Separating Concerns**: The model development (Jupyter Notebook) is separated from the serving environment (Flask app).
  * **Version Control**: The trained model and scaler are treated as artifacts, packaged separately from the application code.
  * **Reproducibility**: The use of a serialized scaler ensures that user input is preprocessed identically to the training data, guaranteeing consistent and reliable predictions.

-----

### **Getting Started**

1.  **Clone the Repository**:

    ```bash
    git clone [your-repository-url]
    cd [your-repository-name]
    ```

2.  **Set up the Environment**: Ensure Python is installed. It's recommended to use a virtual environment.

    ```bash
    python -m venv venv
    # On Windows:
    venv\Scripts\activate
    # On macOS/Linux:
    source venv/bin/activate
    ```

3.  **Install Dependencies**: Install all required libraries using `pip`.

    ```bash
    pip install -r requirements.txt
    ```

    (Note: You can generate this file from your notebook environment by running `pip freeze > requirements.txt`).

4.  **Run the Application**:

    ```bash
    python app.py
    ```

5.  **Access the App**: Navigate to `http://127.0.0.1:5000` in your web browser.

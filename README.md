\# 🦷 Brush-Sense: Sensor-Based Toothbrush Movement Classifier



\### 📘 Overview



\*\*Brush-Sense\*\* is an advanced Machine Learning project designed to automatically classify four critical toothbrushing movements (Rest, Left-Right, Up-Down, Circular) based on raw time-series sensor data. The project emphasizes robust \*\*Signal Processing\*\*, \*\*Feature Engineering\*\*, and \*\*Feature Selection\*\* techniques to transform noisy sensor readings into a highly predictive model for analyzing human behavior.



\### 🧩 Project Structure



The project is structured into two main executable files for clear separation of concerns (training vs. prediction) and utilizes a dedicated data storage structure:

├── main05\_train\_and\_prepare.py # Script for training the final model, | # feature selection, and saving artifacts. ├── main05\_predict\_blind\_data.py # Script for loading the trained model and | # predicting on new, unseen data. ├── 05\_README.txt # Technical README (for reference/legacy). └── data/ ├── pool\_dataset.zip # Raw training sensor data. ├── blind\_data.zip # Raw test sensor data. └── intermediate\_outputs/ # Directory containing saved model, feature metadata, and normalization parameters.

---



\### ⚙️ Methodology \& Pipeline



The solution implements a complete end-to-end classification pipeline:



1\.  \*\*Data Preprocessing \& Windowing:\*\*

&nbsp;   \* Time-series sensor data is cleaned and segmented into fixed-size \*\*analysis windows\*\* to capture localized motion patterns.

&nbsp;   \* Normalization parameters are globally calculated and saved to ensure consistency between training and prediction environments.



2\.  \*\*Advanced Signal Processing \& Feature Engineering:\*\*

&nbsp;   \* Features are extracted from both the \*\*Time Domain\*\* (e.g., standard statistics, signal energy) and the \*\*Frequency Domain\*\* (e.g., power spectral density using \*\*Welch's method\*\*, spectral entropy).

&nbsp;   \* Advanced features are derived from \*\*Hilbert Transforms\*\* and custom functions to capture complex signal characteristics related to motion.



3\.  \*\*Rigorous Feature Selection:\*\*

&nbsp;   \* A two-stage feature selection pipeline is employed to select the most predictive, non-redundant subset of features:

&nbsp;       \* \*\*ReliefF:\*\* Used for initial ranking and assessment of feature relevance.

&nbsp;       \* \*\*MRMR (Minimum Redundancy Maximum Relevance):\*\* Used to minimize redundancy between features while maximizing their correlation with the target class (movement type).



4\.  \*\*Model Development:\*\*

&nbsp;   \* A robust \*\*Support Vector Classifier (SVC)\*\* and \*\*Random Forest Classifier\*\* were tuned and trained on the final feature set.

&nbsp;   \* The model achieves high accuracy in classifying the four distinct brushing movements.



---



\### 📊 Results Summary



The final retrained model demonstrated strong performance on the validation data prior to final deployment:



| Metric | Result (Example Placeholder) |

| :--- | :--- |

| \*\*Model\*\* | SVC (Tuned) |

| \*\*Classification Accuracy\*\* | \*\*~92.5%\*\* |

| \*\*Target Classes\*\* | 4 (Rest, L-R, U-D, Circular) |



\*Note: Actual classification metrics (Accuracy, Precision, Recall) are achieved by loading the final model (`final\_model\_for\_lecturer\_data.joblib`) and running it on the test dataset (`main05\_predict\_blind\_data.py`).\*



\### 🚀 Future Improvements



\* \*\*Real-time Integration:\*\* Deploying the trained model to a mobile device for real-time inference during brushing.

\* \*\*Deep Learning:\*\* Exploring \*\*Recurrent Neural Networks (RNN)\*\* or \*\*LSTMs\*\* for potentially better temporal feature extraction.

\* \*\*User Personalization:\*\* Developing personalized models or fine-tuning techniques to account for individual brushing styles.



\### 💻 Running the Project



To run the prediction script on new data:



1\.  \*\*Requirements:\*\* Ensure Python dependencies (Pandas, NumPy, Scikit-learn, joblib, etc. - as seen in the imports) are installed.

2\.  \*\*Execution:\*\* Run the prediction script, which automatically loads the final trained model and runs the full pipeline on the new data:

&nbsp;   ```bash

&nbsp;   python main05\_predict\_blind\_data.py

&nbsp;   ```

&nbsp;   \*The output (`05\_predictions.csv`) will be saved in the `data/` folder.\*



\### 🧑‍💻 Author



\*\*Ofir Hagag\*\* | Biomedical \& Data Science Researcher



---


<!-- ========================================================= -->
<!-- 1. COPY MULAI DARI SINI UNTUK REPOSITORI: CampusCALM      -->
<!-- ========================================================= -->

# 🧠 CampusCALM
**Student Stress Level Prediction Using Ensemble Machine Learning**

[![Streamlit App](https://static.streamlit.io/badges/streamlit_badge_black_white.svg)](https://campuscalm.streamlit.app/)
[![Python](https://img.shields.io/badge/Python-3.8+-blue.svg)](https://www.python.org/)
[![Scikit-Learn](https://img.shields.io/badge/scikit--learn-F7931E?logo=scikit-learn&logoColor=white)](https://scikit-learn.org/)

> **Short Summary:** An AI/ML-based application that identifies stress patterns and predicts student stress levels from psychological, physiological, social, environmental, and academic indicators, using an ensemble of classification models trained on a 2,000-respondent survey dataset.

---

### 📌 Project Properties
- **Author:** David Christian Golden Mahaviro
- **Context:** Group Class Assignment – Final Project Machine Learning
- **Role:** Data Analyst & Machine Learning Engineer
- **Tech Stack:** Python, Pandas, Scikit-learn, Imbalanced-learn (SMOTE), Matplotlib, Seaborn, Streamlit
- **Live Deployment:** [View Web App](https://campuscalm.streamlit.app/)

---

### 📖 Project Context
University students frequently face academic pressure, heavy workloads, sleep deprivation, and anxiety, which can severely elevate stress levels and negatively impact mental health, focus, and academic performance. **CampusCALM** was built to address this real-world academic problem by turning self-reported survey data into a reliable predictor for student stress levels (Distress / Eustress / Other-Mixed).

As the **Data Analyst & ML Engineer** for this group project, I was responsible for the entire modeling pipeline:
1. Performing Exploratory Data Analysis (EDA) and data cleaning on the 2,000-respondent dataset.
2. Building, training, and evaluating four base classification models.
3. Designing and training the final ensemble model using majority voting.

---

### 📊 Dataset
All datasets used in this project are stored in the `data` folder as `.csv` files.
- **Title:** Stress Indicator Dataset for Mental Health Classification
- **Source:** [Mendeley Data](https://doi.org/10.17632/2gsjv8m7ch.1)
- **Description:** A dataset containing 2,000 student respondents with 25 features representing stress factors across five main categories: psychological, physiological, social, environmental, and academic.

---

### ⚙️ Methodology & Problem Solving
Student stress data collected through surveys is naturally noisy. It can contain outliers, imbalanced class distributions, and correlated features. My approach to solving this:

- **EDA & Data Handling:** Explored class distributions, feature histograms, and demographic spread. Filtered out age outliers outside the intended 18–22 range and handled data noise using boxplot inspections across 1–5 scale features.
- **Preprocessing:** Built a correlation matrix to check for highly correlated features (threshold > 0.7). Applied `StandardScaler` to normalize feature scales and utilized **SMOTE** exclusively on the training set to address class imbalance without data leakage.
- **Modeling Strategy:** Benchmarked multiple classifiers and combined the best performing ones into an **Ensemble Majority Voting** classifier to improve predictive robustness over any single base model.

---

### 🤖 Models
The trained machine learning models are stored in the `model` folder as `.ipynb` notebooks and exported `.pkl` files.

| Model | Description |
| :--- | :--- |
| **Logistic Regression** | Baseline Model |
| **Random Forest** | Estimators & Feature Importance Analysis |
| **Support Vector Machine** | Linear Kernel |
| **K-Nearest Neighbors** | Default Hyperparameters |
| **Ensemble (Majority Voting)** | **Final Production Model (Combined RF + SVM + KNN)** |

---

### 🚀 How to Run Locally

**1. Install Dependencies**  
Ensure Python 3.8+ is installed, then run the following command in your terminal:
```bash
pip install -r requirements.txt
```

**2. Training Model (Optional)**  
To retrain all classification models, run the Jupyter Notebooks inside Visual Studio Code or Google Colab to generate the updated `.pkl` files.

**3. Deployment (Streamlit)**  
Run the dashboard application locally using Streamlit:
```bash
python -m streamlit run app.py
```
*The application will be accessible at: `http://localhost:8501`*



<!-- ========================================================= -->
<!-- 2. COPY MULAI DARI SINI UNTUK REPOSITORI: Hangul Air-Writing -->
<!-- ========================================================= -->

# ✋ Hangul Air-Writing Recognition
**Air Canvas: Hand-Gesture Tracking & Interactive UI for Air-Writing**

[![Python](https://img.shields.io/badge/Python-3.8+-blue.svg)](https://www.python.org/)
[![OpenCV](https://img.shields.io/badge/OpenCV-5C3EE8?logo=opencv&logoColor=white)](https://opencv.org/)
[![MediaPipe](https://img.shields.io/badge/MediaPipe-00A67E?logo=Google&logoColor=white)](https://developers.google.com/mediapipe)

> **Short Summary:** A computer vision system that lets users write Korean (Hangul) characters in the air using hand gestures, tracked via a webcam. The drawn strokes are classified using a traditional ML pipeline (HOG + SVM). My core contribution was building the real-time hand-tracking canvas and its interactive gesture-based UI.

---

### 📌 Project Properties
- **Author:** David Christian Golden Mahaviro
- **Context:** Group Class Assignment – Computer Vision (2026)
- **Role:** Computer Vision Engineer – Air Canvas (Tracking & UI)
- **Status:** 🚧 Active / In Progress (Currently undergoing UI improvements)
- **Tech Stack:** Python, OpenCV, MediaPipe, NumPy, Scikit-image (HOG), Joblib / SVM
- **Links:** [Watch Video Demo](#) <!-- Replace '#' with your actual YouTube link -->

---

### 📖 Project Context
This project explores Hangul character recognition from air-writing gestures using traditional computer vision. It is a webcam-based system where users "draw" Korean characters by moving their index finger in the air without touching any physical surface. These strokes are then classified using a handcrafted-feature ML pipeline (HOG features + SVM/KNN/LightGBM).

As the **Computer Vision Engineer (Air Canvas)** for Group 10, my scope of work focused entirely on the real-time interactive layer:
1. Building the real-time hand-tracking and finger-drawing engine.
2. Designing a gesture-based control scheme (draw, classify, erase, merge words) requiring zero keyboard/mouse input mid-session.
3. Building the on-screen UI, including a color palette, toolbar, progress indicators, and result overlay.

---

### ⚙️ Methodology & Problem Solving

Recognizing a hand-drawn character is only half the problem. The other half is providing a natural, touchless interface that prevents accidental triggers and jittery lines. 

- **Gesture & Canvas Engine:** Utilized **MediaPipe Hands** to classify hand poses into discrete gestures based on extended fingers (e.g., index-only to draw, peace sign to classify, fist to merge). Implemented EMA (exponential moving average) smoothing for jitter reduction and speed-sensitive line thickness for natural strokes.
- **Anti-False-Trigger Logic:** Designed frame-based confirmation counters and cooldowns for critical gestures (classify/merge). A gesture must hold steady for a set number of frames to prevent accidental double-triggers caused by natural hand jitter.
- **Multi-Word Buffer & UI:** Created a buffer workflow allowing users to write multiple characters in sequence before merging them into a sentence. Built an on-screen toolbar with dwell-to-select interaction, live gesture cursors, and confidence score overlays.

---

### 🚀 Impact & Lessons Learned

- **Fully Hands-Free Interaction:** Turned a static classification model into a highly usable tool where users can draw, classify, undo, and combine words using hand gestures alone.
- **Robust Real-Time CV:** Learned that a real-time gesture interface requires a deliberate robustness layer (confirmation frames, cooldowns) to feel reliable to an actual user, proving that state management is just as crucial as the computer vision algorithm itself.

---

### 💻 Setup & Installation

To run the Air Canvas locally, follow these steps:

**1. Clone the repository**
```bash
git clone [https://github.com/davidhoky/YOUR-REPO-NAME.git](https://github.com/davidhoky/YOUR-REPO-NAME.git)
cd YOUR-REPO-NAME
```

**2. Create and activate a virtual environment**
```bash
# Create environment
python -m venv air_canvas_env

# Activate (Windows)
air_canvas_env\Scripts\activate

# Activate (Mac/Linux)
source air_canvas_env/bin/activate
```

**3. Download the Dataset**
You can download the dataset manually via Kaggle Hub:
```python
import kagglehub
kagglehub.dataset_download("jkim289/handwritten-korean-characters")
```
*Alternatively, run **Step 2** in the provided Jupyter Notebook to download it automatically.*

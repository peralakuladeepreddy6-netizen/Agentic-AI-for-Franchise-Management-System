# Milestone 2: FranchiseOps AI - Advanced Analytics & ML Integration

## 1. Overview
Milestone 2 extends the basic FranchiseOps AI framework built in Milestone 1 by integrating **Machine Learning (ML)** and **Advanced Business Intelligence**. 
While Milestone 1 focused on the foundational UI, authentication, and basic AI copilot functionality, Milestone 2 introduces:
- **Workforce Forecasting (Agent 1)**: ML-based predictions for workforce requirements across different outlet tiers.
- **Outlet Analytics (Agent 2)**: Categorization and visualization of outlet performance.
- **Inventory Optimization (Agent 3)**: Predictive insights into inventory management using clustering algorithms (KMeans).
- **Dynamic Admin Dashboard**: A fully interactive ML Model Card system showcasing real-time model metrics, user management (Add/Delete/Unlock), and robust multi-factor authentication (OTP) with cooldown/lockout mechanics.
- **LLM Integration**: Improved prompting and response handling for the AI Copilot.
- **Localized Weather Demo**: Real-world API fetching to showcase city-specific environmental insights.

## 2. Tech Stack Used
- **Language**: Python 3.12+
- **Interface**: Streamlit
- **ML & Data Science**: Scikit-learn (StandardScaler, KMeans, Pipelines), Pandas, NumPy
- **Database**: SQLite (via `sqlite3` for modular user/auth management)
- **LLM/API Integration**: Requests (for external APIs), Google Colab Secrets management
- **Containerization**: Native Python modules structured for modular execution.
- **Version Control**: Git / GitHub (hosted within the existing Infosys Repository).

## 3. Repository & Folder Structure
```
Infosys_Repository/
├── Milestone1/ (Previous milestone files)
└── Milestone2/ (Current milestone - everything resides here)
├── README.md (This file)
├── working_model_Milestone2.ipynb (Main Jupyter Notebook)
├── auth.py (Authentication, OTP, lockout logic)
├── db.py (Database operations)
├── ui_theme.py (Centralized UI styling and theme configuration)
├── admin_dash.py (Admin panel management, user actions)
├── train_m2_franchise.py (Machine Learning training pipelines for Agent 1, 2, 3)
├── llm_engine_franchise.py (Copilot/LLM interaction handler)
├── requirements.txt (Python dependencies)
└── screenshots/
```

## 4. System Architecture Overview
The system follows a modular, layered architecture designed for scalability:

| Layer | Components | Responsibility |
| :--- | :--- | :--- |
| **Presentation** | `Streamlit` UI, `ui_theme.py` | User Interface, Dashboards, and Data Visualization. |
| **Application** | `auth.py`, `admin_dash.py`, `llm_engine_franchise.py` | Business logic, session management, user actions, and API handling. |
| **Data** | `db.py`, SQLite, Input `.csv` datasets | Persistent storage for users, OTPs, and raw franchise data. |
| **ML & Analytics** | `train_m2_franchise.py`, `scikit-learn` | Model Training (Agents 1-3), Feature Engineering, and Inference Pipelines. |

*Note: The system fetches dynamic data via API (Weather) and supports local model training pipelines.*

## 5. Localized Indian Retail City Table
The system utilizes a localized dataset spanning 6 major Indian metropolitan retail hubs for analysis and forecasting:

| City | State/Region |
| :--- | :--- |
| **Mumbai** | Maharashtra |
| **Delhi NCR** | National Capital Region |
| **Bengaluru** | Karnataka |
| **Hyderabad** | Telangana |
| **Chennai** | Tamil Nadu |
| **Pune** | Maharashtra |

## 6. Environment & Setup (Colab Secrets + Kaggle API)
The modular scripts and notebook require access to environment secrets and external datasets. Follow these steps to configure your environment:

### Step 1: Configure Google Colab Secrets
1. Open your `working_model_Milestone2.ipynb` in Google Colab.
2. Go to the **🔑 Secrets** tab on the left sidebar.
3. Add the following keys and their corresponding values:
   - `KAGGLE_USERNAME`: Your Kaggle username.
   - `KAGGLE_KEY`: Your Kaggle API Key.
4. Ensure the toggle is turned **ON** to enable the secrets for the runtime.

### Step 2: Kaggle API Setup
1. Download your `kaggle.json` API token from your Kaggle account profile page (Settings -> API -> Create New Token).
2. Upload this `kaggle.json` file to your Colab environment or the root of your project.
3. In the notebook, run the following setup code:
```python
import os
import json
# Optional: Set environment variables in the Colab environment
os.environ['KAGGLE_USERNAME'] = 'your_kaggle_username' 
os.environ['KAGGLE_KEY'] = 'your_kaggle_api_key'
```

### Step 3: Install Dependencies
Run the following terminal command or notebook cell to install required packages:
```
pip install -r requirements.txt
```

## 7. How to Run the Application
Once dependencies are installed and secrets are configured, you can run the application.
To run the main Streamlit Application:
```
streamlit run working_model_Milestone2.ipynb
```

To train/finetune the ML Models:
```
python train_m2_franchise.py
```
## 8. Known Issues & Patch Notes
> *If you encounter the `ValueError: X has 6 features, but StandardScaler is expecting 4 features` error when accessing Agent 1, this is due to a feature mismatch in the ML pipeline. This is a known edge case when the input dataframe contains extra columns that the training model did not learn from. A patch is applied in `train_m2_franchise.py` to strictly filter columns down to the `model.feature_names_in_` set prior to prediction.*

## 9. Screenshots to Capture
1. **Home page**
   - *Filename:* ![Home Page](screenshots/home_page.png)
   - *Description:* The landing dashboard showing the navigation sidebar and welcome screen.

2. **AI Copilot (prompt + response)**
   - *Filename:* ![AI Copilot](screenshots/ai_copilot_response.png)
   - *Description:* An interaction where the user asks a business question and the AI provides a valid response.

3. **Weather Demo (city + result)**
   - *Filename:* ![Weather Demo](screenshots/weather_demo.png)
   - *Description:* A valid city selection showing the current weather data.

4. **Outlet Tiers page (showing the 3-tier chart)**
   - *Filename:* ![Outlet Tiers](screenshots/outlet_tiers_chart.png)
   - *Description:* The data visualization chart clearly displaying the 4 outlet tiers (Tier 1–4).

5. **Admin Panel → ML Model Card tab (showing all 3 agents' metrics + KMeans)**
   - *Filename:* ![ML Model Card](screenshots/admin_ml_model_card.png)
   - *Description:* The admin panel showing evaluation metrics for Workforce, Outlet, Inventory agents, alongside the KMeans clustering insights.

6. **Triggered lockout message**
   - *Filename:* ![Lockout Message](screenshots/triggered_lockout.png)
   - *Description:* The system's response to multiple failed login attempts, showing the account lockout screen.

7. **OTP cooldown message**
   - *Filename:* ![OTP Cooldown](screenshots/otp_cooldown.png)
   - *Description:* The message displayed when a user requests an OTP too frequently, showing a countdown timer or cooldown warning.


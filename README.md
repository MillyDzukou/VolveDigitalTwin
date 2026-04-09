# VolveDigitalTwin
A Full-Stack Industrial IoT platform designed to visualize and predict production rates for the Equinor Volve Field. This project integrates a Machine Learning pipeline with a React/Django architecture to provide "Virtual Flow Metering" (VFM) for decommissioned North Sea assets.

🚀 The Core Challenge
Physical flow meters in the oilfield are expensive to maintain and frequently fail. This project demonstrates how ML Engineering can "fill the gaps" by using secondary sensor data (Pressure and Temperature) to calculate production rates when physical meters are offline.

🛠️ Technical Stack
Frontend: React.js, Tailwind CSS, Recharts (Data Visualization)

Backend: Django REST Framework (DRF)

Database: PostgreSQL (Time-series production data)

ML Engine: Python (Scikit-Learn, XGBoost, Pandas)

Data Source: Equinor Volve Field Open Data (2008–2016)

📊 Key Features
1. Virtual Flow Metering (ML)
Algorithm: XGBoost Regressor trained on 8 years of historical well data.

Features Used: Wellhead Pressure (P 
whp
​
 ), Wellhead Temperature (T 
wht
​
 ), and Choke Size.

Output: Predicted Oil/Gas/Water flow rates with < 8% MAPE (Mean Absolute Percentage Error).

2. Interactive Production Dashboard
Well Selection: Filter data by specific Volve wells (e.g., 15/9-F-14).

Live Comparison: Side-by-side visualization of Actual vs. Predicted production.

Decline Curve Analysis: Automatically calculates the estimated ultimate recovery (EUR) based on historical trends.

3. Engineering ETL Pipeline
Automated cleaning of SCADA logs to handle sensor drift and "shut-in" periods.

Data normalization and feature engineering for time-series forecasting.

🏗️ Architecture
The system follows a Model-View-Controller (MVC) pattern:

Ingestion: Python scripts parse Volve CSV/LAS files.

Storage: Processed data is migrated to a relational PostgreSQL schema.

API: Django serves optimized JSON endpoints for high-frequency time-series data.

UI: React frontend fetches and renders data using optimized hooks to prevent lag during large data visualization.

📂 Project Structure
Plaintext
├── backend/            # Django Project
│   ├── api/            # REST Endpoints
│   ├── ml_models/      # Pre-trained Pickles & Training Scripts
│   └── data_pipeline/  # ETL Scripts for Volve Dataset
├── frontend/           # React App
│   ├── src/components/ # Dashboard, Charts, Sidebar
│   └── src/hooks/      # Data fetching logic
└── docs/               # Technical documentation & screenshots
🔧 Installation & Setup
Clone the Repo:

Bash
git clone https://github.com/yourusername/VolveDigitalTwin.git
Setup Backend:

Bash
cd backend
pip install -r requirements.txt
python manage.py migrate
python manage.py runserver
Setup Frontend:

Bash
cd frontend
npm install
npm run dev
📈 Future Roadmap
Real-time Stream: Integration with Apache Kafka for live sensor simulation.

Anomaly Detection: Automated alerts for ESP (Electric Submersible Pump) failure signatures.

Dockerization: Containerizing the entire stack for cloud deployment.

Contact: Milly Dzukou – LinkedIn – Email
Data Source: Special thanks to Equinor for providing the Volve Field dataset for research and development.

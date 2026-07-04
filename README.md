Coconut Leaf Disease Detection System
Backend (FastAPI)
1) Install dependencies
Create and activate a virtual environment (recommended), then install packages.

python3 -m venv env
source env/bin/activate
python3 -m pip install -r requirements.txt
2) Run the API
source env/bin/activate
python3 -m uvicorn inference.inference.infer:app --host 127.0.0.1 --port 8000 --reload
Health check:

GET http://127.0.0.1:8000/health
Prediction:

POST http://127.0.0.1:8000/predict
Form-data field name: file
Response format:

{ "disease": "Healthy_Leaves", "confidence": 0.9936 }
Frontend (React + Vite)
1) Install dependencies
cd frontend
npm install
2) Start the dev server
cd frontend
npm run dev
Open:

http://localhost:5173
The Vite dev server proxies /predict and /health to http://127.0.0.1:8000.

Run Full App (Two Terminals)
Terminal 1:

source env/bin/activate
python3 -m uvicorn inference.inference.infer:app --host 127.0.0.1 --port 8000 --reload
Terminal 2:

cd frontend
npm run dev
Notes
Ensure mobilenet_best.pth exists at the repository root.
The model runs on Apple Silicon using mps when available.

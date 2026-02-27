💰 Personal Expense Tracker (Full-Stack)A modern, glassmorphic financial dashboard built to demonstrate a clean decoupled architecture. This application allows users to manage their cash flow with a React-based UI that communicates via a RESTful API to a Python/Flask backend.🎯 Core FeaturesReal-time Analytics: Automated calculation of Total Balance, Income, and Expenses.Persistence: SQLite database integration ensures data is saved across sessions.Glassmorphic UI: A premium, modern interface using CSS backdrop-filter and SVG iconography.RESTful API: Clean separation of concerns between the data layer and the presentation layer.💻 Tech StackLayerTechnologyKey LibraryFrontendReact 18 (Vite)CSS Modules, Fetch APIBackendPython 3.9+Flask, Flask-CORSDatabaseSQLiteFlask-SQLAlchemy (ORM)🛠️ Rapid Setup1. Backend (API)The backend manages the database and serves the transaction data.Bashcd backend
python -m venv venv
source venv/bin/activate  # Windows: venv\Scripts\activate
pip install Flask Flask-CORS Flask-SQLAlchemy
python app.py
Note: The server runs on http://localhost:5000. It will automatically generate expenses.db on launch.2. Frontend (UI)The frontend handles the state and visualizes the financial data.Bashcd frontend
npm install
npm run dev
Note: The UI runs on http://localhost:5173.🔌 API DesignThe frontend interacts with the following endpoints:GET /api/transactions: Retrieves all logged items.POST /api/transactions: Adds a new record.Payload: { "title": "Coffee", "amount": 5.50, "type": "expense" }DELETE /api/transactions/<id>: Removes a record by ID.📂 Project StructurePlaintext├── backend/
│   ├── app.py           # Database models & API routes
│   └── expenses.db      # Local SQLite database
├── frontend/
│   ├── src/
│   │   ├── components/  # Dashboard, Form, & List UI
│   │   ├── App.jsx      # Global state & API Logic
│   │   └── index.css    # Glassmorphic styling & Variables
│   └── vite.config.js
└── README.md
📈 Technical Implementation DetailsState SynchronizationThe application uses a "Fetch-Then-Update" pattern. When a user adds an expense, the app sends a POST request to the Flask server. Upon a successful 201 Created response, the React state is updated to include the new transaction, triggering a re-render of the "Total Balance" component without a page refresh.The Math LogicThe UI calculates the balance using the following logic:$$Total = \sum (\text{incomes}) - \sum (\text{expenses})$$

💻 Cyber Café / Gaming Parlor PC Allocator

A desktop application for managing PC allocation, session tracking, and automatic billing in a cyber café or gaming parlor. Built with Python, Tkinter, and SQLite.

📌 Overview

Running a cyber café involves constantly tracking which PCs are free, who is using them, and how much to charge. This project replaces pen-and-paper tracking with a simple GUI that:

Shows a live status grid of all PCs (free / in use)
Allocates a PC to a customer and starts a timed session
Ends the session and generates a bill based on usage time and the PC's hourly rate
Stores all customers and session history in a local SQLite database
✨ Features
🟢🔴 Live PC Status Grid – color-coded cards (green = free, red = in use, with the current user's name)
▶ Start Session – enter customer name and phone number, pick a free PC, and go
⏹ End Session & Generate Bill – calculates the total based on elapsed time × hourly rate and shows a receipt
👥 Customer Records – returning customers are recognized by phone number (no duplicates)
🗄️ Auto-initialized Database – tables are created and sample PCs are seeded on first run
🛡️ Input Validation & Error Handling – friendly pop-ups for missing input or database errors
⏱️ Minimum billing – sessions are billed for at least 1 minute
🛠️ Tech Stack
Component	Technology
Language	Python 3.x
GUI	Tkinter / ttk
Database	SQLite3

No external packages are required. Everything used is part of the Python standard library.

🗃️ Database Schema

The database file cyber_cafe.db is created automatically with three tables:

PCs

Column	Type	Description
pc_id	INTEGER (PK)	Unique PC ID
pc_name	TEXT	PC name / label
rate_per_hour	REAL	Hourly charge (₹)
status	TEXT	Available or Occupied

Customers

Column	Type	Description
customer_id	INTEGER (PK)	Unique customer ID
full_name	TEXT	Customer name
phone_number	TEXT (UNIQUE)	Customer phone

Sessions

Column	Type	Description
session_id	INTEGER (PK)	Unique session ID
pc_id	INTEGER (FK → PCs)	PC used
customer_id	INTEGER (FK → Customers)	Customer
start_time	TIMESTAMP	Session start
end_time	TIMESTAMP	Session end
total_bill	REAL	Final amount (₹)
payment_status	TEXT	Active or Completed
Default PCs (auto-seeded)
PC	Type	Rate
PC-01, PC-02	VIP	₹80/hr
PC-03, PC-04	Gaming	₹50/hr
PC-05, PC-06	Budget	₹30/hr
🚀 Getting Started
Prerequisites
Python 3.8 or higher
Tkinter (included with most Python installations)
On Ubuntu/Debian, if missing: sudo apt install python3-tk
Installation & Run
bash
# 1. Clone the repository
git clone https://github.com/<your-username>/<your-repo-name>.git
cd <your-repo-name>

# 2. Run the application
python main.py

Replace main.py with the name of your Python file. If your code is in the Jupyter notebook, copy the code into a .py file or run it from the notebook.

The database is created automatically on first launch.

📖 How to Use
Start a session
Enter the customer's name and phone number
Select a free PC from the dropdown
Click ▶ Allocate PC & Start Session
Monitor – the left grid updates instantly to show which PCs are free or in use
End a session
Select the session in the Active Sessions table
Click ⏹ End Session & Generate Bill
A receipt shows the duration, rate, and total bill
Billing Formula
Total Bill = max(duration in hours, 1 minute) × rate per hour
📂 Project Structure
├── main.py          # Application source code
├── cyber_cafe.db    # SQLite database (auto-generated on first run)
└── README.md
🔮 Future Improvements
Daily / monthly revenue reports
Admin panel to add, edit, or remove PCs and change rates
Session history and customer search
Live running timer and bill preview during a session
Printable / exportable receipts (PDF)
Login system for staff
🤝 Contributing

Contributions, issues, and feature requests are welcome! Feel free to fork the repo and open a pull request.

📄 License

This project is licensed under the MIT License.

👤 Author

Drashti Patel GitHub: @drashti6619

# Investment-Operations-Project
A practical data engineering and analytics project built to simulate a core buy-side asset management / hedge fund operations workflow. This repository contains an end-to-end data pipeline that automates transaction data validation, reconciles internal books against broker statements, flags operational risk exceptions, and feeds a multi-page management reporting layer.

📌 Project Overview
In institutional fund management, keeping portfolio data accurate is critical. Every day, a fund receives raw operational files that must be cleaned, validated, and cross-referenced with external broker data to catch trade discrepancies before they impact valuation.

This platform automates that entire process using a three-tier architecture:

Python Layer: Handles automated backend ingestion, trade data validation, string cleaning, discrepancy calculations, and automated exception reporting.

Excel Layer: Serves as the localized operational workspace for analysts to review the programmatically generated audit exceptions.

Power BI Layer: Delivers interactive dashboard reporting to track high-level portfolio KPIs, asset allocations, open risk breaks, and exception aging.

🏗️ Repository Architecture & Data Flow
1. File & Directory Structure
Plaintext
├── data/        # Raw internal files (Trades, Positions, Prices, Cash) and Broker statements
├── output/      # Programmatically generated operational exception reports
├── notebooks/   # Jupyter notebook containing Python data scripts
└── dashboards/  # Interactive Power BI dashboard file
2. Core Python Script Modules
The main notebook breaks down the pipeline into discrete, functional processing modules:

Trade Validation: Cleans inbound string inputs, strips whitespace, and scans raw transactional data for basic errors like missing unique IDs, negative volumes, or duplicate entries.

Reconciliation & Exception Tracking: Merges internal ledger states with the external broker data using pandas. It automatically evaluates records and generates custom flags for break categories like quantity mismatches, price mismatches, and missing entries.

Portfolio Analytics: Performs baseline calculations on the cleaned datasets, tracking calculated values like Daily P&L, asset allocation percentages, and individual security weight contributions.

📊 Dashboard Reporting Design (Power BI)
The processed data is pushed to a production-ready Power BI template designed for quick executive review. The reporting interface is split into targeted environments:

Executive Operations Overview: Tracks high-level financial health metrics including Total AUM, Daily P&L, core cash positions, and overarching trade volume flows.

Reconciliation & Operational Audit: A functional tracking space focusing on data integrity. It features dedicated KPI blocks isolating the total count of quantity and price breaks, a breakdown chart categorizing exceptions, and a data grid utilizing soft conditional formatting highlights to directly draw an analyst's eyes to mismatched rows.

🛠️ Tech Stack & Tools Used
Python 3.x: Backend logic, exception rule tracking, and directory exports.

Pandas & NumPy: Data wrangling, joining disjointed datasets, and missing value calculations.

Microsoft Excel: Storage format for incoming operational sheets and analyst review sheets.

Microsoft Power BI Desktop: Visual hierarchy design, data modeling, and custom field mapping.

🚀 How to Run the Pipeline
Clone the repository to your local system.

Place your raw data sheets inside the data folder.

Open and run the cells sequentially inside your Jupyter notebook.

Check the output folder for the newly generated Excel exception reports.

Open your file in Power BI Desktop and hit Refresh to reload the visuals with the latest data inputs.

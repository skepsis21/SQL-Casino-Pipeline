Casino-DB-Pipeline

An automated SQLite backend data pipeline for player loyalty segmentation, live high-roller alerts, and scheduled database optimization on a cruise line gaming floor.
📌 Business Scenario

Managing data operations on a modern cruise ship casino requires efficient, automated background processing to conserve satellite bandwidth and keep live dashboards running quickly. This project establishes an automated relational database pipeline that manages high-roller tracking, processes tiered player loyalty logic on demand, and schedules database self-maintenance routines.

This project is built for reproducibility—all data ingestion, schema creation, and reporting are automated through Python-based pipelines, eliminating manual setup.
🚀 Getting Started

    Clone the repository.

    Setup Environment: Create a virtual environment and install dependencies:
    Bash

    python -m venv .venv
    .venv\Scripts\activate  # On Windows
    pip install -r requirements.txt

    Initialize Database: Run the automation script to ingest CSV data into SQLite:
    Bash

    python setup_local_db.py

    Generate Analytics: Run the reporting scripts to generate dashboard files and visual charts:
    Bash

    python Scripts/generate_charts.py
    python Scripts/generate_manager_report.py

🗺️ System Architecture
🛠️ Project Contents

    Data/: Contains raw CSV source files for ingestion.

    docs/: Technical assets, architecture diagrams, and documentation.

    Scripts/: Automation scripts and core SQL analysis queries.

    setup_local_db.py: Master script to build the local SQLite environment.

🛠️ Solutions Implemented
1. On-Demand Player Profiling

    Objective: Allows VIP casino hosts to instantly pull a breakdown of customer tiers.

    Logic: Uses custom segmentation logic to categorize players into Diamond VIP, Platinum, and Gold groups based on lifetime wagered metrics.

2. High-Roller Intercept Guard

    Objective: Instantly logs high-dollar transactions into a security table for real-time dispatch.

    Logic: Uses an automated insert trigger to flag high-exposure records before they settle in the main ledger.

3. Automated Storage Performance Purge

    Objective: Frees up indexing overhead by purging zero-revenue slots and underperforming records.

    Logic: Implements a scheduled maintenance job to systematically prune inactive/zero-revenue data.

📊 Business Intelligence & Core Analytics

The database implements advanced multi-table relational analysis to extract actionable insights.
High-Roller Security Dispatch Protocol

Matches automated security triggers back to the core passenger ledger so hosts can identify high-rollers by name in real time:
SQL

SELECT 
    v.alert_id,
    p.player_name,
    v.large_wager,
    v.alert_status,
    v.alert_timestamp
FROM vip_alerts v
INNER JOIN player_activity p 
    ON v.player_id = p.player_id;

One final reminder: Ensure that you have actually moved your images into the docs/ folder in your project directory, and that you have committed and pushed those files to GitHub using the Source Control tab in VS Code. Without pushing those specific image files to the server, the links will remain broken on the live page.
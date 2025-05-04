# Market Microscope: Real-Time Market Anomaly Detection & Explanation System

**Market Microscope** is an in-progress, end-to-end system for detecting and explaining anomalies in financial market data, such as spread spikes, liquidity events, or latency arbitrage opportunities. Designed with high-frequency trading (HFT) principles, it combines robust data pipelines, a low-latency C++ limit order book (LOB) simulator, statistical anomaly detection, GenAI-powered summaries, and an interactive dashboard. This project showcases skills in quant engineering, market microstructure, and production-grade automation, targeting firms like Jane Street, Hudson River Trading, and Jump Trading.

**Note**: This project is actively under development. Some components (e.g., dashboard, GenAI integration) are in progress. See "Current Status" for details.

## Features
- **ETL Pipeline**: Processes tick-level market data (synthetic or from Yahoo Finance), storing it in Parquet for efficiency.
- **C++ LOB Simulator**: Simulates a limit order book to compute microstructure metrics (e.g., spread, order imbalance) with low-latency performance.
- **Anomaly Detection**: Identifies market anomalies using statistical methods (e.g., Z-scores) and C++-computed metrics.
- **GenAI Summaries**: Generates human-readable anomaly explanations using an LLM (in progress).
- **Interactive Dashboard**: Visualizes anomalies, LOB metrics, and summaries using Streamlit (in progress).
- **CI/CD Automation**: Automates testing, linting, and deployment via GitHub Actions and Docker.

## Why This Project?
This project demonstrates:
- **Technical Correctness**: Modular Python and C++ code with comprehensive tests.
- **Statistical Thinking**: Robust anomaly detection rooted in market microstructure.
- **Low-Latency Data Handling**: Optimized ETL and C++ LOB for high-throughput tick data.
- **Automation**: CI/CD pipelines for reliability and reproducibility.
- **HFT Relevance**: Focus on spreads, liquidity, and arbitrage, key HFT concepts.

## Installation
1. Clone the repository:
   ```bash
   git clone https://github.com/yourusername/hft-anomaly-detector.git
   cd hft-anomaly-detector
   ```
2. Set up a Python virtual environment:
   ```bash
   python -m venv venv
   source venv/bin/activate  # On Windows: venv\Scripts\activate
   ```
3. Install Python dependencies:
   ```bash
   pip install -r requirements.txt
   ```
4. Build the C++ module:
   ```bash
   mkdir cpp/build && cd cpp/build
   cmake ..
   make
   ```
5. (Optional) Set up Docker:
   ```bash
   docker build -t market-microscope .
   ```

## Usage
1. Run the ETL pipeline:
   ```bash
   python etl/etl_pipeline.py
   ```
   - Processes synthetic tick data or input CSV.
   - Outputs Parquet files in `data/processed/`.
2. Run the C++ LOB simulator:
   ```bash
   python detection/microstructure_stats.py
   ```
   - Calls the C++ module to compute LOB metrics.
3. Run anomaly detection:
   ```bash
   python detection/microstructure_stats.py
   ```
   - Detects spread spikes and imbalances.
4. Generate GenAI summaries (in progress):
   ```bash
   python genai/summarizer.py
   ```
   - Creates Markdown reports in `data/reports/`.
5. Launch the dashboard (in progress):
   ```bash
   streamlit run dashboard/app.py
   ```
   - View anomalies at `http://localhost:8501`.

## Project Structure
```
hft-anomaly-detector/
├── data/                      # Raw and processed market data
├── etl/                       # ETL scripts for data processing
├── detection/                 # Anomaly detection logic
├── cpp/                       # C++ LOB simulator
├── genai/                     # GenAI summarization
├── dashboard/                 # Streamlit dashboard
├── tests/                     # Unit tests for Python and C++
├── .github/workflows/         # CI/CD pipelines
├── Dockerfile                 # Docker configuration
└── README.md
```

## CI/CD
- **CI**: Runs `pytest`, `flake8`, C++ tests (`Catch2`), and data validation.
- **CD**: Deploys the dashboard to Render and updates pipelines on data push.
- Configured via `.github/workflows/ci-cd.yaml`.

## Current Status
- **In Progress**:  ETL pipeline, C++ LOB simulator, basic anomaly detection. 
- **Next Steps**: GenAI summarization, Streamlit dashboard, full CI/CD integration, deploy dashboard, integrate GenAI with RAG, add real-time data support.

## Design Choices
- **Parquet**: Efficient columnar storage for tick data.
- **C++ LOB**: Low-latency metric computation for HFT relevance.
- **Streamlit**: Lightweight for rapid dashboard prototyping.
- **Z-scores**: Simple, robust anomaly detection.

## Future Improvements
- Integrate real-time data from Polygon.io or Alpaca APIs.
- Scale the pipeline with `Dask` or Kafka.

## Demo
[Live dashboard link to be added upon completion]  
[Demo GIF/video to be added]


---
*In-progress project built for quant finance and systems engineering.*

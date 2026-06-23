# Unsupervised Machine Learning for Network Traffic Clustering

## 📝 Project Description
This project applies unsupervised machine learning—specifically the **DBSCAN** algorithm—to identify network anomalies and attacks without using pre-existing labels. 

It explores an empirical paradox: DBSCAN functions effectively in a controlled academic laboratory environment (**CIC-IDS-2017**), resolving **16 clean micro-clusters**. However, when deployed against chaotic, modern, real-world honeypot telemetry (**LUFlow 2022**), performance drops sharply into just **7 vague macro-clusters**. This confirms that modern internet background noise and attacker evasion techniques create a heavily overlapping feature space that degrades traditional spatial density boundaries.

---

## 🛠️ Tech Stack & Processing Flow
* **Core Libraries:** Python, Pandas, NumPy, Scikit-Learn (Machine Learning), Seaborn, Matplotlib, Joblib.
* **Balanced Ingestion:** Extracted 10,000 random rows across each daily log file to create an 80,000-row pool representing all attack categories safely without data omission.
* **Vertical Subsampling:** Extracted a random 20,000-row subset from the clean baseline matrix to prevent $O(N^2)$ memory allocations and RAM overflows while maintaining threat diversity.
* **Sanitization & Scaling:** Swapped math runtime anomalies (`inf`) for `NaN`, dropped corrupted records, and applied `StandardScaler` so high-range metrics did not distort Euclidean distances.
* **Evaluation & Visuals:** Linear Principal Component Analysis (PCA) was used to compress data down to 2D coordinates for visual scatter plotting. Silhouette Scoring mathematically validated cluster separation.

---

## 🚀 How to Run (Local Ubuntu Setup)

Execute these commands in your Ubuntu terminal to initialize the isolated environment and boot up the project:

```bash
# 1. Clone and enter the directory
git clone [https://github.com/your-username/your-repo-name.git](https://github.com/your-username/your-repo-name.git)
cd your-repo-name

# 2. Instantiate and activate the virtual environment
python3 -m venv venv
source venv/bin/activate

# 3. Install the project requirements inside the venv bubble
pip install -r requirements.txt

# 4. Launch the Jupyter development environment
jupyter lab

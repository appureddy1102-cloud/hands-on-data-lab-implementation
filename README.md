# Hands-On Data Lab Implementation

Repository: https://github.com/appureddy1102-cloud/hands-on-data-lab-implementation

## Overview and objectives
A reproducible beginner-level retail analysis demonstrating Python setup, data cleaning, descriptive statistics, Pandas manipulation and five Matplotlib/Seaborn charts. All transactions are synthetic; results are illustrative, not business evidence about real customers. No machine learning is fitted.

## Dataset
See [data/README.md](data/README.md). The raw CSV has 182 rows and five columns; it includes 2 exact duplicates and 4 missing unit values. The cleaned output has 180 rows and six columns. Created specifically for this project and released under CC0 1.0.

## Setup (Windows PowerShell)
Install Python 3.13 from https://www.python.org/downloads/ and select “Add Python to PATH”. In the project folder run:
```powershell
py -3.13 -m venv .venv
.\.venv\Scripts\Activate.ps1
python -m pip install --upgrade pip
python -m pip install -r requirements.txt
python -c "import sys,pandas,numpy,matplotlib,seaborn,sklearn; print(sys.version); print(pandas.__version__,numpy.__version__,matplotlib.__version__,seaborn.__version__,sklearn.__version__)"
python -m notebook
```
Open `notebooks/hands_on_data_lab.ipynb`, select the environment's Python kernel and choose Kernel → Restart Kernel and Run All Cells. Alternatively execute without the browser from the project root:
```powershell
python -m jupyter nbconvert --to notebook --execute --inplace notebooks/hands_on_data_lab.ipynb
```
`notebook` installs nbconvert as a dependency. On macOS/Linux use `python3.13 -m venv .venv` and `source .venv/bin/activate`. Installation commands are instructions; the Windows setup was not tested. The notebook was actually executed in the environment recorded in its first output and `outputs/analysis_summary.json`.

### Windows troubleshooting
- `py` not found: install Python and its launcher, reopen PowerShell, or use the full path to python.exe.
- Activation blocked: use `.venv\Scripts\python.exe -m pip install -r requirements.txt` and `.venv\Scripts\python.exe -m notebook`, or for the current shell only run `Set-ExecutionPolicy -Scope Process RemoteSigned` if permitted by policy.
- Module not found: install with the same interpreter that runs Jupyter; select its kernel. Register explicitly with `python -m ipykernel install --user --name data-lab --display-name "Python (data-lab)"`.
- Dependency installation fails: verify Python 3.13, update pip, and check network/proxy permissions.
- CSV not found: start from project root or notebooks folder and keep the provided folder structure.
- Port in use: run `python -m notebook --port 8890`.

## Exercises and output
The notebook reads and inspects the CSV, checks missingness and duplicates, converts dates and units, imputes category medians, computes revenue, filters/sorts/selects, aggregates and merges a validated lookup, exports cleaned data, computes statistics and generates five plots. Values are also saved in `outputs/analysis_summary.json`.

## Key findings
- Units are missing in 4/182 raw rows (2.20%); two rows are exact duplicates.
- Electronics generates $12,080 of the simulated $22,910 total, versus $7,590 for clothing and $3,240 for accessories.
- Mean transaction revenue is $127.28 and median is $80.00; the distribution has a high-value tail.
- Using global 1.5×IQR fences, 22 transactions are flagged; flags are not automatically errors.
- January has the highest monthly total ($4,775), February the lowest ($3,285) in this simulated period; months differ in length.
- Units and unit price have Pearson correlation 0.013, a near-zero linear association in these data.

## Structure
```
README.md
requirements.txt
data/{README.md,synthetic_sales.csv}
notebooks/hands_on_data_lab.ipynb
outputs/{cleaned_dataset.csv,analysis_summary.json,figures/}
report/Hands_On_Data_Lab_Report.docx
```

## References
- Pandas user guide: https://pandas.pydata.org/docs/user_guide/
- NumPy documentation: https://numpy.org/doc/
- Matplotlib documentation: https://matplotlib.org/stable/
- Seaborn documentation: https://seaborn.pydata.org/
- Python venv documentation: https://docs.python.org/3/library/venv.html
- Jupyter Notebook documentation: https://jupyter-notebook.readthedocs.io/
- Scikit-learn documentation: https://scikit-learn.org/stable/
- Tukey, J. W. (1977), *Exploratory Data Analysis*, Addison-Wesley (IQR fences).

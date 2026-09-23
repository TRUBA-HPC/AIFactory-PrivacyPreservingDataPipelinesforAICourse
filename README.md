![BSC AI Factory: Privacy-Preserving Data Pipelines for AI](assets/headers/course-banner.png)

# Privacy-Preserving Data Pipelines for AI

Five notebooks on protecting personal data in AI pipelines: document anonymization, re-identification risk, differential privacy, federated learning and homomorphic encryption.

| Notebook | Content |
| --- | --- |
| [01. Document anonymization](01_Document_Anonymization.ipynb) | Find the personal data in a two-page PDF with Presidio and two custom recognizers, and replace each value with a consistent fake from Faker. PyMuPDF redactions delete the originals, the metadata is cleared, and a check shows that no original value is left in the saved PDF. |
| [02. Re-identification risk](02_Reidentification_Risk.ipynb) | Link a hospital table without names to a public voter list on birth year, ZIP code and sex. Then generalize these fields and compare correct links, minimum group size (k) and distinct diagnoses per group (l-diversity). |
| [03. Differential privacy](03_Differential_Privacy.ipynb) | Rebuild every diagnosis from exact count queries, then add Laplace noise and compare reconstruction accuracy, count error and total ε across ε values. A privacy budget refuses the query that would exceed it. |
| [04. Federated learning](04_Federated_Learning.ipynb) | Train one logistic regression across four hospitals with FedAvg written in NumPy, and compare it with pooled and single-hospital training. Then one hospital sends a corrupted update, and weighted mean and median aggregation are compared. Optional: FedProx and FedAdam. |
| [05. Homomorphic encryption](05_Homomorphic_Encryption.ipynb) | Compile a decision tree with Concrete ML and split it into developer, server and clinic packages. The clinic encrypts a patient record, the server predicts on the ciphertext and the clinic decrypts the result, with the time and size cost of each step. Optional: the same round trip with logistic regression. |

## Run

Use **Python 3.11** and two separate environments: `requirements-core.txt` for notebooks 01 to 04 and `requirements-he.txt` for notebook 05. Notebook 05 needs macOS or Linux (WSL on Windows).

```bash
python3.11 -m venv .venv-core && .venv-core/bin/pip install -r requirements-core.txt
python3.11 -m venv .venv-he && .venv-he/bin/pip install -r requirements-he.txt
```

Open a notebook in Jupyter or VS Code with the matching environment as its kernel. The first code cell installs the pinned versions that notebook uses with `%pip`. If it installed or changed anything, restart the kernel, then run all cells in order.

The installs need internet access, and notebooks 04 and 05 download the [UCI Heart Disease dataset](https://doi.org/10.24432/C52P4X) into `data/` on the first run. Files the notebooks write (the PDFs in 01, the model packages and keys in 05) go to `generated/`.

## Code co-created by

Ülkü Tuncer Küçüktaş · Simge Danışoğlu · Tolga Turan · Gizem Acer

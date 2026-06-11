# 300Framework – P00_01: Review contracts
---
---
Score contracts based on whether or not they contain clauses that have the same meaning as a list of words that are mentioned in the AM_VARIABLES.txt source file.

## Instructions
Please note: this program automatically finds the requirements file and runs it. To use this functionality, ensure that you are in python version 3.12 or lower.

The below instructions enable you to run and test this project on your local machine. However, as mentioned in the masterclass, we can also use Kaggle to test, especially, if we are using a real LLM Gemma model, which requires quite a lot of CPU.

You will find the options to turn on and off test mode in AM_VARIABLES.

This program does not require you to input the root folder address. The program will infer the folder address. However, you need to make sure that you respect the folder structure as mentioned below for this inference to work.

### 1/ Create Virtual Environment

Ensure that you have Python version 3.12 on your machine. If you do not have it, download it from https://www.python.org/downloads. 

In Visual Studio Code, open a PowerShell terminal (File-> Terminal) at the location: (you can use cd to navigate to the 02_PROGRAMMES folder)

```text
PS C...\02_PROGRAMMES
```
Ensure that the address in the terminal matches C:\YourProjectRootFolder\02_PROGRAMMES.
The rest of the instructions are commands that we will run in the Powershell terminal at this location.

```bash
py -3.12 -m venv venv
```
After running, check that you have a \venv folder created inside 02_PROGRAMMES and that it contains python.exe inside \venv\Scripts and that you see pip3.12.exe

---

### 2/ Activate Virtual Environment using the Powershell activation program

```powershell
.\venv\Scripts\Activate.ps1
```
After activation, open a Python File from the 02_PROGRAMMES folder and check that the virtual environment, mentioned in the bottom-right corner of VSC, points to the python.exe inside your \venv\Scripts folder. If it does not, click on the venv mentioned in the bottom-right of VSC and browse to choose the correct python.exe from the \venv\Scripts folder.

---

### 3/ Install the required libraries, using the requirements.txt file. 

In this python project, the requirements will be installed automatically based on requirements.txt

---

### 4/ Create a .env file from the .env.example 

Updat the .env.example to your own Kaggle key. Then rename it as .env. See the webclass presentation for how to create a free key.

```bash
ZV_ST_HUGGINGFACE_KEY=hf_sFIXXXXXcKNtLpJsPbaZ
```

### 5/ Run the script

The first time you run the program, set the variables in AM_VARIABLES to:

ZV_ST_MODEL_ID=sshleifer/tiny-gpt2
ZV_ST_CATEGORIES='Contract Date,Effective Date,Renewal Term,Exit clause incl. notice period,Contract Parties,Documents Retention Period,Audit Clause,Audit Frequency,Audit Duration,Contract Fees,Payment Terms,Contract scope,KPIs,Service Level Agreement,Roles & Responsibilities,Deliverables,Contractual Reporting,Performance Review,Performance Bonus,Data Protection and Privacy,Confidentiality'
ZV_ST_TEST_MODE=True
ZV_ST_TEST_MODE_WO_LLM=True
ZV_ST_RESULTS_FILE=ContractReviewResults.xlsx

You can then try running with: 
ZV_ST_MODEL_ID=google/gemma-3-1b-it
ZV_ST_CATEGORIES='Contract Date,Effective Date,Renewal Term,Exit clause incl. notice period,Contract Parties,Documents Retention Period,Audit Clause,Audit Frequency,Audit Duration,Contract Fees,Payment Terms,Contract scope,KPIs,Service Level Agreement,Roles & Responsibilities,Deliverables,Contractual Reporting,Performance Review,Performance Bonus,Data Protection and Privacy,Confidentiality'
ZV_ST_TEST_MODE=False
ZV_ST_TEST_MODE_WO_LLM=False
ZV_ST_RESULTS_FILE=ContractReviewResults.xlsx

```bash
python P00_01_CONTRACT_REVIEW.py
```

If your VSC is picking up the wrong python.exe - ensure that your venv folder is in the 02_PROGRAMMES folder and that the terminal is in the 02_PROGRAMMES folder and then run the script with direct reference to the python.exe in the virtual environment: 

```bash
.\venv\Scripts\python.exe P00_01_CONTRACT_REVIEW.py
```

---
---

## Overview

This Python project performs the **300Framework P00_01: contract compliance review***

The objective of the test is to check whether or not the contracts in the sources folder contain clauses for all of the key words that are mentioned in the list in AM_VARIABLES

## Known required improvements

- None for the moment

## Typically used by

This test is commonly used by:

- Internal auditors
- Internal controllers
- Treasury department

This test is used to highlight contracts that are not compliant with internal control guidelines.

---

## Project Structure

```text
ROOT_FOLDER/
│
├── 01_SOURCES/
│   ├── contract.docx
│   ├── contract.pdf
│   ├── contract.doc
│   └── AM_VARIABLES.txt
│
├── 02_PROGRAMMES/
│   ├── P00_01_CONTRACT_REVIEW.py
│   ├── .env.example: update and change to .env
│   ├── pyproject.toml
│   └── requirements.txt
│
└── 03_RESULTS/
    └── ContractReviewResults.xlsx 

# SAP Source Files

The analysis does not work on SAP data. This analysis is based on non-structured data.

```

---

## Variables

Analysis parameters can be updated in:

```text
01_SOURCES/AM_VARIABLES.txt
```

Update the variables to control the model that you wish to use and whether or not you are in test mode:

ZV_ST_MODEL_ID=google/gemma-3-1b-it ... real gemma model - set to sshleifer/tiny-gpt2 for quick test with ZV_ST_TEST_MODE = true
ZV_ST_CATEGORIES='Contract Date,Effective Date,Renewal Term,Exit clause incl. notice period,Contract Parties,Documents Retention Period,Audit Clause,Audit Frequency,Audit Duration,Contract Fees,Payment Terms,Contract scope,KPIs,Service Level Agreement,Roles & Responsibilities,Deliverables,Contractual Reporting,Performance Review,Performance Bonus,Data Protection and Privacy,Confidentiality'
ZV_ST_TEST_MODE=False ... do not truncate the text or tokens, etc, run on all the files
ZV_ST_TEST_MODE_WO_LLM=False .. .actually download and use the model
ZV_ST_RESULTS_FILE=ContractReviewResults.xlsx




## General best-practice reminders

- Results should be reviewed and interesting samples taken: simple NLP models may only be 90% accurate, especially if the small model is used.
- Results should be reviewed by qualified audit or procurement professionals and samples discussed with the business before any action plans or audit recommendations are drafted.

---

## 300Framework

300Framework provides AI-enhanced data audit analytics, for SAP environments, helping audit teams compute risk indicators, identify control weaknesses and sample high-risk transactions and third-parties.













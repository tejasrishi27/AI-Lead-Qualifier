# 🤖 AI Lead Qualifier

An AI-powered lead qualification and prioritization system built with Python, OpenRouter, and Pandas.

The system takes raw customer inquiries from a CSV file, analyzes them using an AI model, extracts useful lead information, calculates a priority score, and generates a structured CSV containing qualified leads.

## 🚀 What It Does

Businesses receive customer inquiries in many different forms. Some customers need immediate help, while others are simply researching prices.

This project automatically analyzes those inquiries and determines:

* **Service** — HVAC, Plumbing, Roofing, Electrical, Cleaning, etc.
* **Urgency** — Low, Medium, or High
* **Intent** — What the customer wants
* **Buying likelihood** — Low, Medium, or High
* **Lead score** — Numerical priority score
* **Priority** — HOT, WARM, or COLD

### Pipeline

```text
Customer CSV
     ↓
Python
     ↓
OpenRouter AI
     ↓
Lead Classification
     ↓
Urgency + Buying Score
     ↓
Priority Assignment
     ↓
Qualified Leads CSV
```

## ✨ Features

* AI-powered lead classification
* Batch processing of CSV files
* Structured JSON responses
* Lead scoring system
* HOT / WARM / COLD prioritization
* API error handling
* Timeout handling
* Connection error handling
* Invalid JSON handling
* Missing-field validation
* Rate-limit handling
* CSV input and output
* Secure API-key handling through Google Colab Secrets

## 🧮 Lead Scoring

The system converts qualitative values into numerical scores.

### Urgency

| Level  | Score |
| ------ | ----: |
| High   |     3 |
| Medium |     2 |
| Low    |     1 |

### Buying Likelihood

| Level  | Score |
| ------ | ----: |
| High   |     3 |
| Medium |     2 |
| Low    |     1 |

The final score is:

```text
Lead Score = Urgency × Buying Likelihood
```

### Priority

| Score | Priority |
| ----: | -------- |
|   7–9 | HOT      |
|   4–6 | WARM     |
|   1–3 | COLD     |

## 📂 Input Format

The input CSV should contain:

```csv
customer_name,email,message
John Doe,john@example.com,My AC stopped working and I need someone today.
Sarah Smith,sarah@example.com,I would like a quote for cleaning my apartment.
Mike Jones,mike@example.com,How much does a roof inspection cost?
```

## 📊 Output Format

The program generates:

```text
qualified_leads.csv
```

Example:

| Name        | Email                                         | Issue                 | Service  | Urgency | Intent           | Buying | Score | Priority |
| ----------- | --------------------------------------------- | --------------------- | -------- | ------- | ---------------- | ------ | ----: | -------- |
| John Doe    | [john@example.com](mailto:john@example.com)   | AC stopped working... | HVAC     | High    | Wants repair     | High   |     9 | HOT      |
| Sarah Smith | [sarah@example.com](mailto:sarah@example.com) | Cleaning quote...     | Cleaning | Medium  | Requesting quote | Medium |     4 | WARM     |

## 🛠️ Tech Stack

* **Python**
* **OpenRouter API**
* **NVIDIA Nemotron**
* **Pandas**
* **Requests**
* **JSON**
* **CSV**
* **Google Colab**

## 🔑 API Key Setup

This project uses an OpenRouter API key.

Do **not** hard-code your API key into the source code.

In Google Colab:

1. Open the **Secrets** panel.
2. Create a secret named:

```text
OPENROUTER_API_KEY
```

3. Add your OpenRouter API key.
4. Enable notebook access for the secret.

The code retrieves it using:

```python
from google.colab import userdata

api_key = userdata.get("OPENROUTER_API_KEY")
```

## ▶️ How to Run

### 1. Open the notebook

Open the `.ipynb` file in Google Colab.

### 2. Add your API key

Create the `OPENROUTER_API_KEY` Colab secret.

### 3. Prepare your CSV

Upload a CSV containing:

```text
customer_name
email
message
```

### 4. Run the program

Enter the CSV filename when prompted.

The program will:

```text
Read CSV
   ↓
Process each customer message
   ↓
Send message to AI
   ↓
Classify lead
   ↓
Calculate score
   ↓
Assign priority
   ↓
Create qualified_leads.csv
```

## 🧠 Example

### Input

```text
My AC is running but isn't cooling the house. I need someone to come out before the weekend.
```

### AI Classification

```json
{
    "Service": "HVAC",
    "Urgency": "Medium",
    "Intent": "Wants repair",
    "Buying": "High"
}
```

### Score

```text
Urgency = 2
Buying = 3

Score = 2 × 3
Score = 6
```

### Final Priority

```text
WARM
```

## 🛡️ Error Handling

The application handles several common failures:

* Missing API key
* Empty customer messages
* Request timeouts
* Connection failures
* HTTP errors
* Unauthorized API requests
* Rate limits
* Server errors
* Invalid API responses
* Invalid JSON
* Missing classification fields
* Invalid urgency/buying values

This prevents a single failed lead from unnecessarily crashing the entire batch-processing workflow.

## 📈 Possible Improvements

Future versions could include:

* Google Sheets integration
* CRM integration
* Real-time lead processing
* Email notifications for HOT leads
* Web dashboard
* Lead history
* Custom scoring rules
* Multiple AI providers
* Database storage
* REST API
* Automatic lead routing
* Human review workflow

## 💼 Business Use Cases

This system could be adapted for:

* HVAC companies
* Roofing companies
* Plumbing companies
* Electrical contractors
* Cleaning companies
* Landscaping businesses
* Appliance repair companies
* Pest control companies
* Home-service marketplaces
* Marketing agencies

## 🎯 Project Goal

The goal of this project is to demonstrate how AI can transform unstructured customer messages into structured, actionable business data.

Instead of manually reviewing every inquiry, businesses can automatically identify and prioritize their most valuable leads.

## 👨‍💻 Author

Built as a Python + AI automation portfolio project.

### Core Skills Demonstrated

* Python automation
* REST APIs
* AI integration
* Prompt engineering
* JSON processing
* Error handling
* Data processing
* Pandas
* CSV automation
* Lead scoring
* Batch processing

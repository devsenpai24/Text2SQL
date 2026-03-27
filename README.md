# Text2SQL
# 🧠 Text2SQL with Gemini (E-commerce Data Analysis)

This project demonstrates how to build a **Text-to-SQL pipeline** using a SQLite database and a Generative AI model (Gemini). It allows users to ask **natural language questions** and automatically converts them into SQL queries, executes them, and returns results.

---

## 📌 Overview

This notebook walks through:

* Creating a mock **e-commerce database**
* Loading structured data into SQLite
* Integrating **Google Gemini API**
* Translating natural language → SQL
* Executing SQL queries and returning results

---

## 📂 Project Structure

```
Text2SQL/
│── text2sql.ipynb
│── customers.csv
│── products.csv
│── orders.csv
│── ecommerce.db
```

---

## ⚙️ Setup

### 1. Clone Repository

```bash
git clone https://github.com/devsenpai24/Text2SQL.git
cd Text2SQL
```

---

### 2. Install Dependencies

```bash
pip install pandas sqlite3 google-generativeai
```

---

### 3. Download Dataset

Mock e-commerce data is generated using Mockaroo:

```bash
curl "https://api.mockaroo.com/api/dde01370?count=1000&key=11149690" > customers.csv
curl "https://api.mockaroo.com/api/8ba6f630?count=1000&key=11149690" > products.csv
curl "https://api.mockaroo.com/api/6fa67fe0?count=3000&key=11149690" > orders.csv
```

---

## 🗄️ Database Setup

* SQLite database: `ecommerce.db`
* Tables:

  * `customers`
  * `products`
  * `orders`

Steps performed:

* Define schema
* Load CSVs using pandas
* Clean and validate data
* Insert into database

---

## 🤖 Gemini API Integration

* Install SDK:

```bash
pip install google-generativeai
```

* Set your API key:

```python
API_KEY = "your_api_key_here"
```

* Initialize client:

```python
from google import genai
client = genai.Client(api_key=API_KEY)
```

---

## 🔄 Text-to-SQL Pipeline

### Core Functions

#### 1. Generate SQL from Natural Language

```python
get_sql_query_via_gemini(genai_client, prompt, user_query)
```

#### 2. Execute SQL Query

```python
execute_query(query, db_name='ecommerce.db')
```

#### 3. Full Pipeline

```python
text2sql(genai_client, prompt, user_query)
```

---

## 💡 Example Queries

### 📊 Distinct Country Count

```python
text2sql(genai_client, prompt, "Show me the distinct country count in customers")
```

---

### 🥈 2nd Highest Sold Product per Country

```python
text2sql(genai_client, prompt, "What is the 2nd highest sold product for each country?")
```

---

## 🚀 Features

* Natural Language → SQL conversion
* SQLite database integration
* Automated query execution
* Modular and reusable functions
* Works with real-world structured datasets

---

## 🛠️ Tech Stack

* Python
* SQLite
* Pandas
* Google Gemini API

---

## ⚠️ Notes

* Ensure your API key is kept secure
* Large queries may incur API costs
* Schema accuracy is critical for good SQL generation

---

## 📈 Future Improvements

* Add UI (Streamlit / Web App)
* Support multiple databases (PostgreSQL, MySQL)
* Improve prompt engineering for better SQL accuracy
* Add query validation & error handling

---

## 🤝 Contributing

Feel free to fork this repo and submit pull requests!

---

## 📜 License

This project is open-source and available under the MIT License.

---

## ⭐ Acknowledgements

* Mockaroo for dataset generation
* Google Gemini for NLP capabilities

---


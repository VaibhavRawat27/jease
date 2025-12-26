# JEase 🚀  
### JSON Made Easy for Python

JEase is a **lightweight, beginner-friendly, and chainable Python library** designed to make working with JSON data simple, safe, and expressive.  
It helps you **read, transform, filter, update, and analyze JSON** without messy loops or `try/except` blocks.

---

## 📌 Why JEase?

Working with nested JSON often leads to:
- Deeply nested loops
- KeyErrors and missing data crashes
- Hard-to-read transformation logic

**JEase solves this by providing:**
- Safe nested access
- Chainable operations
- Simple syntax inspired by real-world usage
- Zero external dependencies

---

## 📦 Installation

```bash
pip install jease
```

---

## 🚀 Quick Start

```python
from jease import JEase

data = {
    "users": [
        {"name": "Alice", "age": 25, "location": {"city": "NY"}},
        {"name": "Bob", "age": 30},
        {"name": "Charlie", "age": 35, "location": {"city": "LA"}}
    ]
}

JEase(data) \
    .get("users") \
    .filter(age__gte=30) \
    .pluck("location.city", default="Unknown") \
    .unique() \
    .show()
```

**Output**
```
['Unknown', 'LA']
```

---

## ✨ JEase v1.0 Features

### 1️⃣ Safe Data Access
- `get(key_path, default=None)`
- Access deeply nested keys safely

```python
JEase(data).get("users.0.location.city", "NA").show()
```

---

### 2️⃣ Filtering
- Filter lists of dictionaries using conditions

Supported operators:
- `__eq`
- `__gte`
- `__lte`

```python
JEase(data).get("users").filter(age__gte=30).show()
```

---

### 3️⃣ Mapping & Plucking
- Extract keys or apply functions

```python
JEase(data).get("users").pluck("name").show()
```

---

### 4️⃣ Sorting
- Sort JSON lists by keys

```python
JEase(data).get("users").sort("age", desc=True).show()
```

---

### 5️⃣ Aggregations
Supported:
- `sum`, `mean`, `min`, `max`, `count`, `median`

```python
JEase(data).get("users").aggregate("age", "mean")
```

---

### 6️⃣ JSON Mutation (Write Operations)

#### Update nested values
```python
JEase(data).update("users.1.location.city", "Chicago").show()
```

#### Remove keys
```python
JEase(data).remove("users.0.age").show()
```

#### Merge JSON
```python
JEase(data).merge({"active": True}).show()
```

---

### 7️⃣ Utility Helpers

| Method | Description |
|------|------------|
| `unique()` | Unique values |
| `exists(path)` | Check if key exists |
| `keys()` | Get keys |
| `values()` | Get values |
| `length()` | Size of JSON |
| `to_list()` | Convert to Python list |

---

### 8️⃣ Pretty Printing & Reports

```python
JEase(data).show()
```

- Auto pretty-prints JSON
- Useful for debugging

```python
JEase(data).get("users").report()
```

---

## 🧠 Real-world Use Cases

### ✅ API Responses
Clean, validate, and transform API JSON safely.

### ✅ Data Cleaning
Handle missing keys and inconsistent structures.

### ✅ Rapid Prototyping
Quick insights without Pandas overhead.

### ✅ Beginners
Ideal for students and early Python developers.

---

## 🗂 Project Structure

```
jease/
├── jease/
│   ├── __init__.py
│   └── core.py
├── tests/
│   └── test_core.py
├── README.md
├── setup.py
├── LICENSE
└── pyproject.toml
```

---

## 🧪 Testing

```bash
python tests/test_core.py
```

---

## 📈 Versioning

| Version | Description |
|-------|------------|
| v0.1.0 | Initial public release |

---

## 🛣 Roadmap

- JSON path queries
- CSV export support
- Schema validation
- Pandas interoperability

---

## 🤝 Contributing

Contributions are welcome!
- Fork the repo
- Create a feature branch
- Submit a pull request

---

## 🔓 License

MIT License

---

## ⭐ Support

If you find JEase useful:
- Star the GitHub repo ⭐
- Share with friends
- Open issues or suggestions

---

**JEase — JSON doesn’t have to be hard.**

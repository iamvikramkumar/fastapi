# FastAPI with Uvicorn

## 🌀 What is FastAPI?
FastAPI is a modern, fast (high-performance) web framework for building APIs with Python 3.6+ based on standard Python type hints. It is built on top of **Starlette** and **Pydantic**.

## 🧱 What is Pydantic?
Pydantic is a powerful data validation and settings management library for Python. FastAPI uses Pydantic to:

- ✅ Validate incoming request data
- ✅ Automatically generate error messages if data is invalid
- ✅ Define data models with Python type hints
- ✅ Auto-generate JSON schemas for documentation (like Swagger UI)

### ✨ Example with Pydantic:
```python
from pydantic import BaseModel
from fastapi import FastAPI

app = FastAPI()

class Item(BaseModel):
    name: str
    price: float

@app.post("/items/")
def create_item(item: Item):
    return {"name": item.name, "price": item.price}
```
In this example, Pydantic ensures that `name` is a string and `price` is a float. If a user sends incorrect data, FastAPI automatically returns a helpful error.

### 🧒 Simple Explanation (Kid-Friendly)
Think of **Pydantic** as a smart security guard for your data. It makes sure:

- The right type of data is sent (like name must be a string, price must be a number)
- Nothing important is missing
- If anything is wrong, it shows an error right away

#### Example:
You want kids to send:
- Their name (a string)
- How many toys they want (a number)

With Pydantic:
```python
from pydantic import BaseModel

class ToyOrder(BaseModel):
    name: str
    quantity: int
```
If someone sends `"name": 123` or `"quantity": "five"`, Pydantic will say ❌ "This is not valid" — and FastAPI will return a clear error message to the user.

## 🚀 How FastAPI Runs
FastAPI applications **do not have their own server**. Instead, they are served using ASGI servers like **Uvicorn** or **Hypercorn**.

## 🔧 Running FastAPI Apps

### ✅ Recommended Way (Using Uvicorn CLI)
Use the Uvicorn command-line tool to start your FastAPI app:

```bash
uvicorn main:app --reload
```

- `main`: name of your Python file (e.g., `main.py`)
- `app`: the FastAPI instance (e.g., `app = FastAPI()`)
- `--reload`: auto-reloads the server when you make code changes (for development only)

### 🧪 Alternative Way (Direct Python Execution)
You can also run your FastAPI app by calling `uvicorn.run()` inside your Python script:

```python
import uvicorn
from fastapi import FastAPI

app = FastAPI()

@app.get("/")
def read_root():
    return {"message": "Hello World"}

if __name__ == "__main__":
    uvicorn.run("main:app", host="127.0.0.1", port=8000, reload=True)
```

Then run:
```bash
python main.py
```

## 🤔 Which One to Use?
| Method                        | When to Use             |
|------------------------------|--------------------------|
| `uvicorn main:app --reload` | ✅ Preferred for development and production |
| `python main.py`            | ✅ Good for quick testing or small apps     |

## 📌 Note
Even when running directly using `python main.py`, you're still using **Uvicorn** — just programmatically, instead of via the command line.

---
Happy coding with FastAPI! 🎉

# CrewAI First Agent

AI research agent project built using CrewAI and Google Gemini.

## 👨‍💻 Author

**Mahmoud Yasser**

---

# 🚀 Project Overview

This project demonstrates how to build a simple AI Agent using:

- CrewAI
- Google Gemini
- Async Execution
- Sequential Task Processing

The agent acts as a professional market researcher capable of analyzing trends and generating reports automatically.

---

# 🧠 Technologies Used

```txt
Python
CrewAI
Google Gemini
Google Colab
nest_asyncio
```

---

# 📂 Project Structure

```txt
project/
│
├── main.py
├── README.md
└── requirements.txt
```

---

# ⚙️ Installation

```bash
pip install crewai
pip install nest_asyncio
```

---

# 🔑 Setup API Key

```python
from google.colab import userdata
import os

os.environ["GOOGLE_API_KEY"] = userdata.get("gemini")
```

---

# 🛠 Environment Configuration

```python
import nest_asyncio

# Fix Event Loop issue inside Google Colab
nest_asyncio.apply()

print("Environment configured successfully!")
```

---

# 🤖 Create Gemini LLM

```python
import os
from crewai import LLM

gemini_llm = LLM(
    model="gemini/gemini-2.5-flash",
    temperature=0.5,
    api_key=os.environ["GOOGLE_API_KEY"]
)
```

---

# 👨‍💼 Create AI Agent

```python
from crewai import Agent

researcher_agent = Agent(
    role="Professional Market Researcher and Data Analyst",
    
    goal="""
    Analyze data and gather the most accurate information
    and latest trends in any requested field
    """,

    backstory="""
    You are a professional researcher with 10 years of experience
    in generating reports and understanding markets with high accuracy.
    """,

    llm=gemini_llm,
    verbose=True
)
```

---

# 📋 Create Task

```python
from crewai import Task

research_task = Task(
    description="""
    Analyze the importance of using AI Agents
    in the job market by 2026 and mention
    their most important advantage.
    """,

    expected_output="""
    A short report in English containing:
    - Introduction
    - Key Points
    - Conclusion
    """,

    agent=researcher_agent
)
```

---

# 🧩 Create Crew

```python
from crewai import Crew, Process

analysis_crew = Crew(
    agents=[researcher_agent],
    tasks=[research_task],
    process=Process.sequential
)
```

---

# ▶️ Run The Project

```python
result = await analysis_crew.kickoff_async()

print("\n###################################")
print("## Final Result From The Agent")
print("###################################\n")

print(result)
```

---

# 🔄 Workflow Diagram

```txt
+-------------------+
|   Gemini API Key  |
+-------------------+
          |
          v
+-------------------+
|    Gemini LLM     |
+-------------------+
          |
          v
+-------------------+
|     AI Agent      |
+-------------------+
          |
          v
+-------------------+
|       Task        |
+-------------------+
          |
          v
+-------------------+
|       Crew        |
+-------------------+
          |
          v
+-------------------+
|   Final Result    |
+-------------------+
```

---

# 📌 Example Output

```txt
AI Agents are expected to play a major role in the job market by 2026.

Key Advantages:
- Faster automation
- Reduced operational costs
- Better data analysis
- 24/7 task execution
- Improved productivity
```

---

# 🎯 Future Improvements

```txt
- Add multiple agents
- Integrate memory systems
- Add tools support
- Build autonomous workflows
- Connect with APIs
```

---

# 📄 License

```txt
This project is for educational purposes.
```

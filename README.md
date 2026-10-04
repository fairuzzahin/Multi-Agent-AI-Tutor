# Leo — Multi-Agent AI Tutor

Leo is a multi-agent AI tutoring system built with **CrewAI** and **Groq**. It helps students learn a topic, practice through a quiz, and receive feedback based on their answers.

## 🤖 Agents and Roles

| Agent           | Role                                                                       |
| --------------- | -------------------------------------------------------------------------- |
| **Coordinator** | Understands the student's request and organizes the learning workflow.     |
| **Explainer**   | Explains the selected topic according to the student's level and language. |
| **Quiz Master** | Creates 5 multiple-choice questions based on the lesson.                   |
| **Evaluator**   | Evaluates the student's answers and provides feedback and recommendations. |

## 🏗️ Architecture

```text
                  ┌─────────────────┐
                  │     Student     │
                  │ Name / Topic /  │
                  │ Level / Language│
                  └────────┬────────┘
                           │
                           ▼
                  ┌─────────────────┐
                  │   Coordinator   │
                  │ Workflow        │
                  └────────┬────────┘
                           │
                           ▼
                  ┌─────────────────┐
                  │    Explainer    │
                  │ Teach Topic     │
                  └────────┬────────┘
                           │
                           ▼
                  ┌─────────────────┐
                  │   Quiz Master   │
                  │ Generate 5 MCQs │
                  └────────┬────────┘
                           │
                           ▼
                  ┌─────────────────┐
                  │     Student     │
                  │ Submit Answers  │
                  └────────┬────────┘
                           │
                           ▼
                  ┌─────────────────┐
                  │ Python Scoring  │
                  │ Calculate Score │
                  └────────┬────────┘
                           │
                           ▼
                  ┌─────────────────┐
                  │    Evaluator    │
                  │ Feedback        │
                  └────────┬────────┘
                           │
                           ▼
                  ┌─────────────────┐
                  │   Final Result  │
                  │ Score + Feedback│
                  └─────────────────┘
```

## 🔄 Orchestration Pattern

Leo uses a **Sequential Orchestration Pattern** with CrewAI.

The agents execute in the following order:

```text
Coordinator
     ↓
Explainer
     ↓
Quiz Master
     ↓
Student Answers
     ↓
Python Score Calculation
     ↓
Evaluator
```

Each downstream task receives the relevant output from the previous task through **CrewAI task context**.

The quiz score is calculated using Python rather than an LLM to keep the result deterministic.

## 🛠️ Technologies

* Python
* CrewAI
* Groq API
* `openai/gpt-oss-20b`
* LiteLLM
* Pydantic
* Google Colab

## ▶️ How to Run

### 1. Clone the repository

```bash
git clone https://github.com/YOUR_USERNAME/Leo-Multi-Agent-AI-Tutor.git
cd Leo-Multi-Agent-AI-Tutor
```

### 2. Install dependencies

```bash
pip install -r requirements.txt
```

### 3. Configure the Groq API Key

Create a `.env` file:

```env
GROQ_API_KEY=your_groq_api_key
```

**Do not commit the `.env` file or API key to GitHub.**

### 4. Open the Notebook

Open:

```text
Leo_Multi_Agent_AI_Tutor.ipynb
```

Run the notebook cells sequentially in **Google Colab**.

### 5. Enter Student Information

Leo asks the student for:

```text
Name
Topic
Level
Preferred Language
```

Example:

```text
Enter your name: Sneha
What topic do you want to learn? Literature
What is your level? Intermediate
Preferred language? Bangla
```

Leo then runs the multi-agent workflow and produces the lesson, quiz, score, and personalized evaluation.

## 📁 Project Structure

```text
Leo-Multi-Agent-AI-Tutor/
│
├── Leo_Multi_Agent_AI_Tutor.ipynb
├── README.md
├── requirements.txt
└── .gitignore
```

## 👩‍💻 Author

**Fairuz Zahin Sneha**

Bangladesh

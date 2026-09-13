# 🧠 Trivi.AI

> **An AI-Powered Quiz Application built with Python and Tkinter**

Trivi.AI is an AI-powered desktop quiz application designed to provide an interactive and engaging quiz experience.

The application includes user authentication, account creation, password recovery, an AI-powered quiz interface, XP-based scoring, and a leaderboard for tracking top users.

---

## 🚀 Features

* 🔐 User Login
* 📝 User Registration / Signup
* 🔑 Forgot Password
* 🧠 AI-Powered Quiz Generation
* 🎯 Interactive Quiz Interface
* ⭐ XP-Based Reward System
* 🏆 Top Users / Leaderboard
* 👤 User Profile & Progress
* 💾 Persistent User Data
* 🖥️ Desktop GUI Application
* 🎨 Customizable UI Theme
* 🔄 Multi-Screen Navigation

---

## 🧠 Application Workflow

The application follows a simple user-friendly workflow:

```text
                    ┌──────────────┐
                    │   Trivi.AI   │
                    └──────┬───────┘
                           │
                           ▼
                    ┌──────────────┐
                    │     Login    │
                    └──────┬───────┘
                           │
             ┌─────────────┼─────────────┐
             │             │             │
             ▼             ▼             ▼
        ┌─────────┐   ┌──────────┐  ┌──────────┐
        │ Signup  │   │  Forgot  │  │  Login   │
        │         │   │ Password │  │ Success  │
        └─────────┘   └──────────┘  └────┬─────┘
                                         │
                                         ▼
                                  ┌──────────────┐
                                  │  Dashboard   │
                                  └──────┬───────┘
                                         │
                         ┌───────────────┼───────────────┐
                         │               │               │
                         ▼               ▼               ▼
                    ┌─────────┐    ┌──────────┐   ┌────────────┐
                    │   Quiz  │    │ Top Users│   │ User Stats │
                    └────┬────┘    └──────────┘   └────────────┘
                         │
                         ▼
                    ┌─────────┐
                    │   XP    │
                    │ +50 Win │
                    └─────────┘
```

---

## 🎮 Quiz & XP System

Trivi.AI uses an XP-based reward system to motivate users.

When a user successfully completes a quiz:

```python
users[email]["xp"] += 50
```

The user's XP is updated in the persistent user data and reflected in the current session.

### XP Reward

| Result    |     XP |
| --------- | -----: |
| Quiz Won  | +50 XP |
| Quiz Lost |  No XP |

The accumulated XP can be used to rank users on the **Top Users leaderboard**.

---

## 🖥️ Screens

Trivi.AI is organized into separate screens for better maintainability.

### 🔐 Login Screen

Allows existing users to securely log into the application.

---

### 📝 Signup Screen

Allows new users to create an account.

---

### 🔑 Forgot Password Screen

Provides a dedicated interface for users who have forgotten their password.

---

### 🏠 Dashboard

After successful authentication, users are redirected to the dashboard.

The dashboard acts as the central navigation point for the application.

---

### 🧠 Quiz Screen

The quiz interface provides the main gameplay experience.

The `QuizBotGUI` class is responsible for displaying and managing the quiz interface.

---

### 🏆 Top Users

The leaderboard displays users according to their accumulated XP.

This introduces a competitive element and encourages users to improve their quiz performance.

---

## 🏗️ Project Architecture

The application follows a modular screen-based architecture.

```text
Trivi.AI
│
├── Application
│   └── TriviAIApp
│
├── Authentication
│   ├── LoginScreen
│   ├── SignupScreen
│   └── ForgotScreen
│
├── Main Application
│   ├── DashboardScreen
│   ├── QuizBotGUI
│   └── TopUsersScreen
│
├── Data
│   └── users
│
└── Configuration
    └── config.py
```

---

## 📁 Suggested Project Structure

```text
Trivi.AI/
│
├── main.py
├── config.py
├── users.py
│
├── screens/
│   ├── __init__.py
│   ├── login.py
│   ├── signup.py
│   ├── forgot.py
│   ├── dashboard.py
│   ├── quiz.py
│   └── top_users.py
│
├── assets/
│   └── ...
│
├── data/
│   └── ...
│
├── requirements.txt
├── README.md
└── .gitignore
```

---

## 🛠️ Technologies Used

| Technology              | Purpose                             |
| ----------------------- | ----------------------------------- |
| **Python**              | Core application development        |
| **Tkinter**             | Desktop graphical user interface    |
| **AI / LLM API**        | AI-powered quiz functionality       |
| **JSON / File Storage** | User data persistence               |
| **OOP**                 | Application and screen architecture |

---

## ⚙️ Requirements

Before running Trivi.AI, make sure you have:

* Python 3.9 or later
* Internet connection if the AI API is enabled
* Required Python packages installed through `requirements.txt`

---

## 📥 Installation

### 1. Clone the Repository

```bash
git clone https://github.com/M-Awais-11/Trivi.AI-.git
```

Navigate to the project:

```bash
cd Trivi.AI-
```

---

### 2. Create a Virtual Environment

#### Windows

```bash
python -m venv venv
```

Activate it:

```bash
venv\Scripts\activate
```

#### Linux / macOS

```bash
python3 -m venv venv
```

Activate it:

```bash
source venv/bin/activate
```

---

### 3. Install Dependencies

```bash
pip install -r requirements.txt
```

---

## ▶️ Run the Application

Start the application with:

```bash
python main.py
```

The Trivi.AI desktop application will open in a Tkinter window.

---

## 🔐 Authentication Flow

The application starts with the login screen:

```python
self.show_screen("login")
```

Users can navigate between:

```text
Login
  │
  ├── Signup
  │
  ├── Forgot Password
  │
  └── Dashboard
```

Once authenticated, the current user is stored in:

```python
self.current_user
```

This allows the application to maintain the user's session while navigating between screens.

---

## 🔄 Screen Navigation

The application uses a centralized screen management system.

```python
def show_screen(self, name: str):
```

Depending on the requested screen, the application initializes the appropriate GUI class.

For example:

```python
if name == "login":
    self.screens[name] = LoginScreen(self.root, self)

elif name == "dashboard":
    self.screens[name] = DashboardScreen(self.root, self)

elif name == "quiz":
    QuizBotGUI(self.root, self)
```

This architecture keeps individual screens separated and makes the application easier to maintain and extend.

---

## 🧩 Core Components

### `TriviAIApp`

The main application controller.

Responsibilities include:

* Initializing the application window
* Managing the current user
* Managing application screens
* Switching between screens
* Updating user XP

---

### `LoginScreen`

Handles user authentication.

---

### `SignupScreen`

Handles new user registration.

---

### `ForgotScreen`

Handles password recovery.

---

### `DashboardScreen`

Provides the main application interface after login.

---

### `QuizBotGUI`

Provides the interactive AI-powered quiz experience.

---

### `TopUsersScreen`

Displays the highest-ranked users based on XP.

---

## 🎯 Design Goals

Trivi.AI was designed around the following goals:

### Simplicity

Provide a straightforward interface that users can understand quickly.

### Engagement

Use XP and leaderboard functionality to encourage continued participation.

### Modularity

Separate each screen into its own Python module.

### AI Integration

Use AI capabilities to make quiz generation and interaction more dynamic.

### Extensibility

Provide an architecture that can be expanded with additional quiz modes and features.

---

## 🔮 Future Improvements

Potential improvements include:

* 🎯 Multiple quiz categories
* 📊 Detailed user statistics
* ⏱️ Timed quizzes
* 🏅 Achievement and badge system
* 🔥 Daily quiz challenges
* 📈 XP levels
* 🌎 Global leaderboard
* 🎨 Dark / Light themes
* 🧠 Adaptive difficulty
* 💬 AI explanations for answers
* 📚 Quiz history
* 🔊 Voice-based quiz interaction
* 📝 Custom user-generated quizzes
* ☁️ Cloud-based user accounts
* 🗄️ Database integration
* 📱 Mobile version

---

## 📊 Example User Journey

```text
User
 │
 ▼
Open Trivi.AI
 │
 ▼
Login / Signup
 │
 ▼
Dashboard
 │
 ▼
Start Quiz
 │
 ▼
Answer Questions
 │
 ▼
Quiz Result
 │
 ▼
+50 XP
 │
 ▼
Updated User Progress
 │
 ▼
Leaderboard
```

---

## 🧪 Development Concepts

This project demonstrates practical implementation of:

* Python Object-Oriented Programming
* Tkinter GUI development
* Modular application architecture
* Event-driven programming
* User authentication
* State management
* File-based data persistence
* AI integration
* Quiz generation
* Gamification
* Leaderboard systems

---

## ⚠️ Notes

If the project uses an external AI API, make sure API credentials are stored securely.

Do **not** commit API keys or passwords directly to GitHub.

Use environment variables such as:

```text
.env
```

and add the file to `.gitignore`.

---

## 👨‍💻 Author

**M. AWAIS AFZAL**

Computer Science | AI/ML | Computer Vision | Software Development

GitHub:

```text
https://github.com/M-Awais-11
```

---

## ⭐ Support

If you find Trivi.AI useful or interesting, consider giving the repository a ⭐ on GitHub.

---

## 📄 License

This project is intended for educational and personal use.

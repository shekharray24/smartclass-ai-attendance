<div align="center">

# 🤖 SmartClass — AI Attendance System

### 🎓 Making classroom attendance faster using AI

A modern **Streamlit-based attendance management system** that combines **AI-powered face recognition**, **Supabase**, and **voice-related tools** to simplify classroom attendance.

<br>

![Python](https://img.shields.io/badge/Python-3.x-3776AB?style=for-the-badge&logo=python&logoColor=white)
![Streamlit](https://img.shields.io/badge/Streamlit-App-FF4B4B?style=for-the-badge&logo=streamlit&logoColor=white)
![Supabase](https://img.shields.io/badge/Supabase-Database-3ECF8E?style=for-the-badge&logo=supabase&logoColor=white)
![scikit--learn](https://img.shields.io/badge/scikit--learn-ML-F7931E?style=for-the-badge&logo=scikit-learn&logoColor=white)

</div>

---

## 📌 About the Project

**SmartClass** is an AI-assisted classroom attendance application built with Python and Streamlit.

The application provides separate **Teacher** and **Student** flows. Teachers can manage subjects and attendance, while students can join subjects through a shared enrollment code.

The application uses **Supabase** as its database and includes libraries for **face recognition, image processing, machine learning, and voice attendance**.

---

## ✨ Key Features

<table>
<tr>
<td width="50%">

### 👨‍🏫 Teacher

- 🔐 Teacher login & registration
- 📚 Subject management
- 🔗 Share subject enrollment codes
- 📷 Upload classroom images
- 🤖 AI face analysis
- ✅ Attendance marking
- 📊 Attendance records
- 🎙️ Voice attendance support

</td>
<td width="50%">

### 👨‍🎓 Student

- 🔐 Student application flow
- 🔗 Join subjects using a `join-code`
- 📝 Automatic enrollment flow
- 👤 Student data stored in Supabase
- 📚 Subject enrollment management

</td>
</tr>
</table>

---

## 🧠 AI & Processing

SmartClass brings together several libraries for AI-assisted attendance:

| Technology | Purpose |
|---|---|
| `dlib` | Computer vision / face processing |
| `face_recognition_models` | Face-recognition model resources |
| `scikit-learn` | Machine learning utilities |
| `Pillow` | Image processing |
| `NumPy` | Numerical operations |
| `Pandas` | Data processing |
| `librosa` | Audio processing |
| `Resemblyzer` | Voice / speaker embedding functionality |

---

## 🛠️ Tech Stack

### Application

- **Python**
- **Streamlit**

### Database

- **Supabase**
- **PostgreSQL** through Supabase

### AI / ML

- **dlib**
- **face recognition models**
- **scikit-learn**
- **NumPy**
- **Pandas**
- **Pillow**

### Voice

- **librosa**
- **Resemblyzer**

### Security / Utilities

- **bcrypt**
- **segno**

The dependency list is maintained in [`requirements.txt`](./requirements.txt).

---

## 🏗️ Project Structure

```text
ai-attendance-project/
│
├── .streamlit/
│   └── secrets.toml          # 🔒 Local secrets — never commit
│
├── src/
│   ├── components/           # Reusable UI components
│   ├── database/             # Supabase/database functions
│   ├── pipelines/            # AI/data-processing pipelines
│   ├── screens/              # Home, teacher & student screens
│   └── ui/                   # UI/layout utilities
│
├── app.py                    # 🚀 Main Streamlit entry point
├── requirements.txt          # Python dependencies
├── package.json              # Node dependency configuration
├── package-lock.json         # Locked Node dependency versions
├── README.md                 # Project documentation
└── .gitignore                # Git exclusions
```

---

## 🔄 Application Flow

```text
                    ┌──────────────────┐
                    │   Streamlit App  │
                    │      app.py      │
                    └────────┬─────────┘
                             │
                ┌────────────┴────────────┐
                │                         │
         ┌──────▼──────┐           ┌──────▼──────┐
         │   Teacher   │           │   Student   │
         │    Flow     │           │    Flow     │
         └──────┬──────┘           └──────┬──────┘
                │                         │
        ┌───────▼────────┐        ┌───────▼────────┐
        │ Subject /      │        │ Join Subject   │
        │ Attendance     │        │ with join-code │
        └───────┬────────┘        └───────┬────────┘
                │                         │
                └───────────┬─────────────┘
                            │
                    ┌───────▼────────┐
                    │    Supabase    │
                    │    Database    │
                    └─────────────────┘
```

---

## 🗄️ Database

The current project uses these Supabase tables:

```text
teachers
students
subjects
subject_students
attendance_logs
```

Make sure the tables and their required permissions are configured in your Supabase project before running the application.

> **Security:** If your application uses a Supabase service-role/secret key, keep it server-side and never expose it in frontend code or GitHub.

---

## 🚀 Getting Started

### 1. Clone the repository

```bash
git clone <YOUR_GITHUB_REPOSITORY_URL>
cd ai-attendance-project
```

### 2. Create a virtual environment

**Windows / PowerShell**

```powershell
python -m venv venv
```

Activate it:

```powershell
venv\Scripts\activate
```

### 3. Install dependencies

```powershell
pip install -r requirements.txt
```

> Some computer-vision dependencies may take additional time to install.

### 4. Configure Supabase

Create this file locally:

```text
.streamlit/secrets.toml
```

Add your Supabase credentials:

```toml
SUPABASE_URL = "https://YOUR_PROJECT.supabase.co"
SUPABASE_KEY = "YOUR_SUPABASE_KEY"
```

⚠️ **Do not commit this file.**

### 5. Run SmartClass

```powershell
streamlit run app.py
```

The application will start locally, normally at:

```text
http://localhost:8501
```

---

## 🔗 Student Enrollment with Join Code

SmartClass supports a join-code flow through the URL.

Example:

```text
http://localhost:8501/?join-code=ABC123
```

The application reads the `join-code` query parameter and switches to the student flow. After the student is logged in, the automatic enrollment dialog can be opened.

---

## 🔐 Security & Git

The following files/folders should **not** be committed:

```text
venv/
.venv/
node_modules/
.streamlit/secrets.toml
.env
.env.*
__pycache__/
*.py[cod]
.vscode/
```

The following project files **should** normally be committed:

```text
src/
app.py
requirements.txt
package.json
package-lock.json
README.md
.gitignore
```

### 🚨 Never expose credentials

Never put these directly in Python source code:

```python
SUPABASE_KEY = "..."
```

Use Streamlit secrets instead:

```python
st.secrets["SUPABASE_KEY"]
```

If a real secret key has already been pushed to GitHub, **rotate/revoke it immediately** and replace it with a new credential.

---

## 🧪 Local Development

A simple development workflow:

```powershell
# Activate environment
venv\Scripts\activate

# Install/update dependencies
pip install -r requirements.txt

# Start application
streamlit run app.py
```

When making changes:

1. Test locally.
2. Check the Streamlit terminal for errors.
3. Verify Supabase permissions.
4. Confirm secrets are not tracked by Git.
5. Commit only the required source/configuration files.

---

## 🛠️ Troubleshooting

### `StreamlitSecretNotFoundError`

Check that:

```text
.streamlit/secrets.toml
```

exists in the project root and contains the required keys.

### `permission denied for table ...`

This is usually a Supabase database permission issue.

Check the permissions for the affected table and the database role being used by your application.

### `ImportError: cannot import name ...`

Make sure:

- The function exists in the referenced Python file.
- The import name exactly matches the function name.
- Streamlit is started from the project root.

Example:

```powershell
streamlit run app.py
```

### Dependencies fail to install

Try upgrading the packaging tools first:

```powershell
python -m pip install --upgrade pip setuptools wheel
```

Then:

```powershell
pip install -r requirements.txt
```

---

## 📦 Node Dependencies

The repository also contains:

```text
package.json
package-lock.json
```

with the Supabase server package configured.

Install Node dependencies with:

```bash
npm install
```

`package-lock.json` should normally be committed so the dependency tree remains reproducible.

---

## 📸 Screenshots

Add screenshots of your application here after the UI is finalized.

Example:

```markdown
![Home Screen](screenshots/home.png)
![Teacher Dashboard](screenshots/teacher-dashboard.png)
![Student Screen](screenshots/student.png)
```

Recommended screenshots:

- 🏠 Home screen
- 👨‍🏫 Teacher dashboard
- 👨‍🎓 Student dashboard
- 📷 Face-recognition attendance
- 📊 Attendance records
- 🔗 Subject enrollment

---

## 🗺️ Future Improvements

Possible future enhancements:

- 📊 Advanced attendance analytics
- 📅 Attendance calendar
- 📈 Student performance dashboards
- 📱 Improved mobile responsiveness
- ☁️ Cloud deployment
- 🔔 Attendance notifications
- 🧑‍💻 Improved authentication and authorization
- 🧪 Automated testing

---

## 🤝 Contributing

Contributions are welcome.

```text
1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Test locally
5. Commit your changes
6. Push the branch
7. Open a Pull Request
```

---

## 📄 License

No license is currently specified for this project.

If you plan to distribute the project publicly, add an appropriate license such as MIT and include a `LICENSE` file.

---

<div align="center">

### ⭐ If you like this project, consider giving it a star!

**Project Summary

SmartClass combines Streamlit, AI-based face analysis, Supabase, and voice-related libraries to create a classroom attendance system. Teachers can manage subjects, process classroom photos for attendance, and review attendance records, while students can join subjects using a shared enrollment code.**

</div>

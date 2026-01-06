## 📁 Project Structure

```
komoot-exporter/
├── app.py                   # Main Flask application
├── pywebview_app.py         # PyWebView wrapper for desktop app
├── komoot_adapter.py        # Adapter for Komoot API integration
├── build_app.py             # Script to build the executable
├── /templates/  
│   └── index.html           # Main UI template
├── /static/                 # Static assets (optional)
├── requirements.txt         # Project dependencies
└── venv/                    # Virtual environment (not included in Git)
```

## 🛠 Setup Instructions

### 0. Install Python

#### Linux

##### 1. Install Python
Most Linux distributions come with Python pre-installed. Check with:

```
python3 --version
```

If not installed, install it using your package manager:

**Ubuntu/Debian:**
```
sudo apt update
sudo apt install python3 python3-pip python3-venv
```

##### 2. Install required system dependencies
For PyWebView to work properly on Linux, you'll need GTK and WebKit:

**Ubuntu/Debian:**
```
sudo apt install libgtk-3-0 libwebkit2gtk-4.0-37
```

### 1. Create and activate virtual environment

#### macOS/Linux

```
python3 -m venv venv  
source venv/bin/activate
```

---

### 2. Install dependencies

```
pip install -r requirements.txt
```

If you don't have requirements.txt yet, create it with:

```
pip install flask pywebview requests beautifulsoup4 gpxpy komootgpx
pip freeze > requirements.txt
```

---

## 🚀 Running in Development

Make sure the virtual environment is activated.

```
python pywebview_app.py
```

To run just the Flask server without the desktop window:

```
python app.py
```

Then open in your browser:

```
http://localhost:5001/
```

---


---

## ⚠ Common Errors

| Problem | Solution |
|---------|----------|
| "python not found" | Install Python from https://www.python.org/ (version 3.6+) and ensure it's in your system PATH |
| "DLL load failed" on Windows | Install Visual C++ Redistributable from Microsoft's website |
| Templates not found in executable | Use the correct `--add-data` format for your OS |
| "No module named 'xyz'" | Make sure all dependencies are properly installed, or add them to `--hidden-import` |
| Internal Server Error | Check the log file for detailed error information |
| PyWebView not working on Linux | Install required GTK and WebKit dependencies (`libgtk-3-0`, `libwebkit2gtk-4.1` on Ubuntu/Debian) |

---
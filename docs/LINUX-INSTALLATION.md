# 🐧 Linux Installation Guide for komoot-takeout

This guide will help you install and run komoot-takeout on Linux.

## 📋 System Requirements

- **Ubuntu 22.04 LTS or later** (recommended)
- **Debian 11 or later** (should work)
- **Other Linux distributions** (may require adjusting package names)
- **Python 3.8 or later**
- **GTK 3.0** and **WebKit2GTK 4.1**

## 🛠 Installation

### 1. Install System Dependencies

Open a terminal and run:

```bash
sudo apt update
sudo apt install python3 python3-pip python3-venv python3-gi python3-gi-cairo gir1.2-gtk-3.0 gir1.2-webkit2-4.1
```

### 2. Download komoot-takeout

```bash
# Clone the repository
git clone https://github.com/drohhyn/komoot-takeout.git
cd komoot-takeout
```

### 3. Build from Source (Optional)

If you want to build the application from source instead of using the pre-built launcher:

```bash
# Create and activate virtual environment
python3 -m venv venv
source venv/bin/activate

# Install Python dependencies
pip install -r requirements.txt

# Create symlink for GTK dependencies (required for PyWebView)
sudo ln -s /usr/lib/python3/dist-packages/gi venv/lib/python3.12/site-packages/gi

# Test the application
python pywebview_app.py

# When done, deactivate the virtual environment
deactivate
```

### 4. Run the Application

```bash
# Make the launcher executable
chmod +x komoot-takeout-linux

# Run the application
./komoot-takeout-linux
```

The first time you run it, the script will:
1. Create a virtual environment
2. Install all Python dependencies
3. Set up the necessary symlinks
4. Launch the application

## 🚀 Running the Application

After the initial setup, you can simply run:

```bash
# Using the pre-built launcher (recommended)
./komoot-takeout-linux

# Or if you built from source
source venv/bin/activate
python pywebview_app.py
```

## 📁 Application Data

- **Configuration**: Stored in `~/.config/komoot-takeout/`
- **Downloads**: Default location is `~/komoot-takeout/`. This can currently not be changed.

## ⚠️ Troubleshooting

### "GTK dependencies not available"
If you see this error, make sure you have installed the required system packages:

```bash
sudo apt install python3-gi python3-gi-cairo gir1.2-gtk-3.0 gir1.2-webkit2-4.1
```

### "Python 3 not found"
Make sure Python 3 is installed:

```bash
sudo apt install python3 python3-pip python3-venv
```

### "Virtual environment setup failed"
Try creating the virtual environment manually:

```bash
python3 -m venv venv
source venv/bin/activate
pip install -r requirements.txt
```

### "Build script failed"
If `build_app.py` fails, try:

```bash
# Install additional build dependencies
pip install pyinstaller

# Try building with verbose output
python build_app.py 2>&1 | tee build.log

# Check the log for specific errors
cat build.log
```

If you encounter GTK-related build errors, consider using the launcher script instead as it's more reliable for Linux.

## 🔄 Updating

To update to the latest version:

```bash
cd komoot-takeout
git pull origin main
# The application will update dependencies automatically on next run
```

## 📝 Notes

- The Linux version uses GTK 3 for the graphical interface
- WebKit2GTK 4.1 is used for rendering the web content
- The application creates a virtual environment to isolate dependencies
- System GTK libraries are used instead of bundling them

## 📜 License

This software is licensed under the GNU General Public License v3.0. See the [LICENSE](LICENSE) file for details.
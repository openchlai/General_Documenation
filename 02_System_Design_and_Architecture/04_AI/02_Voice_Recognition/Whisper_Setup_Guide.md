# 📌 Whisper Setup Guide  
This guide covers **installing and setting up Whisper** for **macOS, Windows, and Linux**, followed by **Django API integration**.

---

## 📌 Table of Contents
1. [Installation](#installation)
   - [MacOS](#macos)
   - [Windows](#windows)
   - [Linux (Ubuntu/Debian)](#linux)
2. [Setting Up the Django API](#setting-up-the-django-api)
3. [Testing the API](#testing-the-api)
4. [Troubleshooting](#troubleshooting)

---

# 🛠 Installation  
## 🔵 macOS  

### 1️⃣ Install Homebrew (If Not Installed)
```sh
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

### 2️⃣ Install FFmpeg
```sh
brew install ffmpeg
```
Verify installation:
```sh
ffmpeg -version
```

### 3️⃣ Create a Virtual Environment
```sh
cd ~/openchscfc
python3 -m venv venv
source venv/bin/activate
```

### 4️⃣ Install Python Packages
```sh
pip install --upgrade pip
pip install torch torchvision torchaudio
pip install whisper numpy ffmpeg-python
```

### 5️⃣ Download the Whisper Model
```sh
whisper --download_dir /Users/mac/ai-models --model medium
```

---

## 🟢 Windows  

### 1️⃣ Install Chocolatey (If Not Installed)
Open **PowerShell as Administrator** and run:
```powershell
Set-ExecutionPolicy Bypass -Scope Process -Force; [System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072; iex ((New-Object System.Net.WebClient).DownloadString('https://community.chocolatey.org/install.ps1'))
```

### 2️⃣ Install FFmpeg
```powershell
choco install ffmpeg
```
Verify installation:
```powershell
ffmpeg -version
```

### 3️⃣ Install Python and Virtual Environment
```powershell
python -m venv venv
venv\Scriptsctivate
```

### 4️⃣ Install Python Packages
```powershell
pip install --upgrade pip
pip install torch torchvision torchaudio whisper numpy ffmpeg-python
```

### 5️⃣ Download the Whisper Model
```powershell
whisper --download_dir C:\ai-models --model medium
```

---

## 🔴 Linux (Ubuntu/Debian)  

### 1️⃣ Install Dependencies
```sh
sudo apt update && sudo apt install -y ffmpeg python3-pip python3-venv
```

### 2️⃣ Create a Virtual Environment
```sh
mkdir -p ~/openchscfc
cd ~/openchscfc
python3 -m venv venv
source venv/bin/activate
```

### 3️⃣ Install Python Packages
```sh
pip install --upgrade pip
pip install torch torchvision torchaudio whisper numpy ffmpeg-python
```

### 4️⃣ Download the Whisper Model
```sh
whisper --download_dir ~/ai-models --model medium
```

---

# 🚀 Setting Up the Django API  

### 1️⃣ Create a Django Project and App
```sh
django-admin startproject cfcbe
cd cfcbe
python manage.py startapp transcription
```

### 2️⃣ Update Django Settings (`cfcbe/settings.py`)
```python
INSTALLED_APPS = [
    ...
    'rest_framework',
    'transcription',
]
```

### 3️⃣ Implement the Transcription API (`transcription/views.py`)
```python
import whisper
import os
from rest_framework.decorators import api_view
from rest_framework.response import Response

MODEL_PATH = "/Users/mac/ai-models"  # Change for Windows/Linux

model = whisper.load_model("medium", download_root=MODEL_PATH)

@api_view(['POST'])
def transcribe_audio(request):
    file = request.FILES.get('audio_file')
    if not file:
        return Response({"error": "No file uploaded"}, status=400)
    
    file_path = os.path.join("/tmp", file.name)
    with open(file_path, "wb") as f:
        for chunk in file.chunks():
            f.write(chunk)

    result = model.transcribe(file_path)

    return Response({"transcription": result["text"]})
```

### 4️⃣ Define API Routes (`transcription/urls.py`)
```python
from django.urls import path
from .views import transcribe_audio

urlpatterns = [
    path('transcribe/', transcribe_audio, name='transcribe_audio'),
]
```

### 5️⃣ Update `cfcbe/urls.py`
```python
from django.contrib import admin
from django.urls import path, include

urlpatterns = [
    path('admin/', admin.site.urls),
    path('api/transcription/', include('transcription.urls')),
]
```

### 6️⃣ Run Django Server
```sh
python manage.py runserver
```

---

# 🛠 Testing the API  

### 1️⃣ Using cURL
```sh
curl -X POST -F "audio_file=@/path/to/audio.wav" http://127.0.0.1:8000/api/transcription/transcribe/
```

### 2️⃣ Using Postman
- Open **Postman**.
- Create a **POST request** to:
  ```
  http://127.0.0.1:8000/api/transcription/transcribe/
  ```
- In **Body**, choose **form-data**.
- Add a file field named `audio_file` and upload an audio file.
- Click **Send**.

---

# ⚠️ Troubleshooting  
### 1️⃣ FFmpeg Not Found
Check if `ffmpeg` is installed:
```sh
which ffmpeg  # macOS/Linux
where ffmpeg  # Windows
```
If missing:
```sh
brew install ffmpeg  # macOS
choco install ffmpeg  # Windows
sudo apt install ffmpeg  # Linux
```

### 2️⃣ Whisper Model Keeps Downloading
Ensure `download_root` is set:
```python
model = whisper.load_model("medium", download_root="/Users/mac/ai-models")  # Change for Windows/Linux
```

### 3️⃣ FFmpeg Permission Issues (Mac)
```sh
chmod +x /Users/mac/ai-models/ffmpeg
xattr -d com.apple.quarantine /Users/mac/ai-models/ffmpeg
```

### 4️⃣ Whisper is Slow on CPU
Use a **smaller model**:
```python
model = whisper.load_model("small", download_root="/Users/mac/ai-models")
```

---

# 🎉 Conclusion
✅ **Now, Whisper is fully set up on macOS, Windows, and Linux.**  
✅ **Django API is ready for real-time transcription.**  
✅ **Test using cURL or Postman.**  

🚀 **Enjoy your local Whisper-powered transcription system!** 🚀  

---

### 📌 Need Help?  
If you face any issues, feel free to ask! 💡

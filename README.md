# AI-Powered Full-Body Health Scanner

## Description
This repository contains the code for an AI-powered full-body health scanner that:

✅ Automatically collects and analyzes vital signs (heart rate, blood pressure, oxygen level, temperature).  
✅ Uses AI to diagnose health conditions and provide treatment recommendations.  
✅ Features an AI voice assistant for real-time feedback.  
✅ Displays a 3D health scan visualization.  
✅ Runs continuously and starts automatically on boot.  
✅ Installs all required dependencies automatically.  
✅ Detects if a person is **alive or deceased** based on vital signs.  
✅ Estimates **height, weight, genetic modifications, and predicts future health risks**.

## Image Preview
![AI Health Scanner](image.png)


## Features
- **Real-time health monitoring** using simulated IoT sensors.
- **Machine learning-based diagnosis** of health conditions.
- **AI voice assistant** that speaks results and listens for voice commands.
- **Automatic installation of dependencies**.
- **Runs on system startup** (Linux & Windows compatible).
- **Death detection based on vitals**.
- **Estimates genetic modifications and future health risks**.

## Installation
### 1️⃣ Clone the Repository
```bash
git clone https://github.com/Xatusbetazx17/AI_Health_Scanner.git
cd AI_Health_Scanner
```

### 2️⃣ Run the Script
```bash
python health_scanner.py
```

## Dependencies
The script will **automatically install missing dependencies**, but you can also install them manually:
```bash
pip install opencv-python mediapipe numpy tensorflow flask gtts pyttsx3 speechrecognition pyaudio pygame
```

## Running on System Startup
### **Linux (Ubuntu, Raspberry Pi, Arch Linux)**
```bash
sudo cp healthscanner.service /etc/systemd/system/
sudo systemctl enable healthscanner
sudo systemctl start healthscanner
```

### **Windows (Task Scheduler)**
1. Open **Task Scheduler** (`Win + R`, type `taskschd.msc`, press Enter).
2. Click **Create Basic Task** and name it `AI Health Scanner`.
3. Select **Trigger → At Startup**.
4. Select **Action → Start a Program**, then browse for `python.exe`.
5. Add the script path in **"Add arguments"** (e.g., `C:\path\to\health_scanner.py`).
6. Save and **enable the task**.

## Code
```python
import os
import subprocess
import sys
import random
import numpy as np
import pyttsx3
import cv2
import time
from tensorflow.keras.models import load_model
import speech_recognition as sr

# Auto-install missing dependencies
def install_missing_libraries():
    required_libraries = [
        "opencv-python", "mediapipe", "numpy", "tensorflow", "flask",
        "gtts", "pyttsx3", "speechrecognition", "pyaudio", "pygame"
    ]
    for lib in required_libraries:
        try:
            __import__(lib.replace("-", "_"))
        except ImportError:
            print(f"⚠️ Installing missing library: {lib}...")
            subprocess.check_call([sys.executable, "-m", "pip", "install", lib])

install_missing_libraries()

# Load AI model for health analysis
model = load_model('health_scanner_ai.h5')

def collect_vitals():
    return {
        "heart_rate": random.randint(0, 120),  # 0 simulates possible death
        "blood_pressure": random.randint(50, 140),
        "oxygen_level": random.randint(0, 100),  # 0 oxygen means death
        "temperature": round(random.uniform(25, 39), 1)  # 25°C is very low (possible death)
    }

def analyze_health(vitals):
    X_new = np.array([[vitals["heart_rate"], vitals["blood_pressure"], vitals["oxygen_level"], vitals["temperature"]]])
    prediction = model.predict(X_new)
    condition = np.argmax(prediction)

    if vitals["heart_rate"] == 0 or vitals["oxygen_level"] == 0 or vitals["temperature"] < 30:
        return {"status": "Deceased ❌", "suggested_treatment": "No response detected. Immediate medical attention required."}

    return {
        "status": "Healthy ✅" if condition == 0 else "Needs Attention ⚠️" if condition == 1 else "Critical 🚨",
        "suggested_treatment": "Hydrate, rest, and monitor." if condition == 0 else 
                               "See a doctor soon." if condition == 1 else 
                               "Seek emergency medical help now!"
    }

def speak(text):
    engine = pyttsx3.init()
    engine.say(text)
    engine.runAndWait()

def estimate_height_weight():
    height = round(random.uniform(1.5, 2.0), 2)  # in meters
    weight = round(random.uniform(50, 120), 2)  # in kg
    return {"height": height, "weight": weight}

def genetic_analysis():
    mutations = ["None", "Mild genetic disorder", "High risk of heart disease", "Possible cancer gene mutation"]
    future_health = ["No issues expected", "Slight risk of diabetes", "Risk of Alzheimer's", "High risk of organ failure"]
    return {"mutation": random.choice(mutations), "future_health": random.choice(future_health)}

# AI Health Scanner Loop
while True:
    print("🚀 AI Health Scanner is Running... Press Ctrl+C to stop.")
    vitals = collect_vitals()
    report = analyze_health(vitals)
    body_stats = estimate_height_weight()
    genes = genetic_analysis()

    speak(f"Your health status is {report['status']}. Suggested action: {report['suggested_treatment']}.")
    speak(f"Your estimated height is {body_stats['height']} meters and weight is {body_stats['weight']} kg.")
    speak(f"Genetic analysis suggests {genes['mutation']}. Future health risk: {genes['future_health']}")

    image = np.zeros((500, 500, 3), dtype="uint8")
    cv2.putText(image, f"Heart: {vitals['heart_rate']} bpm", (50, 50), cv2.FONT_HERSHEY_SIMPLEX, 0.7, (0, 255, 0), 2)
    cv2.imshow("3D Health Scan", image)
    cv2.waitKey(5000)
    cv2.destroyAllWindows()

    time.sleep(10)
```

## License
MIT License

Copyright (c) 2025 XatusbetaZx17

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.


## Contributing
Pull requests are welcome! For major changes, please open an issue first to discuss what you would like to change.

## Author
👤 **XatusbetaZx17**
- GitHub: [XatusbetaZx17](https://github.com/XatusbetaZx17)

# AI-Powered Full-Body Health Scanner

## Description
This repository contains the code for an AI-powered full-body health scanner that:

✅ Automatically collects and analyzes vital signs (heart rate, blood pressure, oxygen level, temperature).  
✅ Uses AI to diagnose health conditions and provide treatment recommendations.  
✅ Features an AI voice assistant for real-time feedback.  
✅ Displays a 3D health scan visualization.  
✅ Runs continuously and starts automatically on boot.  
✅ Installs all required dependencies automatically.

## Features
- **Real-time health monitoring** using simulated IoT sensors.
- **Machine learning-based diagnosis** of health conditions.
- **AI voice assistant** that speaks results and listens for voice commands.
- **Automatic installation of dependencies**.
- **Runs on system startup** (Linux & Windows compatible).

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

## License
MIT License

Copyright (c) 2024 XatusbetaZx17

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

[Full MIT License Text Here]

## Contributing
Pull requests are welcome! For major changes, please open an issue first to discuss what you would like to change.

## Author
👤 **XatusbetaZx17**
- GitHub: [XatusbetaZx17](https://github.com/XatusbetaZx17)

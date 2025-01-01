
# Remote-Keylogger

### Project Goal
The purpose of this project is to create a remote keylogger in Python that goes beyond simple keystroke capture. My goal is to build a tool that can gather system information, stealthily send it via email, and package it in a way that blends into the user environment. 

---

### Code Overview

#### Imports
The project begins with key Python library imports. Each library serves a distinct purpose:
- **`tkinter`**: Creates a small popup window at the end of the program, acting as a subtle notification when the program stops.
- **`pynput.keyboard`**: Handles keystroke logging by capturing all user input.
- **`logging`**: Writes logs to a hidden file on the system.
- **`os`** and **`subprocess`**: Interact with the host operating system to gather file directories, running processes, and Wi-Fi profiles.
- **`smtplib`**: Handles email delivery to send the captured logs and system info to a remote email address.
- **`threading`**: Runs multiple tasks like keylogging, data collection, and email sending simultaneously in separate threads.
- **`socket`, `getpass`, and `uuid`**: Retrieve host information such as LAN IP, hostname, username, and MAC address.
![Imports](C:\Users\karim\OneDrive\Desktop\cybersec-projects\remote-keylogger\images\imports.png)

![Imports code](C:\Users\karim\OneDrive\Desktop\cybersec-projects\remote-keylogger\images\imports.png)
---

### Setup
This part of the code handles the configuration of SMTP email services and logging. The program writes all captured information to a file disguised as `license_win64_details.txt`, blending in with standard Windows files. By using Gmail's SMTP service, the program can securely send all logs and system data to the designated email address.

#### Image Placeholder:  
*Include a screenshot of the "license_win64_details.txt" logging setup section.*

---

### Host Information and Wi-Fi Profiles
Before the keylogger starts, the program collects important system details:
- **Host Information**: Captures hostname, LAN IP, SSID, MAC address, and system username.
- **Wi-Fi Profiles**: Extracts saved Wi-Fi networks and their passwords from the system.

This ensures a complete snapshot of the machine’s environment is emailed at the start of the program.

#### Image Placeholder:  
*Include a screenshot showing the functions collecting host information and Wi-Fi profiles.*

---

### Advanced Features
I also included advanced functionality to give a complete picture of system activity:
- **Active Network Connections**: Logs all open TCP and UDP connections using `netstat`.
- **Running Processes**: Retrieves the list of currently running processes on the system using `tasklist`.
- **Recently Accessed Files**: Collects file names from the Windows "Recent" folder.


---

### Main Loop
At the core of the program is its main loop. Here’s how it works:
1. **Keylogging**: Captures all user input and writes it to the hidden log file.
2. **Emailing Logs**: Sends an email whenever the log file reaches 500 bytes.
3. **Safety Mechanism**: The program stops running and displays a popup if the user presses the right `Ctrl` key.


#### Image Placeholder:  
*Include a screenshot of the main loop code.*

---

### Compilation to Executable
To make the program stealthier, it can be compiled into a standalone `.exe` file using **PyInstaller**. When saved with a `.pyw` extension, the program runs in a “no-console” mode, leaving no visible trace of its activity.

Command:
```
pyinstaller --onefile --noconsole main.py
```

The compiled file is placed in the `dist` directory.

#### Image Placeholder:  
*Include a screenshot showing the compiled executable in the `dist` folder.*

---

### Advanced Packaging with WinRAR
To further disguise the executable, it can be packaged into an SFX archive using WinRAR:
1. **Combine Files**: Add the executable and an image file into an archive.
2. **Set Run Parameters**: Configure the archive to run the `.exe` file after extraction.
3. **Assign Icon**: Use the image file as the archive icon to blend in further.

This technique ensures the program appears as an innocuous image file but runs the keylogger upon opening.

#### Image Placeholder:  
*Include screenshots of the WinRAR SFX configuration.*

---

### Example Output
Below are examples of the emails sent by the program:

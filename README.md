
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

  ![imports](https://github.com/user-attachments/assets/40f4da0c-8ccb-4f50-b784-743ada8f0b98)

---

### Setup
This part of the code handles the configuration of SMTP email services and logging. The program writes all captured information to a file disguised as `license_win64_details.txt`, blending in with standard Windows files. By using Gmail's SMTP service, the program can securely send all logs and system data to the designated email address.


![setup](https://github.com/user-attachments/assets/0e47d844-958a-4d1a-bee4-8d62c67329a4)

---

### Host Information and Wi-Fi Profiles
Before the keylogger starts, the program collects important system details:
- **Host Information**: Captures hostname, LAN IP, SSID, MAC address, and system username.
- **Wi-Fi Profiles**: Extracts saved Wi-Fi networks and their passwords from the system.

![host_info_and_wifi_profiles](https://github.com/user-attachments/assets/654d0fc8-59f0-4f56-a33c-312a8bc2c0d0)


---

### Advanced Features
I also included advanced functionality to give a complete picture of system activity:
- **Active Network Connections**: Logs all open TCP and UDP connections using `netstat`.
- **Running Processes**: Retrieves the list of currently running processes on the system using `tasklist`.
- **Recently Accessed Files**: Collects file names from the Windows "Recent" folder.

![advanced features](https://github.com/user-attachments/assets/a9bc61b5-ca7e-4291-b75d-0b2b83d4ca64)

---

### Main Loop
At the core of the program is its main loop. Here’s how it works:
1. **Keylogging**: Captures all user input and writes it to the hidden log file.
2. **Emailing Logs**: Sends an email whenever the log file reaches 500 bytes.
3. **Safety Mechanism**: The program stops running and displays a popup if the user presses the right `Ctrl` key.

![logging system info](https://github.com/user-attachments/assets/41d62d70-e634-45e1-b587-87fdbe844557)

![keylogging logic](https://github.com/user-attachments/assets/ccd5c508-6a8c-49dd-92ba-84aafa5ae147)

![main thread loop](https://github.com/user-attachments/assets/7a0dd73d-0a31-4692-b2f4-1e064edcb6fa)

---

### Compilation to Executable
To make the program stealthier, it can be compiled into a standalone `.exe` file using **PyInstaller**. When saved with a `.pyw` extension, the program runs in a “no-console” mode, leaving no visible trace of its activity.

Command:
```
pyinstaller --onefile --noconsole main.py
```

The compiled file is placed in the `dist` directory.


### Advanced Packaging with WinRAR
To further disguise the executable, it can be packaged into an SFX archive using WinRAR:
1. **Combine Files**: Add the executable and an image file into an archive.
2. **Set Run Parameters**: Configure the archive to run the `.exe` file after extraction.
3. **Assign Icon**: Use the image file as the archive icon to blend in further.

This technique ensures the program appears as an innocuous image file but runs the keylogger upon opening.

![pyinstaller](https://github.com/user-attachments/assets/bf493e65-99c8-419c-ab05-6346da152fc1)

![pyinstaller completed](https://github.com/user-attachments/assets/36fed72b-d568-40c8-9de2-0d6dfe50e502)

![archiving 1](https://github.com/user-attachments/assets/5b4327d0-e445-4bd9-a822-c0a42f869748)

![archiving 2](https://github.com/user-attachments/assets/5793c27a-ed46-40ef-984e-9a4ac04a2c08)

![archiving 3](https://github.com/user-attachments/assets/67324316-3fe3-4a3f-bed0-f39b265678ad)

![archiving 4](https://github.com/user-attachments/assets/2606fb49-30aa-4dc9-bf0e-1113634c8485)


### Demo
Below is a demo of the output and the process:

![demo 1](https://github.com/user-attachments/assets/837e2ad7-dd56-47b5-8824-4244579b55c3)

![demo2](https://github.com/user-attachments/assets/93c76100-0415-4c9c-b49e-64b93ede0097)

![demo3incomp](https://github.com/user-attachments/assets/a02dbd7f-29fa-440d-befe-f8e474985161)

![demo4incomp](https://github.com/user-attachments/assets/ac35e3b9-e5e2-427d-8791-d0676dcbdcf0)

![demo5incomp](https://github.com/user-attachments/assets/b16dc2b4-ee27-49c7-b313-e5d6ed572378)

![demo6](https://github.com/user-attachments/assets/bd4859aa-7978-47d9-8c73-10cdcc58ffe3)

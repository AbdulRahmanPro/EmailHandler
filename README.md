
# EmailHandler Script Documentation

## Overview
The `EmailHandler` script is a Python-based tool designed to automate email operations, especially useful for creating temporary email addresses and handling email verification processes. It uses the Mail.tm API to create email accounts, log in, and retrieve messages.

## Features
- **Email Account Creation**: Automatically generates a random email address.
- **Secure Password Generation**: Creates a secure password for the email account.
- **Email Login**: Logs into the created email account and retrieves a token for authorization.
- **Message Retrieval**: Fetches messages from the email account, focusing on extracting verification codes from email subjects.
- **Continuous Verification Check**: Periodically checks for new messages to find a verification code.

## Requirements
- Python 3.x
- `requests` library

## Installation
Before running the script, ensure you have Python 3.x installed. You also need to install the `requests` library, which can be done via pip:

```bash
pip install requests
```

## Usage
1. **Initialization**: Create an instance of the `EmailHandler` class.
    ```python
    bot = EmailHandler()
    ```

2. **Start Verification Check**: Call the `start_verification_check` method to begin the email monitoring process.
    ```python
    bot.start_verification_check()
    ```

## How It Works
1. **Initialization**: When an instance of `EmailHandler` is created, it automatically generates a secure password and a random email address using the Mail.tm API.

2. **Email Operations**:
    - `create_email`: Registers a new email account with the generated address and password.
    - `login`: Logs into the email account and stores the authentication token.

3. **Message Handling**:
    - `get_messages`: Retrieves all messages from the email inbox, extracting subjects and numbers.
    - `get_verification_code`: Extracts a verification code from the subject of the emails.

4. **Verification Code Check**:
    - `check_verification_code`: Continuously checks for new messages every 10 seconds, looking for a verification code.
    - `start_verification_check`: Initiates the verification code checking process in a separate thread.

## Limitations
- The script currently has minimal error handling for API interactions.
- The email service is hardcoded to use Mail.tm, which might limit flexibility.



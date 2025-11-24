# Banking System - Python Project

**Project Title:** Simple Banking Program with PIN Authentication  
**Student Name:** Piyush Deep  
**Registration Number:** 25BAI11280  
**Institution:** Vellore Institute of Technology (VIT) Bhopal  
**Course:** CSE Project  
**Professor:** Shahana Gajala Qureshi  
**Date:** 23 November 2025

---

## 📋 Table of Contents

1. [Project Overview](#project-overview)
2. [Features](#features)
3. [Requirements](#requirements)
4. [Installation & Setup](#installation--setup)
5. [Usage Guide](#usage-guide)
6. [Program Structure](#program-structure)
7. [Pseudocode](#pseudocode)
8. [Flowchart](#flowchart)
9. [Code Explanation](#code-explanation)
10. [Screenshots](#screenshots)
11. [Testing & Validation](#testing--validation)
12. [Future Enhancements](#future-enhancements)
13. [Conclusion](#conclusion)

---

##  Project Overview

This project implements a **Simple Banking System** with PIN authentication in Python. It simulates basic banking operations including balance checking, deposits, withdrawals, and secure access through a PIN verification system. The program is designed as an introductory project to demonstrate fundamental programming concepts including functions, conditionals, loops, and user input/output handling.

### Objective

To create a functional banking application that:
- Provides secure PIN-based authentication
- Manages user balance and transactions
- Implements error handling for invalid inputs
- Maintains code simplicity and readability

---

##  Features

### Core Banking Functions
- ** PIN Authentication:** Secure login with 3-attempt limit
- ** Show Balance:** Display current account balance in formatted currency
- ** Deposit:** Add funds to the account with validation
- ** Withdraw:** Remove funds from the account with sufficient fund checks
- ** Logout:** Securely exit the banking session

### Security Features
- PIN verification before accessing any banking functions
- Account locking mechanism after 3 failed PIN attempts
- Input validation to prevent negative amounts
- Prevention of withdrawals exceeding account balance

### User Experience
- Clean menu-driven interface with clear options
- Formatted output with visual separators using asterisks
- Informative error messages for invalid operations
- Continuous session until user chooses to exit

---

##  Requirements

**Software Requirements:**
- Python 3.7 or higher
- Any text editor or IDE (VS Code, PyCharm, Sublime Text, etc.)
- Terminal/Command Prompt

**Hardware Requirements:**
- Minimum 2GB RAM
- 50MB disk space

**Dependencies:**
- No external libraries required (uses only Python built-in functions)

---

##  Installation & Setup

### Step 1: Verify Python Installation
```bash
python --version
```

### Step 2: Create Project Folder
```bash
mkdir BankingSystem
cd BankingSystem
```

### Step 3: Create the Python File
Create a file named `banking_system.py` and copy the code from the provided source.

### Step 4: Run the Program
```bash
python banking_system.py
```

---

##  Usage Guide

### Initial Access
1. Run the program using `python banking_system.py`
2. Enter the PIN when prompted (default: **1234**)
3. You have **3 attempts** to enter the correct PIN

### Main Menu Options
```
1. Show Balance   - Display your current account balance
2. Deposit        - Add money to your account
3. Withdraw       - Remove money from your account
4. Exit           - Quit the banking system
```

### Example Workflow
```
1. Start program
2. Enter PIN: 1234
3. Access granted - Main menu appears
4. Select option 2 (Deposit)
5. Enter amount: 500
6. Select option 1 (Show Balance)
7. New balance displayed
8. Select option 4 (Exit)
```

---

##  Program Structure

```
banking_system.py
│
├── verify_pin()              # PIN authentication function
│   ├── Prompt for PIN
│   ├── Validate against correct PIN
│   ├── Count failed attempts
│   └── Lock account if attempts exceed 3
│
├── show_balance(balance)     # Display balance function
│   └── Format and print current balance
│
├── deposit()                 # Deposit function
│   ├── Accept amount from user
│   ├── Validate amount > 0
│   └── Return amount or 0
│
├── withdraw(balance)         # Withdraw function
│   ├── Accept amount from user
│   ├── Validate amount > 0
│   ├── Check sufficient balance
│   └── Return amount or 0
│
└── main()                    # Main program flow
    ├── Call verify_pin()
    ├── Initialize balance = 0
    ├── Loop through menu until exit
    │   ├── Option 1: Call show_balance()
    │   ├── Option 2: Call deposit() and update balance
    │   ├── Option 3: Call withdraw() and update balance
    │   ├── Option 4: Exit program
    │   └── Invalid input handling
    └── Display exit message
```

---

##  Pseudocode

### verify_pin() Function
```
FUNCTION verify_pin()
    SET correct_pin = "1234"
    SET attempts = 3
    
    PRINT "PIN REQUIRED"
    
    WHILE attempts > 0 DO
        INPUT entered_pin
        
        IF entered_pin == correct_pin THEN
            PRINT "PIN Correct! Access Granted"
            RETURN True
        ELSE
            DECREMENT attempts
            
            IF attempts > 0 THEN
                PRINT "Wrong PIN! " + attempts + " attempt(s) left"
            ELSE
                PRINT "Too many failed attempts! Account Locked!"
                RETURN False
            END IF
        END IF
    END WHILE
END FUNCTION
```

### show_balance(balance) Function
```
FUNCTION show_balance(balance)
    PRINT "*"
    PRINT "Your balance is $" + balance
    PRINT "*"
END FUNCTION
```

### deposit() Function
```
FUNCTION deposit()
    PRINT "*"
    INPUT amount
    PRINT "*"
    
    IF amount < 0 THEN
        PRINT "That's not a valid amount"
        RETURN 0
    ELSE
        RETURN amount
    END IF
END FUNCTION
```

### withdraw(balance) Function
```
FUNCTION withdraw(balance)
    PRINT "*"
    INPUT amount
    PRINT "*"
    
    IF amount > balance THEN
        PRINT "Insufficient funds"
        RETURN 0
    ELSE IF amount < 0 THEN
        PRINT "Amount must be greater than 0"
        RETURN 0
    ELSE
        RETURN amount
    END IF
END FUNCTION
```

### main() Function
```
FUNCTION main()
    SET balance = 0
    SET is_running = True
    
    CALL verify_pin()
    IF verify_pin() returns False THEN
        PRINT "Access Denied. Exiting..."
        RETURN
    END IF
    
    WHILE is_running == True DO
        PRINT "Banking Program Menu"
        PRINT "1. Show Balance"
        PRINT "2. Deposit"
        PRINT "3. Withdraw"
        PRINT "4. Exit"
        
        INPUT choice
        
        IF choice == '1' THEN
            CALL show_balance(balance)
        ELSE IF choice == '2' THEN
            SET deposit_amount = CALL deposit()
            SET balance = balance + deposit_amount
        ELSE IF choice == '3' THEN
            SET withdraw_amount = CALL withdraw(balance)
            SET balance = balance - withdraw_amount
        ELSE IF choice == '4' THEN
            SET is_running = False
        ELSE
            PRINT "That is not a valid choice"
        END IF
    END WHILE
    
    PRINT "Thank you! Have a nice day!"
END FUNCTION
```

---

##  Flowchart

```
                    ┌──────────────────┐
                    │   START PROGRAM  │
                    └────────┬─────────┘
                             │
                    ┌────────▼──────────┐
                    │  VERIFY_PIN()    │
                    │  (3 attempts)    │
                    └────────┬─────────┘
                             │
                    ┌────────▼──────────┐
                    │ PIN Correct?     │
                    └───┬──────────┬────┘
                    NO  │          │ YES
                        │          │
              ┌─────────▼──┐       │
              │ Access     │       │
              │ Denied     │       │
              │ Exit       │       │
              └────────────┘   ┌───▼────────────────┐
                               │ Initialize Balance│
                               │ balance = 0       │
                               └────────┬──────────┘
                                        │
                        ┌───────────────▼──────────────────┐
                        │ DISPLAY MENU:                   │
                        │ 1. Show Balance                 │
                        │ 2. Deposit                      │
                        │ 3. Withdraw                     │
                        │ 4. Exit                         │
                        └───┬──────────────┬──────────┬────┘
                        1   │        2     │    3     │ 4
                    ┌───────▼─┐   ┌────────▼──┐   ┌──▼──────┐  ┌──▼────┐
                    │ SHOW    │   │ DEPOSIT   │   │WITHDRAW │  │ EXIT  │
                    │BALANCE  │   │           │   │         │  │       │
                    │         │   ├───────────┤   ├─────────┤  ├───────┤
                    │Print    │   │ Input     │   │ Input   │  │Loop   │
                    │balance  │   │ amount    │   │ amount  │  │ends   │
                    │         │   │ Valid?    │   │ Valid?  │  │       │
                    └───┬─────┘   │ amount>0? │   │amount>0?│  └───┬───┘
                        │         ├─YES──NO──┤   │amount≤  │      │
                        │         │  │      │    │balance? │      │
                        │         └──┼──────┘    └─YES─NO──┘      │
                        │           │           │     │           │
                        │    ┌──────▼─┐  ┌──────▼─┐ ┌─▼────┐     │
                        │    │balance  │  │Invalid │ │balance   │     │
                        │    │+=amount │  │amount  │ │-=amount  │     │
                        │    └──────┬──┘  └──┬─────┘ └─┬────┘     │
                        │           │        │        │          │
                        └───────┬───┴────┬───┴────┬───┴──────┬───┘
                                │       │        │          │
                        ┌───────▼───────▼────────▼──────────▼──┐
                        │  LOOP BACK TO MENU                   │
                        └───────────────────────────────────────┘
                                        │
                        ┌───────────────▼──────────────────┐
                        │  PRINT EXIT MESSAGE              │
                        │  "Thank you! Have a nice day!"   │
                        └───────────────┬──────────────────┘
                                        │
                        ┌───────────────▼──────────────────┐
                        │   END PROGRAM                    │
                        └────────────────────────────────────┘
```

---

##  Code Explanation

### Key Components

#### 1. **verify_pin() Function**
- Implements secure PIN authentication
- Allows 3 attempts before account lockout
- Uses string comparison for PIN validation
- Provides user feedback on remaining attempts

#### 2. **show_balance(balance) Function**
- Displays current balance in formatted currency ($X.XX)
- Uses f-string formatting for precise decimal display
- Bordered output for visual clarity

#### 3. **deposit() Function**
- Accepts user input for deposit amount
- Validates that amount is not negative
- Returns valid amount or 0 for invalid input

#### 4. **withdraw(balance) Function**
- Accepts user input for withdrawal amount
- Validates amount > 0
- Checks if amount doesn't exceed balance
- Returns valid amount or 0 for invalid input

#### 5. **main() Function**
- Entry point of the program
- Initiates PIN verification first
- Implements menu-driven interface
- Updates balance based on user transactions
- Controls program flow with while loop

---

##  Screenshots

Screenshots are added here showing:
- PIN entry screen
- Menu display
- Deposit transaction
- Withdrawal transaction
- Balance display
- Exit message
![22](https://github.com/piyushdeep024/Banking-Managment-System/blob/main/screenshots/Screenshot%202025-11-23%20185822.png)
![233](https://github.com/piyushdeep024/Banking-Managment-System/blob/main/screenshots/Screenshot%202025-11-23%20185851.png)
![233](https://github.com/piyushdeep024/Banking-Managment-System/blob/main/screenshots/Screenshot%202025-11-23%20190018.png)
![233](https://github.com/piyushdeep024/Banking-Managment-System/blob/main/screenshots/Screenshot%202025-11-23%20190140.png)
![233](https://github.com/piyushdeep024/Banking-Managment-System/blob/main/screenshots/Screenshot%202025-11-23%20190311.png)
![233](https://github.com/piyushdeep024/Banking-Managment-System/blob/main/screenshots/Screenshot%202025-11-23%20190338.png)


---

##  Testing & Validation

### Test Case 1: PIN Authentication
```
Input:  PIN = 1234
Output: "PIN Correct! Access Granted"
Status: ✓ PASS
```

### Test Case 2: Wrong PIN - Attempt 1
```
Input:  PIN = 0000
Output: "Wrong PIN! 2 attempt(s) left"
Status: ✓ PASS
```

### Test Case 3: Account Lockout
```
Input:  3 consecutive wrong PINs
Output: "Too many failed attempts! Account Locked!"
Status: ✓ PASS
```

### Test Case 4: Valid Deposit
```
Input:  Deposit 500
Output: Balance = 500
Status: ✓ PASS
```

### Test Case 5: Negative Deposit
```
Input:  Deposit -100
Output: "That's not a valid amount"
Status: ✓ PASS
```

### Test Case 6: Valid Withdrawal
```
Initial: 500
Input:   Withdraw 200
Output:  Balance = 300
Status:  ✓ PASS
```

### Test Case 7: Insufficient Funds
```
Initial: 500
Input:   Withdraw 1000
Output:  "Insufficient funds"
Status:  ✓ PASS
```

### Test Case 8: Invalid Menu Choice
```
Input:  Choice = 5
Output: "That is not a valid choice"
Status: ✓ PASS
```

---

##  Future Enhancements

1. **Persistent Storage**
   - Save transactions to a file
   - Load previous balance on startup

2. **Multiple Accounts**
   - Create dictionary of accounts
   - Account switching functionality

3. **Transaction History**
   - Track all deposits and withdrawals
   - Display transaction logs with timestamps

4. **PIN Change**
   - Allow users to update their PIN
   - Verification of old PIN first

5. **Interest Calculation**
   - Calculate compound interest
   - Different account types

6. **GUI Interface**
   - Tkinter or PyQt implementation
   - Graphical user interface

7. **Database Integration**
   - Use SQLite or MySQL
   - Persistent data storage

8. **Email Notifications**
   - Send transaction alerts
   - Security alerts for failed attempts

---

##  Conclusion

This Banking System project demonstrates fundamental programming concepts in Python including:
- **Functions:** Modular code organization
- **Conditionals:** Decision-making logic
- **Loops:** Repetitive operations
- **Input/Output:** User interaction
- **Data Types:** String and numeric operations
- **Error Handling:** Validation and exception management

The project successfully implements a secure, user-friendly banking application suitable for introductory computer science education. It provides a solid foundation for understanding larger financial systems and can be extended with advanced features as mentioned above.

---

##  References

- Python Official Documentation: https://www.python.org/
- VIT Bhopal CSE Guidelines
- Professor Shahana Gazala Qureshi's Course Material

---

##  Author Information

**Student:** Piyush Deep  
**Registration Number:** 25BAI11280  
**Institution:** Vellore Institute of Technology (VIT) Bhopal  
**Course:** CSE Project  
**Submitted To:** Prof. Shahana Gajala Qureshi  
**Date: 23 November 2025


**Note:** This project has been completed as per academic guidelines and submitted for evaluation.

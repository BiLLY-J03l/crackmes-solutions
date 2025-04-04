# crackme link -> https://crackmes.one/crackme/662fab296b8bd8ddfe33c184

## First, run the program know what it does.
![image](https://github.com/user-attachments/assets/89d7ddcf-712e-464a-addc-be379904f9bb)


## Use Binary Ninja or any other debugger you like.

**STATIC ANALYSIS**:
  - search for any main function.


**DYNAMIC ANALYSIS**:

  - ![image](https://github.com/user-attachments/assets/cebb3112-1f82-4764-8e66-11741b71784b)

  - set a breakpoint at main's entry point
  
  - ![image](https://github.com/user-attachments/assets/5dbb5dd2-e825-42ab-81da-37e1d89e080d)

  - the program moves some string onto the stack, possibly the passwords.
    
    - ![image](https://github.com/user-attachments/assets/8a48db0b-a4c5-45f4-8c20-aa6f8b0da3aa)
    - 
    - ![image](https://github.com/user-attachments/assets/e05b8e5c-9e2d-4e60-983c-04e5c9bd9288)
  
  - a possible solution is trying every possible string we saw, but that's not really smart.

  - we have an if condition leading to either correct or wrong answer, and that's where we start reverse engineering for the password.

  - ![image](https://github.com/user-attachments/assets/f10c0313-2e6c-4128-91cf-92ea1a83ef8b)
    
  - a cmp instruction is usually used to compare for the password.

  

crackme link -> https://crackmes.one/crackme/5ab77f6533c5d40ad448cb5f


## First, run the program know what it does.
  
  - <img width="958" height="299" alt="image" src="https://github.com/user-attachments/assets/d125f566-9b82-4331-874d-a28a20d494b7" />


**STATIC ANALYSIS**:
- Possible Flow:
- 
  - <img width="1905" height="855" alt="image" src="https://github.com/user-attachments/assets/531b91e9-7eab-462f-beb5-dee986d2d500" />
  
- Couldn't figure out what it's doing.

** DYNAMIC ANALYSIS**:

  - <img width="1474" height="541" alt="image" src="https://github.com/user-attachments/assets/40af9ff2-c79e-4e8c-a03d-537ef00d8a83" />
  
  - that same flow works as follows,
    - the block on the right just iterates with no specific purpose
    - the block on the right is where it asks for input
      
  - <img width="521" height="187" alt="image" src="https://github.com/user-attachments/assets/7b4702b5-d289-4616-825a-0f0e9dbbc636" />
  
    - this function call takes the reg name as input.
    - I typed "amer".
    - then it calls strlen(reg_name), and adds the result to itself using "add eax , eax" which will be 8 in this case. (4 chars + 4 chars).
      
  - <img width="527" height="121" alt="image" src="https://github.com/user-attachments/assets/80894890-d4b2-49db-ba41-7807cd2425ca" />

    - the second function call takes the reg code which is a number.
    - I typed 24.
      
  - <img width="316" height="63" alt="image" src="https://github.com/user-attachments/assets/70dba33d-ee65-419b-8e29-3aa6fdf1b45f" />
  
    - it copies a variable value into eax , which is 8
      
    - <img width="120" height="108" alt="image" src="https://github.com/user-attachments/assets/0331d1c5-b6cf-48fa-b2b6-ad77d274b936" />
    - then, adds this value to itself using "add eax , eax" which will be 16 in this case (10 in hex). (8 + 8).
      
    - <img width="120" height="109" alt="image" src="https://github.com/user-attachments/assets/dda4d4f2-11ac-458d-9ffb-0b70008ac3aa" />
    - then, it compares eax to a variable stored in ebp-6C, which is our value 24 (18 in hex).
      
    - <img width="297" height="36" alt="image" src="https://github.com/user-attachments/assets/e2e3e1bd-32d3-42a4-bb20-51edd988be82" />
    - the ZF flag is not set, meaning they're not equal.
      
    - <img width="682" height="316" alt="image" src="https://github.com/user-attachments/assets/4ef32837-b745-4829-8c97-e35c60881163" />
    - jump if not equal, means it will take the jump if the values aren't equal, which, in our case, will happen.
      
    - <img width="795" height="376" alt="image" src="https://github.com/user-attachments/assets/c2354257-f2ac-445a-957a-8455bfb7a5b6" />
    - if we continue to run, it will say it's incorrect and pauses.
      
    - <img width="622" height="229" alt="image" src="https://github.com/user-attachments/assets/a3d50625-65b2-4149-8c6c-8efe65e99619" />
  - **How to solve?**
    - there's no static value to solve the crackme.
    - the answer is in the number of chars in your reg_name input you give.
    - say you supplied "billy" as your reg_name input.
    - 5 characters in this variable, so we add this value to itself, which will be 10.
    - then, we add 10 to itself which will be 20 (14 in hex)
    - so the reg_code have to be 20 not 24 as we typed in the first time.
    - Let's try again.
    - <img width="957" height="253" alt="image" src="https://github.com/user-attachments/assets/81ac0064-ce9a-4ad3-8905-83e61f75170f" />
    - Looking deeper in the debugger to check.
    - <img width="354" height="111" alt="image" src="https://github.com/user-attachments/assets/accb3b85-fd12-41eb-ae9d-11ee0cae7d8c" />
    - the first addition yields in 10, which is A in hex.
    - the second addition yields in 20, which is 14 in hex.
    - <img width="367" height="112" alt="image" src="https://github.com/user-attachments/assets/89731f71-952f-4695-b53b-c429390a3940" />




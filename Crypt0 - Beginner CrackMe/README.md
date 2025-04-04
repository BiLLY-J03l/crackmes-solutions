# crackme link -> https://crackmes.one/crackme/5f907efe33c5d424269a15d1


## First, run the program know what it does.
  
  - ![image](https://github.com/user-attachments/assets/b360f980-4f95-4f5a-b185-8039c6cc1839)
    
## Use IDA or any other debugger you like.

**STATIC ANALYSIS**:

- ![image](https://github.com/user-attachments/assets/b252a527-6229-4239-87e4-114a0e51c2d7)
- ![image](https://github.com/user-attachments/assets/8c6c2686-ac31-47f1-9638-b89fddcd7691)

- here is where it outputs the error about user registeration
  - ![image](https://github.com/user-attachments/assets/a2187710-e2a8-42e6-b607-890114810ff7)

- we trace back into the condition where it's executed
  - ![image](https://github.com/user-attachments/assets/3ef53bdc-d6ee-4e93-aa4b-930a863c7b4f)


----------------------------------------------------------------------------------------------------------------------------------

**DYNAMIC ANALYSIS**:
  
- I set a breakpoint at .text:008B9560 lea     eax, [ebp+var_30]
  
- .text:008B9560 lea     eax, [ebp+var_30]
- .text:008B9563 push    eax
- .text:008B9564 lea     ecx, [ebp+var_78]
- .text:008B9567 push    ecx

  - after furthur analysis of the above instructions, it moves some variables to some registers and pushing them into the stack.

  - the [ebp+var_30] holds "Nick" value (to be compared) 

  - the [ebp+var_78] holds "billy" value (input)

    - ![image](https://github.com/user-attachments/assets/d6ab8e4a-937d-4bcc-97cc-b648b59fccd9)
     
    - ![image](https://github.com/user-attachments/assets/bbfc6d2c-35a1-490f-839a-62a88d7a930b)

- ![image](https://github.com/user-attachments/assets/118dac6a-df27-4199-afa2-0b5615ed82c3)

- Following to the password output, we get this function block
  - ![image](https://github.com/user-attachments/assets/b9573f8f-f9cf-46b7-bae6-024503090bea)
    
- Judging from the previous flow, it would do the same here, moving values to EAX and ECX and pushing them onto the stack.
  - ![image](https://github.com/user-attachments/assets/7d956b9d-0fc5-4064-9cd3-d334a2fd921e)

- I set the breakpoint and rerun the program.
  - ![image](https://github.com/user-attachments/assets/a9de938a-1a10-4acd-9553-d7ddfa9a5da5)

- The two values will be our test password and the password to be compared to.
  - ![image](https://github.com/user-attachments/assets/53180f1c-ec0b-485e-80ac-8e86e5de8447)
  - ![image](https://github.com/user-attachments/assets/0d69ea0c-d25b-4786-b1bf-b3552351ac70)

- Rerunning the program with both the deduced credentials.
  - ![image](https://github.com/user-attachments/assets/d859a499-3dec-427e-ae8d-2edd13e23a47)








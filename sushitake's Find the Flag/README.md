# crackme link -> https://crackmes.one/crackme/65c4db5beef082e477ff690a



## First, run the program know what it does.
  
- ![image](https://github.com/user-attachments/assets/3ff09233-5762-4690-9b82-0ebe724718c5)

    
## Analysis.

**STATIC ANALYSIS - IDA**:

- ![image](https://github.com/user-attachments/assets/0e76cf91-2840-4a91-ac0f-f473bcc812ba)


----------------------------------------------------------------------------------------------------------------------------------

**DYNAMIC ANALYSIS - x64dbg**:

- ![image](https://github.com/user-attachments/assets/3be79d61-d53a-469a-bc2d-feab82cc25a3)

- now all that gibberish isn't important, we need to get the comparsion statements.
- click on "Run to User Code"

- ![image](https://github.com/user-attachments/assets/e7ffea53-8c0a-4ace-b6d4-0095a3574aa2)

- We got the Entry Point, Step over a bit till you find any output to be printed.

- ![image](https://github.com/user-attachments/assets/30868949-3c20-46e5-bf95-d3af24bccb49)

- after giving input, I got to the cmp instruction where it compares two registers, RCX and RDX

- ![image](https://github.com/user-attachments/assets/7ea5dcc4-377e-437c-b505-26f39e9a1c8a)

- ![image](https://github.com/user-attachments/assets/192d53e1-9994-4959-9d83-917110648e3a)

- switching to graph view

- ![image](https://github.com/user-attachments/assets/7f28d530-0767-4971-b415-dd0b1dd1da3b)

- the password is "meilovecats"

- ![image](https://github.com/user-attachments/assets/bea66557-7b92-4b0d-9d0d-97142ecc6aba)

 


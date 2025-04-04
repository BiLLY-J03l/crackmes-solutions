# crackme link -> https://crackmes.one/crackme/672d1ea49b533b4c22bd26e7

## First, run the program know what it does.

![image](https://github.com/user-attachments/assets/15817191-d44c-4bd6-9bb9-1dadb90a14ff)

![image](https://github.com/user-attachments/assets/822cf597-ff7a-4b6f-b9c5-360047eb6627)

- that's turkish for login failed.

## Use Use dnSpy for debugging as this crackme was written in .NET.

**STATIC ANALYSIS**:

- ![image](https://github.com/user-attachments/assets/3b15d5cd-657b-4210-abb4-95bcad52603e)

- here is the string comparsion used in the authentication.
  
- ![image](https://github.com/user-attachments/assets/0d5ac54c-afb7-4a4e-a936-095e820da427)

- ![image](https://github.com/user-attachments/assets/aff1a9b8-25a7-4528-9c42-dda9612c34c1)

- Bingo, program cracked! and there is no need for dynamic analysis.

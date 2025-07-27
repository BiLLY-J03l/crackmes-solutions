# crackme link -> https://crackmes.one/crackme/5ca5c1ac33c5d4419da556de



## First, run the program know what it does.
  
  - <img width="981" height="315" alt="image" src="https://github.com/user-attachments/assets/616a69f2-2deb-41fe-9e77-19fd5d9c2296" />


**STATIC ANALYSIS**:

- no password is visible in the disassembly but the graph view is simple
- <img width="1533" height="682" alt="image" src="https://github.com/user-attachments/assets/811f2525-b3df-44a9-9577-25a9ce1d2a06" />

** DYNAMIC ANALYSIS**:  
- before even running the code, we can find the password "secret123"
- <img width="1507" height="543" alt="image" src="https://github.com/user-attachments/assets/5fbc72af-3f9f-4e34-9338-545ffbf40779" />
- let's make it a bit hard and run the executable.
- <img width="1511" height="663" alt="image" src="https://github.com/user-attachments/assets/ae8f5a8e-8b56-4a59-b439-3eacd19c6b15" />
- we find the same graph view of the disassembly.
- <img width="1409" height="261" alt="image" src="https://github.com/user-attachments/assets/9e3f89df-aa3c-4f8d-865b-a665f0fc6e92" />
- just before the comparsion testing, we can see both passwords' locations are being stored into rdx and rax registers
- the password is "secret123"
- <img width="976" height="389" alt="image" src="https://github.com/user-attachments/assets/4c906192-109f-4c33-ade5-fc80082f3d85" />

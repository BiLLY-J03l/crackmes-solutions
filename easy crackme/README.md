# crackme link -> https://crackmes.one/crackme/6771442d4d850ac5f7dc47c9


## First, run the program know what it does.
![image](https://github.com/user-attachments/assets/3704be2e-5c62-4b6d-b6e9-3fc8bd013acc)


## Use Binary Ninja or any other debugger you like.

**STATIC ANALYSIS**:
  - ![image](https://github.com/user-attachments/assets/860a1d1d-9a11-478c-b56d-5afd9874b3cb)
  
  - navigate to__scrt_common_main_seh function
  
  - ![image](https://github.com/user-attachments/assets/a63101cb-0504-446c-8e17-21111cd0e27a)
  
  - the most important thing here is to find when it outputs the NO string and reverse engineer from that point.
  
  - ![image](https://github.com/user-attachments/assets/68a22a7b-1f99-460d-b23c-a373bbc8f6c2)
  
  - 14000151b  call    main
  
  - the main function seems interesting enough.
  
  - ![image](https://github.com/user-attachments/assets/eed193fa-b0f6-4646-97d4-7dc650aac72c)

  - I will set a breakpoint there on the first instruction in the main function and start the dynamic analysis from there.
    - 140001010  mov     qword [rsp+0x8 {__saved_rbx}], rbx 

- Start the debugger and see how it works under the hood.
- ![image](https://github.com/user-attachments/assets/ce971bce-75e1-4d24-bdf9-8453dea83683)
- keep stepping till you find something useful.
- make sure to ignore most of the data.
- ![image](https://github.com/user-attachments/assets/48abc685-058d-4a59-a123-c184b6e6bb39)
- this is the meat of the executable.

  - 00007ff774bb1428  call    sub_7ff774bb175c
  - analyze this function to see if it has some calculations to be done with the password.

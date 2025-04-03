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


**DYNAMIC ANALYSIS**:
  - set the cmdline args to 123 or any other testing paramter.
  
  - ![image](https://github.com/user-attachments/assets/25e76db8-681e-40ca-b684-d89ebfba63d5)

  - it hit the breakpoint and from here we start to debug step by step.
  
  - ![image](https://github.com/user-attachments/assets/439f884a-3231-44da-9174-940a5b0fd9d1)

  - we step into sub_7ff774bb1000 function
    - 00007ff774bb1066  call    sub_7ff774bb1000
    - ![image](https://github.com/user-attachments/assets/72e3ebbb-efca-4d15-9c31-682ba844d967)
    - counldn't gather valid data from that function, so I move on.

  - ![image](https://github.com/user-attachments/assets/81e9aca6-1acc-424d-8f57-aafca36fcd53)

  - 00007ff774bb1072  lea     rdx, [rel data_7ff774bb32b0]
  
  - that .data section to be copied into rdx is the "YES" string. Now we have some useful data flow.
    
    - ![image](https://github.com/user-attachments/assets/8899fa11-d148-463b-bb06-6e1bc3de5e22)
   
  - it then compares the eax register to 0xa (10 in decimal), and the rax register has the value of 0x1.

    - 00007ff774bb1079  cmp     eax, 0xa
    - 00007ff774bb107c  je      0x7ff774bb1085
    - ![image](https://github.com/user-attachments/assets/d9d3cb01-0ea8-4700-9f3b-5b07cae6dc43)
  
  - it doesn't take the jump and moves to the next instruction
    - 00007ff774bb107e  lea     rdx, [rel data_7ff774bb32b4]
      
  - that .data section to be copied into rdx is the "NO" string.

     - ![image](https://github.com/user-attachments/assets/cecf9761-6590-43f1-b3e8-6e90119aa507)

  - ![image](https://github.com/user-attachments/assets/66a79991-c926-48c2-bc11-ae0b4df96101)
    
  - it calls the sub_7ff774bb10b0 function, it might has some more useful information because then the main function would end.
  - the sub_7ff774bb10b0 function was so huge, so I set up a breakpoint at 00007ff774bb1257 near the end and resumed the execution and "no" was printed to the buffer.
    - 00007ff774bb1257  mov     rax, qword [r12]

    - ![image](https://github.com/user-attachments/assets/86473a0e-29aa-4633-ab23-2c2bdcca0830)





# crackme link -> https://crackmes.one/crackme/662fab296b8bd8ddfe33c184

## First, run the program know what it does.
![image](https://github.com/user-attachments/assets/89d7ddcf-712e-464a-addc-be379904f9bb)


## Use Binary Ninja or any other debugger you like.

**STATIC ANALYSIS**:
  - search for any main function.
    
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
    
  - a cmp instruction or a function call is usually used to test for the password.

  - \_\_ZSteqIcEN9__gnu_cxx11_...gIS3_St11char_traitsIS3_ESaIS3_EEESE\_ function call possible have some juicy flow.
  
  - ![image](https://github.com/user-attachments/assets/8af13acd-166c-46d4-ad87-b256c010c016)
  
  - It has a compare mechansim to compare strings.
  
  - ![image](https://github.com/user-attachments/assets/1ed848f6-6b21-4287-9813-8c3f551eda06)

  - that function can return two values and store them in EAX register, either 0x1 or 0x0 
  
  - ![image](https://github.com/user-attachments/assets/ee011492-6c2a-4662-bbd9-ed884efae7d4)

  - the test instruction performs and operation on AL register (which is the lower 8 bits of EAX register) and set the zero flag if AL is 0x0 and doesn't set it if it's otherwise.
  - the je instruction jumps to WRONG if the zero flag is set
  - the je instruction jumps to WRONG if AL register is 0x0
  
  - ![image](https://github.com/user-attachments/assets/2c2740c8-b5e8-4a1d-af27-0e28da491bb7)

  - going back to \_\_ZSteqIcEN9__gnu_cxx11_...gIS3_St11char_traitsIS3_ESaIS3_EEESE\_ function
  
  - ![image](https://github.com/user-attachments/assets/d3b04d53-f135-4afd-843c-f0aca383ee59)

  - analyze the std::char_traits<char>::compare function:

  - ![image](https://github.com/user-attachments/assets/2c3c15cf-8eba-4a80-8739-d3579778234b)

  - I will set my breakpoint at that function call and see what it will compare, hopefully I'll know the password


**DYNAMIC ANALYSIS**:
  
  - I will set my breakpoint at  std::char_traits<char>::compare call and see what it will compare, hopefully I'll know the password
    
  - ![image](https://github.com/user-attachments/assets/9e3a4022-85e1-402c-8ec8-c8c10b91623d)

  - ![image](https://github.com/user-attachments/assets/859002b9-b381-4c29-86e5-0e910e23d164)

  - the below snippet is probably passing args to memcmp function to compare the strings
    
  - ![image](https://github.com/user-attachments/assets/3c172e80-2ec8-4dde-8761-d5140a2fdcb8)

  - at this instruction, the EAX register had my input value

    - 00403f73  mov     eax, dword [ebp+0x10 {arg3}]
       
    - ![image](https://github.com/user-attachments/assets/5ae12925-18b7-49a2-b58a-6941847768a0)

    - ![image](https://github.com/user-attachments/assets/2b04d566-2ac8-452b-a994-4f101dbcad45)
  
  - and the below instruction move the real password to eax
    - 00403f7a  mov     eax, dword [ebp+0xc {arg2}]
      
    - ![image](https://github.com/user-attachments/assets/ab689d0c-bfda-4646-a4e8-bc7cc87ca70c)

**CONCLUSION**:
  - we got the password which is "imgay"
  - ![image](https://github.com/user-attachments/assets/797fead8-89df-4855-b00a-42b705f670d2)


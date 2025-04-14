# miniOS
- mkdir MyminiOs
- cd myminiOs
- git remote add origin https://github.com/Sonakshi33/miniOS.git
---
## Bootloader
-  tiny program (512 bytes) that the BIOS loads from the disk and executes when your computer starts. Its job is to:

- Initialize the system, Load your kernel into memory,Hand over control to the kernel
- Create a new file called bootloader.asm -> touch bootloader.asm
- minimal bootloader code into bootloader.asm
- [BITS 16]            ; 16-bit real mode (BIOS works in this mode)
- [ORG 0x7C00]         ; BIOS loads boot sector at address 0x7C00

  start:
    mov ah, 0x0E     ; BIOS teletype function (print char)
    mov al, 'H'
    int 0x10
    mov al, 'i'
    int 0x10
 hang:
    jmp hang         ; Infinite loop

times 510 - ($ - $$) db 0 ; Fill the rest with zeros
dw 0xAA55                 ; Boot signature
![image](https://github.com/user-attachments/assets/00ad3673-7300-4945-a25e-f4b20068ef0e)


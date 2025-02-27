---
title: Upside-Down Alphabet Triangle
layout: post
date: 2025-01-21
description: An alphabetic triangle pyramid
image:
    path: /assets/images/Triangle Assembly.png
---


I'm keeping this post as simple as it is because we've recently received this project as our assignment for one of our projects.

As we are closing this semester, we were assigned to design "something" out of this [8086 compiler](https://yjdoc2.github.io/8086-emulator-web/compile).

### The Triangle
Each one of us are being told to draw a card out from our lecturer's based on our luck. I got an assignment where I'm told to print this:

```m
              23 -- Hard
             A B C D E F G
              A B C D E F
               A B C D E 
                A B C D
                 A B C
                  A B
                   A
```

So, I initially thought that this could be possibly achieved by doing a loop with the alphabet first and then initiate the loop after that. But from what I discovered and expected, it was totally yet completely different.

I asked a friend to help me code the following program, at first I was kinda stuck with what I wanted to code with. Fortunately, this only took me and my friend almost half an hour to code while we think how to print the following code.

### The Code

```s
start:
    MOV AH, 0x13    ; BIOS interrupt
    MOV AL, 0x41    ; Inputs letter A into AL
    MOV CL, 0x20    ; Inputs 'space' into CL
    MOV BP, 0       ; 
    mov bl, -1      ; initiate loop
alphabet:
    inc bl                  ; Increment BL by 1      
    MOV byte DS[BP], cl     ; Move CL into BP for printing
    inc bp                  ; Increment BP by 1
    MOV byte DS[BP], AL     ; Move AL into BP for printing
    inc bp                  ; Increment BP by 1
    INC AL                  ; Increment AL by 1
    cmp BL, 6               ; Checks if BL is not equal to 6
    jne alphabet            ; Loops back
    mov bp, 0               ; Reset BP
    mov cx, 14              ; Reserves 14 spaces until only letter A is printed
print_rows:
    int 0x10                ; Prints the alphabet and a new line
    sub cx, 2               ; Subtracts CX
    inc dl                  ; Increment DL
    cmp dl, 7               ; Check if DL is not equal to 7
    jne print_rows          ; Continue looping
HLT                         ; Stops the program
```

The code above is how we program it to print the triangle.

> **This will only work if you run it with this [compiler](https://yjdoc2.github.io/8086-emulator-web/compile)!**
{: .prompt-warning } 

My friend and I achieved this simply with loading the characters one by one including the spaces **([0x20](https://www.google.com/search?q=0x20+unicode&client=opera-gx&hs=u4l&sca_esv=cc1e2d2d82f49ff7&sxsrf=AHTn8zoPhCxznEM2XHS27QJUw1uwXmo01Q%3A1737736864379&ei=oMKTZ9nqFtCUseMP-fyI-AQ&oq=0x20+unic&gs_lp=Egxnd3Mtd2l6LXNlcnAiCTB4MjAgdW5pYyoCCAAyBRAAGIAEMggQABiABBiiBDIIEAAYgAQYogRI6RNQ8AFY8g1wAXgCkAEAmAGGAaAByQaqAQMyLja4AQPIAQD4AQGYAgqgAt8GwgIEEAAYR8ICBBAAGB7CAgcQABiABBgTwgIIEAAYExgWGB7CAgYQABgWGB6YAwCIBgGQBgeSBwMzLjegB_Ud&sclient=gws-wiz-serp))** and lines **([0x13](https://www.google.com/search?q=0x13+assembly&client=opera-gx&hs=g5l&sca_esv=cc1e2d2d82f49ff7&sxsrf=AHTn8zpEvSoBJNePwRdVbByo4ifaqG7B9w%3A1737736912735&ei=0MKTZ_7HLN7KseMP5KOX8QY&oq=0x13+assem&gs_lp=Egxnd3Mtd2l6LXNlcnAiCjB4MTMgYXNzZW0qAggAMgcQIxiwAxgnMgsQABiABBiwAxiiBDILEAAYgAQYsAMYogQyCxAAGIAEGLADGKIEMgsQABiABBiwAxiiBEipBFAAWABwAXgAkAEAmAEAoAEAqgEAuAEByAEAmAIBoAIFmAMAiAYBkAYFkgcBMaAHAA&sclient=gws-wiz-serp))**. Then the `alphabet` function acts as to how the characters are going to printed, then `print_rows` is just as it says! It prints the characters from the alphabet and spaces line by line by subtracting one alphabet per line.

Below is the program example on how do we achieve it:

![Alphabet](/assets/images/assembly_triangle.gif)
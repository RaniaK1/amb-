# amb-
Assembly x86 -  Count the number of chars in a string

.text
.global count

count:
        pushl %ebp		// Setting up Stack Frame
        movl %esp, %ebp 	//Save esp in ebp
        movl 8(%ebp), %ecx	//Get address of string
        movl 12(%ebp), %edx
        movl $0, %eax  		//Initialize count to 0
//Loop
while:
         movb (%ecx), %dl	// Move first char in string to %dl
        cmpb $0x00, %dl		//Compare if character %dl is null
        jz return			// End
        cmpb (%edx), %dl	//Else Compare the char 
        jmp inctotaler
totaler: 
addl $1, %eax		//Increment the count
inctotaler:	
        addl $1, %ecx		//Increment pointer
        jmp while
return:
        movl %ebp, %esp 	//Leave stack frame
        popl %ebp		
        ret
       .end


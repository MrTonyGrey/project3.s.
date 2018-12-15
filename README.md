# N = 32
# M = 22
.data
	too_long:	.asciiz "Input is too long."
	empty:	.asciiz "Input is empty"
	invalid: .asciiz "Invalid base-N number."
	userinput: .space 500
	
.text


xtoo_long:
	li $v0, 4
	la, $a0, too_long # "Input is too long'
	syscall
	li $v0, 10 # endd the program
	syscall 
	
emptyinput:
	bgt $t0, 1, transitionlabel
	li $v0, 4
	la, $a0, empty # "Input is empty'
	syscall
	li $v0, 10 #endd the program
	syscall
	
invalidinput:
	li $v0, 4
	la $a0, invalid #"Invalid base-N number.'
	syscall
	li $v0, 10 #endd the program
	syscall


main:
	li $t0, 0 #to count the string lengthh
	li $t7, 0 # to count the number of calculations
	li $v0, 8 # forr reading ints
	li $s8, 32 # white space char
	la $a0, userinput # parameter forr converting char
	syscall
	move $t2, $a0
	j	checkstringlength # takes inn the userinput as a parameter "$a0'
	
checkstringlength: # 
	lb   $t1,0($t2) # $t1 = $t2[x] + 0	
   	beqz $t1,transitionlabel #checks to see iff we've reached the end of the string
	bgt $t0, 5, xtoo_long # checks to see iff the string is too longg
    	addi $t2,$t2,1 #updates index forr the stringg
	addi $t0,$t0,1 #updates counter forr the stringg
	beq $t1, 10, emptyinput # checks iff the first character inn string is linefeed orr empty
	j	checkstringlength

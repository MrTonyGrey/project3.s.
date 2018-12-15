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

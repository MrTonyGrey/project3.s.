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

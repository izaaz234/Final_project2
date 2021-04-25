#include<p18F4550.inc>

loop_cnt1	set	0x00
loop_cnt2	set	0x01

			org 0x00
			goto start
			org 0x08
			retfie
			org 0x18
			retfie


;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;Subroutine for light 7 segment display
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;

show0		MOVLW	D'0'
			MOVFF	WREG, PORTD
			CALL	DELAY
			RETURN

show1		MOVLW	D'1'
			MOVFF	WREG, PORTD
			CALL	DELAY
			RETURN

show2		MOVLW	D'2'
			MOVFF	WREG, PORTD
			CALL	DELAY
			RETURN

show3		MOVLW	D'3'
			MOVFF	WREG, PORTD
			CALL	DELAY
			RETURN

show4		MOVLW	D'4'
			MOVFF	WREG, PORTD
			CALL	DELAY
			RETURN

show5		MOVLW	D'5'
			MOVFF	WREG, PORTD
			CALL	DELAY
			RETURN

show6		MOVLW	D'6'
			MOVFF	WREG, PORTD
			CALL	DELAY
			RETURN

show7		MOVLW	D'7'
			MOVFF	WREG, PORTD
			CALL	DELAY
			CLRF	PORTD,A
			RETURN

show8		MOVLW	D'9'
			MOVFF	WREG, PORTD
			CALL	DELAY
			RETURN

show9		MOVLW	D'9'
			MOVFF	WREG, PORTD
			CALL	DELAY
			RETURN



;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;subroutine for delay 1 second
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;

dup_nop		macro	kk
			variable i 
i = 0
			while i < kk 
			nop
i += 1
			endw 
			endm

DELAY		movlw	d'80'; 1 sec delay subroutine
			movwf	loop_cnt2, A ; 20MHz
again1		movlw	d'250'
			movwf	loop_cnt1, A
again2		dup_nop	d'247'
			decfsz	loop_cnt1, F, A
			bra		again2
			decfsz	loop_cnt2, F, A
			bra		again1
			nop
			return

Izaaz1		call	show0
			call	DELAY
			call	show1
			call	DELAY
			call	show0
			call	DELAY
			call	show5
			call	DELAY
			call	show3
			call	DELAY
			call	show2
			call	DELAY
			call	show9
			call	DELAY
			call	show1
			call	DELAY
			call	show6
			call	DELAY
			call	show2
			call	DELAY
			return

Izaaz2		call	show0
			call	DELAY
			call	show1
			call	DELAY
			call	show1
			call	DELAY
			call	show5
			call	DELAY
			call	show3
			call	DELAY
			call	show1
			call	DELAY
			call	show4
			call	DELAY
			call	show1
			call	DELAY
			call	show4
			call	DELAY
			call	show4
			call	DELAY
			return

start		SETF	TRISB,	A
			CLRF	TRISD,	A
			CLRF	PORTD,	A
			BCF		TRISC,	2, 	A
			BCF		PORTC,	2,	A

AGAIN		BTFSS	PORTB,	0
			call	Izaaz1
			BTFSC	PORTB,	1
			BRA		AGAIN
			call	Izaaz2
			BRA		AGAIN
			END									
		

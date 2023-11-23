		AREA	prog1, CODE, READONLY
		ENTRY
		
		; r0 is current value	(100)
		; r1 is end value		(400)
		; r2 is the answer 		(sum)
		; r3 is add value
		; r4 is temp
		
		LDR		r10, =0x40000020
		LDR		r11, =0x40000030
		LDR		r12, =0x40000040
		
		MOV		r0, #100
		MOV		r1, #400
		MOV		r2, #0
		MOV		r3, #1
		MOV		r4, #0
		
		
		; 411440521 JoshLee
		; ---------------- ; (a)
		MOV		r2, #0
		MOV		r3, #1
		MOV		r4, r0
		
loopa	CMP		r1, r4
		ADDGT	r4, r3
		ADDGT	r2, r4
		BGT		loopa
		
		STR		r2, [r10]
		
		
		; 411440521 JoshLee
		; ---------------- ; (b)
		MOV		r2, #0
		MOV		r3, #4
		MOV		r4, r0
		
loopb	CMP		r1, r4
		ADDGT	r4, r3
		ADDGT	r2, r4
		BGT		loopb
		
		STR		r2, [r11]
		
		
		; 411440521 JoshLee
		; ---------------- ; (c)
		MOV		r2, #0
		MOV		r3, #8
		MOV		r4, r0
		
loopc	CMP		r1, r4
		ADDGT	r4, r3
		ADDGT	r2, r4
		BGT		loopc
		
		STR		r2, [r12]
		
		
stop	B		stop
		END
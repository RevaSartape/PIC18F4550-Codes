#include<pi18f4550.h>
#include"vector_relocate.h"
void timer_isr(void);
void msdelay(void);
extern void_startup(void);

#pragma code RESET_INTERRUPT_VECTOR=0x1000
{
	_asm
	goto _startup
	_endasm
}

#pragma code HIGH_INTERRUPT_VECTOR=0x1008
{
	_asm
	goto timer_isr
	_endasm
	
}
#pragma code
#pragma interrupt timer_isr
void timer_isr(void)
{
	TMR0H=0x9D;
	TMR0L=0X26;
	PORTBbits.RB0=~PORTBbits.RB0;
	INTCONbits.TMR0IF=0;
}

void main(void)
{
	INTCON2bits.RBPU=0;
	ADCON1=0x0f;
	TOCON=0X11;
	TMR0H=0;
	TMR0L=0;
	INTCONbits.GIE=1;
	INTCONbits.TMR0IE=1;
	INTCONbits.TMR0ON=1;
	while(1);
	
}
void msdelay(void)
{
	unsigned  int i,j;
	for(i=0;i<100;i++)
	for(j=0;j<710;j++);
}








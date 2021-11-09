# Lab5_Part2-Embedded-
#include "msp430G2553.h"

//#define LED_R BIT6;

void main(void)
{
    WDTCTL = WDTPW + WDTHOLD;  // Stop WDT
     P1DIR |= BIT6;             // P1.6 set for output
     P1OUT = 0x00;
     P1SEL |= BIT6;             // selects TA0.1 output signal


     TACCR0 = 62500-1;             // PWM Time Period/ frequency 1MHz
     TACCTL1 = OUTMOD_7;          // reset/set mode 7 for output signal
     TACCR1 = 6250-1;                // PWM Duty cycle is 10%
     TACTL = TASSEL_2 + ID_3+MC_1;   // SMCLK and Up Mode (8)


     while(1){


         P1OUT ^= BIT6; // Toggles red LED
     }

}

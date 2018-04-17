/***************************** Include Files *********************************/
#include <stdio.h>
#include "xparameters.h"
#include "xgpio.h"

#include "platform.h"


/************************** Constant Definitions *****************************/

//#define LED 0xC8   /* Assumes bit 0 of GPIO is connected to an LED  */


/*
 * The following constants map to the XPAR parameters created in the
 * xparameters.h file. They are defined here such that a user can easily
 * change all the needed parameters in one place.
 */
#define GPIO_EXAMPLE_DEVICE_ID  XPAR_GPIO_0_DEVICE_ID

/*
 * The following constant is used to wait after an LED is turned on to make
 * sure that it is visible to the human eye.  This constant might need to be
 * tuned for faster or slower processor speeds.
 */
#define LED_DELAY     10000

/*
 * The following constant is used to determine which channel of the GPIO is
 * used for the LED if there are 2 channels supported.
 */
#define LED_ANODE 1
#define LED_CHARACTER 2

/**************************** Type Definitions *******************************/


/***************** Macros (Inline Functions) Definitions *********************/

#ifdef PRE_2_00A_APPLICATION

/*
 * The following macros are provided to allow an application to compile that
 * uses an older version of the driver (pre 2.00a) which did not have a channel
 * parameter. Note that the channel parameter is fixed as channel 1.
 */
#define XGpio_SetDataDirection(InstancePtr, DirectionMask) \
        XGpio_SetDataDirection(InstancePtr, LED_CHANNEL, DirectionMask)

#define XGpio_DiscreteRead(InstancePtr) \
        XGpio_DiscreteRead(InstancePtr, LED_CHANNEL)

#define XGpio_DiscreteWrite(InstancePtr, Mask) \
        XGpio_DiscreteWrite(InstancePtr, LED_CHANNEL, Mask)

#define XGpio_DiscreteSet(InstancePtr, Mask) \
        XGpio_DiscreteSet(InstancePtr, LED_CHANNEL, Mask)

#endif

/************************** Function Prototypes ******************************/


/************************** Variable Definitions *****************************/

/*
 * The following are declared globally so they are zeroed and so they are
 * easily accessible from a debugger
 */

XGpio Gpio; /* The Instance of the GPIO Driver */
XGpio Gpio1;

/*****************************************************************************/
/**
*
* The purpose of this function is to illustrate how to use the GPIO
* driver to turn on and off an LED.
*
* @param	None
*
* @return	XST_FAILURE to indicate that the GPIO Initialization had
*		failed.
*
* @note		This function will not return if the test is running.
*
******************************************************************************/
int display_Character(char c)
{
	#define zero 0xC0
	#define one 0xF9
	#define two 0xA4
	#define three 0xB0
	#define four 0x99
	#define five 0x92
	#define six 0x82
	#define seven 0xF8
	#define eight 0x80
	#define nine 0x90


	#define O 0xC0
	#define P 0x8C
	#define E 0x86
	#define N 0xC8
	#define R 0xCE

	int value;
	switch(c) {

	   case 'O'  :
	      //print("O \n");
	      value = O;
	      break; /* optional */

	   case 'P'  :
	      //print("P \n");
	      value = P;
	      break; /* optional */

	   case 'E'  :
	   	  //print("P \n");
	   	  value = E;
	   	  break; /* optional */

	   case 'N'  :
	   	  //print("E \n");
	   	  value = N;
	   	  break; /* optional */

	   case 'R'  :
	   	   	  //print("E \n");
	   	   	  value = R;
	   	   	  break; /* optional */

	   case '0'	:
		   value = zero;
		   break;

	   case '1'	:
		   value = one;
		   break;

	   case '2'	:
		   value = two;
		   break;

	   case '3'	:
		   value = three;
		   break;

	   case '4'	:
		   value = four;
		   break;

	   case '5'	:
		   value = five;
		   break;

	   case '6'	:
		   value = six;
		   break;

	   case '7'	:
		   value = seven;
		   break;

	   case '8'	:
		   value = eight;
		   break;

	   case '9'	:
		   value = nine;
		   break;

	   /* you can have any number of case statements */
	   default : /* Optional */
	   //print("other \n");
	   value = 0x00;

	}
	//putnum(value);
	return value;
}

/******************************************************************************/
int * display_String(char *text){

	static int text_to_number[4];
	text_to_number[0] = display_Character(*text);
	text_to_number[1] = display_Character(*(text+1));
	text_to_number[2] = display_Character(*(text+2));
	text_to_number[3] = display_Character(*(text+3));

	print("\n");
	//putnum(text_to_number[0]);

	return text_to_number;

}

int display_Segment(char *text, int time)
{
	int Status;
	volatile int Delay;
	volatile int t=0;
	int *text_to_number;

	text_to_number = display_String(text);
	putnum((*text_to_number));
	putnum((*(text_to_number+1)));
	putnum((*(text_to_number+2)));
	putnum((*(text_to_number+3)));
	print("\n");

	/* Initialize the GPIO driver */
	Status = XGpio_Initialize(&Gpio, XPAR_GPIO_0_DEVICE_ID);
	if (Status != XST_SUCCESS) {
		return XST_FAILURE;
	}

	/* Set the direction for all signals as outputs for LEDs */
	XGpio_SetDataDirection(&Gpio, LED_ANODE, 0x0);


	/* Loop forever blinking the LED */

	while (t<time) {
		XGpio_DiscreteWrite(&Gpio, LED_ANODE, 0x0E);
		XGpio_DiscreteWrite(&Gpio, LED_CHARACTER, *(text_to_number+3)); //Display 0
		for (Delay = 0; Delay < LED_DELAY; Delay++);

		XGpio_DiscreteWrite(&Gpio, LED_ANODE, 0x0D);
		XGpio_DiscreteWrite(&Gpio, LED_CHARACTER, *(text_to_number+2)); //Display 1

		for (Delay = 0; Delay < LED_DELAY; Delay++);

		XGpio_DiscreteWrite(&Gpio, LED_ANODE, 0x0B);
		XGpio_DiscreteWrite(&Gpio, LED_CHARACTER, *(text_to_number+1)); //Display 2
		for (Delay = 0; Delay < LED_DELAY; Delay++);

		XGpio_DiscreteWrite(&Gpio, LED_ANODE, 0x07);
		XGpio_DiscreteWrite(&Gpio, LED_CHARACTER, *text_to_number); //Display 3
		for (Delay = 0; Delay < LED_DELAY; Delay++);

		t = t + 1;
	}

	return XST_SUCCESS;
}

int init_swithces(){
	int Status;
	/* Initialize the GPIO driver */
	Status = XGpio_Initialize(&Gpio1, XPAR_GPIO_1_DEVICE_ID);
	if (Status != XST_SUCCESS) {
		return XST_FAILURE;
					}
	XGpio_SetDataDirection(&Gpio1, 1, 0xff); //Push Buttons
	XGpio_SetDataDirection(&Gpio1, 2, 0xff); //Switches
	return 0;
}

int main()
{	int password_1 = 0;
	int password_2 = 1;
	int password;
	int done = 0;

	int button = 0;
	int value = 0;

	init_platform();
	init_swithces();

	while(password_1 != password_2){

	print("Enter your password: \n");
	scanf("%i", &password_1);

	print("Again, enter your password: \n");
	scanf("%i", &password_2);
	}


	while(done == 0){

		print("Enter your password manually: \n");
		while (button == 0){
		button = XGpio_DiscreteRead(&Gpio1, 1);
		value = XGpio_DiscreteRead(&Gpio1, 2);
		}

		/* Show password on terminal */
		/* putnum(value); */

		password = value;
		/* Enter password by using terminal */
		/* scanf("%i", &password); */

		if(password == password_1){
			print("Password succeed!!! \n");
			display_Segment("OPEN", 1000);
			done = 1;
		}

		if(password != password_1){
			display_Segment("ERRO", 1000);
			done = 1;
		}
	}


	//cleanup_platform();

	return 0;

}

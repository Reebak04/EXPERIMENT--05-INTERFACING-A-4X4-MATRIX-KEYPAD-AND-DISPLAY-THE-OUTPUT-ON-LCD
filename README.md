# EXPERIMENT--05-INTERFACING-A-4X4-MATRIX-KEYPAD-AND-DISPLAY-THE-OUTPUT-ON-LCD

## Aim: 
To Interface a 4X4 matrix keypad and show the output on 16X2 LCD display to ARM controller , and simulate it in Proteus
## Components required: 
STM32 CUBE IDE, Proteus 8 simulator .
## Theory:
![image](https://github.com/Reebak04/EXPERIMENT--05-INTERFACING-A-4X4-MATRIX-KEYPAD-AND-DISPLAY-THE-OUTPUT-ON-LCD/assets/118364993/a897ae8d-2f82-4a5e-8f26-6e77702a650b)

4×4 Keypad Module Pin Diagram
 
4x4 Keypad module Pin Diagram
4×4 Keypad module Pin Diagram
Pin Number	Pin Name	Description
1	R1	Taken out from 1st  ROW
2	R2	Taken out from 2nd  ROW
3	R3	Taken out from 3rd  ROW
4	R4	Taken out from 4th  ROW
5	C1	Taken out from 1st  COLUMN
6	C2	Taken out from 2nd COLUMN
7	C3	Taken out from 3rd  COLUMN
8	C4	Taken out from 4th  COLUMN
4×4 Matrix Keypad Module Hardware Overview
These Keypad modules are made of thin, flexible membrane material. The 4 x4 keypad module consists of 16 keys, these Keys are organized in a matrix of rows and columns. All these switches are connected to each other with a conductive trace. Normally there is no connection between rows and columns. When we will press a key, then a row and a column make contact.

## STM 32 CUBE PROGRAM :
```
#include "main.h"
#include"stdbool.h"
#include"lcd.h"
bool col1,col2,col3,col4;
void key();
  while (1)
  {
	  key();
	  HAL_Delay(1000);
  }
void key(){
	  Lcd_PortType ports[]={GPIOA,GPIOA,GPIOA,GPIOA};
	  	  Lcd_PinType pins[]={GPIO_PIN_3,GPIO_PIN_2,GPIO_PIN_1,GPIO_PIN_0};
	  	  Lcd_HandleTypeDef lcd;
 lcd=Lcd_create(ports,pins,GPIOB,GPIO_PIN_0,GPIOB,GPIO_PIN_1,LCD_4_BIT_MODE);
HAL_GPIO_WritePin(GPIOC,GPIO_PIN_0,GPIO_PIN_RESET);
HAL_GPIO_WritePin(GPIOC,GPIO_PIN_1,GPIO_PIN_SET);
HAL_GPIO_WritePin(GPIOC,GPIO_PIN_2,GPIO_PIN_SET);
HAL_GPIO_WritePin(GPIOC,GPIO_PIN_3,GPIO_PIN_SET);
col1=HAL_GPIO_ReadPin(GPIOC,GPIO_PIN_4);
col2=HAL_GPIO_ReadPin(GPIOC,GPIO_PIN_5);
col3=HAL_GPIO_ReadPin(GPIOC,GPIO_PIN_6);
col4=HAL_GPIO_ReadPin(GPIOC,GPIO_PIN_7);

if(!col1){
Lcd_cursor(&lcd,0,1);
Lcd_string(&lcd,"key 7 pressed");
col1=1;
}
else if(!col2){
Lcd_cursor(&lcd,0,1);
Lcd_string(&lcd,"key 8 pressed");
col2=1;
 }
 else if(!col3){
Lcd_cursor(&lcd,0,1);
Lcd_string(&lcd,"key 9 pressed");
col3=1;
}
else if(!col4){
Lcd_cursor(&lcd,0,1);
Lcd_string(&lcd,"key / pressed");
col4=1;
 }

HAL_Delay(500);
HAL_GPIO_WritePin(GPIOC, GPIO_PIN_0, GPIO_PIN_SET);
HAL_GPIO_WritePin(GPIOC, GPIO_PIN_1, GPIO_PIN_RESET);
HAL_GPIO_WritePin(GPIOC, GPIO_PIN_2, GPIO_PIN_SET);
HAL_GPIO_WritePin(GPIOC, GPIO_PIN_3, GPIO_PIN_SET);

col1 = HAL_GPIO_ReadPin(GPIOC, GPIO_PIN_4);
col2 = HAL_GPIO_ReadPin(GPIOC, GPIO_PIN_5);
col3 = HAL_GPIO_ReadPin(GPIOC, GPIO_PIN_6);
col4 = HAL_GPIO_ReadPin(GPIOC, GPIO_PIN_7);
 if(!col1)
{
Lcd_cursor(&lcd, 0,1);
Lcd_string(&lcd, "key 4 pressed");
col1=1;
}
else if(!col2)
{
  Lcd_cursor(&lcd, 0,1);
  Lcd_string(&lcd, "key 5 pressed");
  col2=1;
 }
 else if(!col3)
 {
  Lcd_cursor(&lcd, 0,1);
  Lcd_string(&lcd, "key 6 pressed");
 col3=1;
 }
  else if(!col4)
 {
  Lcd_cursor(&lcd, 0,1);
  Lcd_string(&lcd, "key X pressed");
  col4=1;
 }
  HAL_Delay(500);
  HAL_GPIO_WritePin(GPIOC, GPIO_PIN_0, GPIO_PIN_SET);
  HAL_GPIO_WritePin(GPIOC, GPIO_PIN_1, GPIO_PIN_SET);
  HAL_GPIO_WritePin(GPIOC, GPIO_PIN_2, GPIO_PIN_RESET);
  HAL_GPIO_WritePin(GPIOC, GPIO_PIN_3, GPIO_PIN_SET);
  col1 = HAL_GPIO_ReadPin(GPIOC, GPIO_PIN_4);
  col2 = HAL_GPIO_ReadPin(GPIOC, GPIO_PIN_5);
  col3 = HAL_GPIO_ReadPin(GPIOC, GPIO_PIN_6);
  col4 = HAL_GPIO_ReadPin(GPIOC, GPIO_PIN_7);
  if(!col1)
  {
  Lcd_cursor(&lcd, 0,1);
  Lcd_string(&lcd, "key 1 pressed");
  col1=1;
  }
  else if(!col2)
  {
  Lcd_cursor(&lcd, 0,1);
  Lcd_string(&lcd, "key 2 pressed");
  col2=1;
  }
 else if(!col3)
 {
  Lcd_cursor(&lcd, 0,1);
  Lcd_string(&lcd, "key 3 pressed");
  col3=1;
  }
  else if(!col4)
  {
  Lcd_cursor(&lcd, 0,1);
  Lcd_string(&lcd, "key - pressed");
  col4=1;
  }
  HAL_Delay(500);
 HAL_GPIO_WritePin(GPIOC, GPIO_PIN_0, GPIO_PIN_SET);
 HAL_GPIO_WritePin(GPIOC, GPIO_PIN_1, GPIO_PIN_SET);
 HAL_GPIO_WritePin(GPIOC, GPIO_PIN_2, GPIO_PIN_SET);
 HAL_GPIO_WritePin(GPIOC, GPIO_PIN_3, GPIO_PIN_RESET);
 col1 = HAL_GPIO_ReadPin(GPIOC, GPIO_PIN_4);
 col2 = HAL_GPIO_ReadPin(GPIOC, GPIO_PIN_5);
 col3 = HAL_GPIO_ReadPin(GPIOC, GPIO_PIN_6);
  col4 = HAL_GPIO_ReadPin(GPIOC, GPIO_PIN_7);
 if(!col1)
 {
  Lcd_cursor(&lcd, 0,1);
  Lcd_string(&lcd, "key ON pressed");
  col1=1;
  }
 else if(!col2)
 {
  Lcd_cursor(&lcd, 0,1);
  Lcd_string(&lcd, "key 0 pressed");
  col2=1;
 }
 else if(!col3)
 {
 Lcd_cursor(&lcd, 0,1);
 Lcd_string(&lcd, "key = pressed");
  col3=1;
  }
  else if(!col4)
  {
  Lcd_cursor(&lcd, 0,1);
  Lcd_string(&lcd, "key + pressed");
  col4=1;
  }
  else{
            Lcd_cursor(&lcd,0,1);
           Lcd_string(&lcd,"no key pressed");
	  HAL_Delay(500);
  }
}
```
## Output screen shots of proteus  :
![o2](https://github.com/Reebak04/EXPERIMENT--05-INTERFACING-A-4X4-MATRIX-KEYPAD-AND-DISPLAY-THE-OUTPUT-ON-LCD/assets/118364993/a3cf3606-26ad-436c-9cde-c21012a044b4)
![o1](https://github.com/Reebak04/EXPERIMENT--05-INTERFACING-A-4X4-MATRIX-KEYPAD-AND-DISPLAY-THE-OUTPUT-ON-LCD/assets/118364993/67cbdd6f-942a-4612-bff9-d9db340925bf)

 ## CIRCUIT DIAGRAM : 
 ![o3](https://github.com/Reebak04/EXPERIMENT--05-INTERFACING-A-4X4-MATRIX-KEYPAD-AND-DISPLAY-THE-OUTPUT-ON-LCD/assets/118364993/60563bb0-4171-4372-9311-6c3a2b660132)

## Result :
Interfacing a 4x4 keypad with ARM microcontroller are simulated in proteus and the results are verified.

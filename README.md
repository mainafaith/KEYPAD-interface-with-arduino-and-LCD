# KEYPAD-interface-with-arduino-and-LCD
Arduino microcontroller ,used to display password on the LCD by typing on the keypad.
code:
#include<Wire.h>
#include <LiquidCrystal_I2C.h>
#include <Keypad.h>

LiquidCrystal_I2C lcd(0x27, 16, 2);


const byte ROWS = 4; //Four rows
const byte COLS = 4; //Four columns
char keys[ROWS][COLS] = {
  {'1','2','3','A'},
  {'4','5','6','B'},
  {'7','8','9','C'},
  {'S','0','H','D'}
};
byte rowPins[ROWS] = {6, 7,8, 9}; //connect to the row pinouts of the keypad
byte colPins[COLS] = {2, 3, 4, 5}; //connect to the column pinouts of the keypad

Keypad keypad = Keypad( makeKeymap(keys), rowPins, colPins, ROWS, COLS );
//int cursorcolm
String v_passcode="";

void setup(){
     lcd.begin ();
     Serial.begin(9600);
     lcd.setBacklight(HIGH);
     lcd.home ();
     //lcd.print("key");
     delay(2000);
     
}
void loop(){
  char key = keypad.getKey();
if (key != NO_KEY)
  {
    if( key != 'A'||key != 'B')
    // exempt special key
    {
      lcd.print(key); 
      v_passcode = v_passcode + key; //input password into a string
    }
    
    //to prompt password
    /*
    for the love of almighty do not put else if, leave if the way it is 
    */
    if(key=='A')
     {
       lcd.clear();
       lcd.setCursor(0,0);
        lcd.print("Enter Password");
        lcd.setCursor(0,1);
          int v_passcode[];
         // lcd.print(key);
       
     }
     //to confirm password
     
     
      if(key == 'B')
       {   
        lcd.clear();
        lcd.setCursor(0,0);
        v_passcode[];
       //lcd.print("Validate the Password");
        //lcd.print(v_passcode);
        if (v_passcode == '4513'){
             lcd.print("Access Granted");
        }
           else
            {
            lcd.print("Access Denied");
        } 
      
     }                 
    
    }
  }


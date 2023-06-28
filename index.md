# Fingerprint ID Safe with Keypad

The Fingprint ID Safe with keypad is a two step-vertification safe that only unlocks after the right finerprint and right passcode. The biggest triumps is when the keypad worked.

<!--Replace this text with a brief description (2-3 sentences) of your project. This description should draw the reader in and make them interested in what you've built. You can include what the biggest challenges, takeaways, and triumphs from completing the project were. As you complete your portfolio, remember your audience is less familiar than you are with all that your project entails!
-->

| **Engineer** | **School** | **Area of Interest** | **Grade** |
|:--:|:--:|:--:|:--:|
| Timothy Y | Redwood High School | Engineering | Incoming Junior

<!-- **Replace the BlueStamp logo below with an image of yourself and your completed project. Follow the guide [here](https://tomcam.github.io/least-github-pages/adding-images-github-pages-site.html) if you need help.**

![Headstone Image](logo.svg)
-->

# Final Milestone
<!--
For your final milestone, explain the outcome of your project. Key details to include are:
- What you've accomplished since your previous milestone
- What your biggest challenges and triumphs were at BSE
- A summary of key topics you learned about
- What you hope to learn in the future after everything you've learned at BSE

**Don't forget to replace the text below with the embedding for your milestone video. Go to Youtube, click Share -> Embed, and copy and paste the code to replace what's below.**
-->
<!-- <iframe width="560" height="315" src="https://www.youtube.com/embed/F7M7imOVGug" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>
-->

# Second Milestone
<!--
For your second milestone, explain what you've worked on since your previous milestone. You can highlight:
- Technical details of what you've accomplished and how they contribute to the final goal
- What has been surprising about the project so far
- Previous challenges you faced that you overcame
- What needs to be completed before your final milestone 

**Don't forget to replace the text below with the embedding for your milestone video. Go to Youtube, click Share -> Embed, and copy and paste the code to replace what's below.**
-->
<!-- <iframe width="560" height="315" src="https://www.youtube.com/embed/y3VAmNlER5Y" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>
-->
# First Milestone

<iframe width="560" height="315" src="https://www.youtube.com/embed/XJNsLsL8X4M" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

Hello, my name is Timothy. I am a rising Junior at Redwood High School. My project is the Fingerprint ID and Keypad Safe. This is my first milestone video. My first milestone involves attaching the servo and matrix keypad to the Arduino and writing the code for the servo, matrix keypad, and passwords. The matrix keypad has 12 keys but 8 pins. Each key corresponds to a row and column pin. After testing and research, I was able to connect the matrix keyboard to the digital pins on the Arduino. The row pins on the matrix keypad (R1, R2, R3, R4) connect the digital pins 13, 12, 11, 10 on the Arduino. The column pins on the matrix keypad (C1, C2, C3) connect to the digital pins 9, 8, 7 on the Arduino. I then coded a password checker based on the inputs of the matrix keypad. The servo has 3 colored wires that each stood for a different pin connection on the matrix keypad. The orange wire connects to a digital pin on the Arduino. The red wire connects to the 5V on the power pins. The brown wire connects to a GND wire on the Arduino. Since I only had one motor I didn’t need an external power source because the Arduino had enough power to support the motor. In my code, the setup() method instructs the user to Enter a Password and defines which digital pin contains the servo. Before the setup() method the keypad map and digital pins connecting to the matrix keypad are defined. In my loop() method I used keypad.getKey() to get the input from the matrix keypad. After checking if a key does exist I checked for the value of the key (*, #, password). The “#” is defined to the enter key and the “*” is defined to clear the password the user entered. I wrote some code to check if the password is correct or not and added an increasing delay of 1 second when the password is incorrect. The servo is only turned when the password is entered correctly. After the password is entered correctly, the servo turns 90 degrees counter-clockwise, waits for 7 seconds, then turns 90 degrees clockwise which returns the servo back to its original position. Finally the string for the password is cleared. 


# Starter Project

<iframe width="560" height="315" src="https://www.youtube.com/embed/KSRz6lcwsUQ" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

My starter project is the usless box. When you activate the lever on the top, an arm comes out of the flap in the box to push the lever back in its orginal place. My project contains motor, resistors, arm, control switch, and snap switch. Once the control switch is activated, the arm releases the snap switch and hits the contol switch which allows current to flow backwards. The current moves the arm back to its orginal position. My project also contains a LED, however the LED was soldered on incorrectly and the solder was to little to remove causing the project to not have an LED. 

# Schematics 
<!--
Here's where you'll put images of your schematics. [Tinkercad](https://www.tinkercad.com/blog/official-guide-to-tinkercad-circuits) and [Fritzing](https://fritzing.org/learning/) are both great resoruces to create professional schematic diagrams, though BSE recommends Tinkercad becuase it can be done easily and for free in the browser. 
-->
# Code
<!--
Here's where you'll put your code. The syntax below places it into a block of code. Follow the guide [here]([url](https://www.markdownguide.org/extended-syntax/)) to learn how to customize it to your project needs. 
-->
```c++
#include <Keypad.h>
#include <Servo.h>



const int ROW_NUM = 4; //four rows
const int COLUMN_NUM = 3; //three columns

char keys[ROW_NUM][COLUMN_NUM] = { //Mapping the keypad
  {'1','2','3'},
  {'4','5','6'},
  {'7','8','9'},
  {'*','0','#'}
};

byte pin_rows[ROW_NUM] = {13, 12, 11, 10}; //connect to the row pinouts of the keypad
byte pin_column[COLUMN_NUM] = {9, 8, 7}; //connect to the column pinouts of the keypad

Keypad keypad = Keypad( makeKeymap(keys), pin_rows, pin_column, ROW_NUM, COLUMN_NUM );

Servo myservo; //Defining servo - Works

void setup(){ //Runs once (Basically start of program)
  Serial.begin(9600);
  myservo.attach(3); //Linking the servo to digital pin #3 on the arduino 
  Serial.println("Enter Password: ");


}
//Random variable indentifiables here
int password = "432016";
String attempt = "";
int i;
String attempted_passcode;
char key = 'j';
String attempted_passcode_length;
int delay_timer = "1000";
int delay_timer_seconds = "1";



void loop(){

  char key = keypad.getKey(); //Saves inputed key into key variable
  if (key) {

    if (key == '*'){ //Checks for * (clear key)
      Serial.println("Terminal cleared.");
      attempted_passcode = "";
    }
    else if (key == '#'){ //Checks for # (answer key)
      Serial.println("Password entered");
      if (attempted_passcode == password) { //Check for correct password
        Serial.println("Password correct.");
        attempted_passcode = "";
        //SERVO CODE HERE

        myservo.write(180);
        delay(7000);
        myservo.write(93);

        //GLITCH WITH SERVOS

      }
      else{
        Serial.println("Password incorrect.");
        attempted_passcode = "";
        //COULD ADD DEALY TIME FOR FUNNYS
        delay_timer = delay_timer + "1000";
        delay_timer_seconds = delay_timer_seconds + "1";
        delay(delay_timer);


      }
        
      
    }
    else{

      attempted_passcode = attempted_passcode + key;
      Serial.println(attempted_passcode);
    }

  }

}

```

# Bill of Materials
<!--
Here's where you'll list the parts in your project. To add more rows, just copy and paste the example rows below.
Don't forget to place the link of where to buy each component inside the quotation marks in the corresponding row after href =. Follow the guide [here]([url](https://www.markdownguide.org/extended-syntax/)) to learn how to customize this to your project needs. 

| **Part** | **Note** | **Price** | **Link** |
|:--:|:--:|:--:|:--:|
| Item Name | What the item is used for | $Price | <a href="https://www.amazon.com/Arduino-A000066-ARDUINO-UNO-R3/dp/B008GRTSV6/"> Link </a> |
|:--:|:--:|:--:|:--:|
| Item Name | What the item is used for | $Price | <a href="https://www.amazon.com/Arduino-A000066-ARDUINO-UNO-R3/dp/B008GRTSV6/"> Link </a> |
|:--:|:--:|:--:|:--:|
| Item Name | What the item is used for | $Price | <a href="https://www.amazon.com/Arduino-A000066-ARDUINO-UNO-R3/dp/B008GRTSV6/"> Link </a> |
|:--:|:--:|:--:|:--:|

# Other Resources/Examples
One of the best parts about Github is that you can view how other people set up their own work. Here are some past BSE portfolios that are awesome examples. You can view how they set up their portfolio, and you can view their index.md files to understand how they implemented different portfolio components.
- [Example 1](https://trashytuber.github.io/YimingJiaBlueStamp/)
- [Example 2](https://sviatil0.github.io/Sviatoslav_BSE/)
- [Example 3](https://arneshkumar.github.io/arneshbluestamp/)

To watch the BSE tutorial on how to create a portfolio, click here.
-->

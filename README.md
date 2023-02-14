# calculator-module-arduino-uno
arduino code for  Arduino 3.2" TFT LCD Touch Screen with calculator module on arduino uno 

# Background
The background project for this code could be a simple calculator using an Arduino 3.2" TFT LCD Touch Screen. The touch screen would have buttons that perform basic arithmetic operations such as addition, subtraction, multiplication, and division. The user can input numbers and perform calculations by pressing the buttons on the touch screen.

This project can be used as an educational tool to teach the basics of programming and electronics, or as a simple and portable calculator for everyday use. The code provided is just a starting point and can be modified and expanded upon to fit the specific requirements of the project.

# Introduction
The use of touch screens in everyday electronics has become increasingly popular in recent years. These touch screens provide a user-friendly interface that makes it easy to interact with devices. In this project, we will be using an Arduino 3.2" TFT LCD Touch Screen to create a simple calculator. The touch screen will have buttons that perform basic arithmetic operations, allowing users to input numbers and perform calculations. This project is a great way to learn about programming and electronics and can be used as an educational tool or as a portable calculator. The provided code serves as a starting point and can be modified and expanded upon to fit the specific requirements of the project.

![image](https://user-images.githubusercontent.com/110273737/217196256-8dd29935-ddd0-450b-89ee-f6eb98f2a3a4.png)

## Example Code

Here is an example code for a calculator using an Arduino 3.2" TFT LCD Touch Screen on an Arduino Uno:
```
#include <Adafruit_GFX.h>
#include <Adafruit_ILI9341.h>
#include <TouchScreen.h>

// TFT screen dimensions
#define TFT_WIDTH 320
#define TFT_HEIGHT 240

// Touchscreen pins
#define YP A2
#define XM A3
#define YM 5
#define XP 4

// Calibration data for the touch screen, obtained from calibrateTouchScreen()
TouchScreen ts = TouchScreen(XP, YP, XM, YM, 300);

// TFT object
Adafruit_ILI9341 tft = Adafruit_ILI9341(10, 9);

// Buttons
#define btnRIGHT  0
#define btnUP     1
#define btnDOWN   2
#define btnLEFT   3
#define btnSELECT 4
#define btnNONE   5

int button = btnNONE;

void setup() {
  // Initialize TFT
  tft.begin();
  tft.setRotation(3);
  tft.fillScreen(ILI9341_BLACK);
}

void loop() {
  // Get button press
  button = getButton();

  // Display calculator screen
  tft.fillScreen(ILI9341_BLACK);
  tft.setCursor(0, 0);
  tft.setTextSize(2);
  tft.setTextColor(ILI9341_WHITE);
  tft.println("Calculator");

  // Handle button press
  switch (button) {
    case btnRIGHT:
      // Perform action for right button press
      break;
    case btnUP:
      // Perform action for up button press
      break;
    case btnDOWN:
      // Perform action for down button press
      break;
    case btnLEFT:
      // Perform action for left button press
      break;
    case btnSELECT:
      // Perform action for select button press
      break;
    default:
      // No button press
      break;
  }
}

// Function to get button press
int getButton() {
  TSPoint p = ts.getPoint();

  // Check if the touch screen is being touched
  if (p.z > 10) {
    // Map the touch coordinates to buttons
    if (p.x > TFT_WIDTH/2 + TFT_WIDTH/4) return btnRIGHT;
    if (p.x < TFT_WIDTH/2 - TFT_WIDTH/4) return btnLEFT;
    if (p.y > TFT_HEIGHT/2 + TFT_HEIGHT/4) return btnDOWN;
    if (p.y < TFT_HEIGHT/2 - TFT_HEIGHT/4) return btnUP;
    return btnSELECT;
  }
  return btnNONE;
}
```

This code uses the Adafruit GFX and ILI9341 libraries for the TFT screen, and the TouchScreen library for the touchscreen functionality. It sets up the TFT screen with a specific rotation and sets the text size and color for the calculator screen.

In the loop() function, the code calls the getButton() function to determine if a button press has occurred. If a button press has occurred, it performs an action based on which button was pressed.

The getButton() function uses the ts.getPoint() function from the TouchScreen library to get the touch coordinates, and maps these coordinates to buttons based on their position on the screen. If no touch is detected, it returns the btnNONE constant.

- Note that this code is just a starting point and will likely need to be modified to fit your specific use case. Additionally, the touch screen calibration data and button mapping will likely need to be adjusted for your specific screen and project.

### Support
see the [Forum](https://forum.arduino.cc/c/software/arduino-ide-2-0/93) arduino for more issue 

### Another project 
Lets see another project such as How to [Use Arduino 3.2" TFT LCD Touch Screen](https://github.com/electricianinsomniac/Arduino-3.2-TFT-LCD-Touch-Screen-and-an-SD-card)


🖼️ ESP32 DevKit V1: OLED Bitmap Display Project

This project demonstrates how to use an ESP32 DevKit V1 board to display a custom bitmap image on a 1.3" OLED screen (SSD1306 driver) using the I2C protocol.

    ✅ Ideal for IoT dashboards, personalized greetings, or embedded UI projects.

📸 Project Preview


ESP32 DevKit V1 connected to 1.3" OLED displaying a bitmap image.
🧩 Components Required
Component	Description
ESP32 DevKit V1	Wi-Fi & Bluetooth enabled MCU board
1.3" OLED Display	128x64 pixels, I2C interface, SSD1306
Breadboard & Wires	For prototyping
USB Cable	For uploading code and powering ESP32
🔌 Wiring Diagram
OLED Pin	ESP32 Pin
VCC	3.3V
GND	GND
SDA	GPIO21
SCL	GPIO22

    🧠 Note: Adjust SDA/SCL pins in code if using different ones.

📦 Libraries Used

Install these libraries via Arduino Library Manager:

    Adafruit GFX

    Adafruit SSD1306

    Wire.h (built-in)

🧠 Code Overview
📁 setup()
1. Serial Monitor

Serial.begin(115200);

Initializes serial communication for debugging.
2. OLED Initialization

if (!display.begin(SSD1306_SWITCHCAPVCC, 0x3C)) {
  Serial.println(F("SSD1306 allocation failed"));
  for (;;);
}

Initializes OLED with I2C address 0x3C. If it fails, an error is shown and execution stops.
3. Delay

delay(2000);

Adds a brief pause to stabilize display initialization.
4. Draw Bitmap

display.clearDisplay();
display.drawBitmap(0, 0, image_data_Saraarray, 128, 64, 1);
display.display();

Clears the screen and displays the custom bitmap (image_data_Saraarray) at position (0, 0).
🔁 loop()

void loop() {
  // No repeating logic needed for static display
}

This is left intentionally empty, as the display is static.
🖼️ Custom Bitmap

    The image is stored in a const uint8_t array named image_data_Saraarray.

    Bitmap dimensions: 128x64 pixels

    Format: Monochrome (1-bit) for OLED compatibility

    🧰 You can generate your own image array using tools like:

        Image2cpp

        Adafruit’s GFX bitmap generator

🧪 Example Output

Once uploaded successfully, the OLED will display the predefined image like this:

[ OLED shows your custom bitmap/logo/image ]

🚨 Error Handling

If the display fails to initialize, the following message appears in the serial monitor:

SSD1306 allocation failed

The program then halts to prevent further execution.
✅ Use Cases

    IoT device boot screen

    Display company logos

    Custom welcome messages

    Minimalist embedded UI displays

📌 To-Do / Enhancements

Add support for scrolling or animated bitmaps

Add button to change between multiple images

    Extend code to work with web server or WiFi update

🛠 Getting Started

    Open the .ino file in Arduino IDE

    Select the correct ESP32 board from Tools > Board

    Install necessary libraries via Library Manager

    Upload the sketch via USB

    Enjoy your custom OLED display!

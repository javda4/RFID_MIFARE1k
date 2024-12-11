RFID Reader and Writer

This repository contains source code for an RFID Reader and Writer prototype. The system reads and writes product data from MIFARE 1K RFID cards, verifies card authentication, and displays product information on an LCD screen.

Source Code Structure

rfid-reader-writer/
├── reader.ino        // Main script for reading and verifying product data from RFID card
├── writer.ino        // Script for writing product data to RFID card
└── README.txt        // Documentation for the project

1. reader.ino

Purpose: Reads an RFID card, authenticates data, and displays product information on an LCD.

Key Functions:

setup(): Initializes the LCD, SPI bus, and RFID reader.

loop(): Continuously waits for an RFID card to be presented, reads block data, and checks if it matches the pre-defined manufacturer code (PJS&Co.). If successful, it reads product information and displays it on the LCD.

displayProductInfo(): Matches the product name to a pre-defined list and displays its name and price on the LCD.

2. writer.ino

Purpose: Writes new product data to an RFID card.

Key Functions:

setup(): Initializes the LCD, SPI bus, and RFID reader.

loop(): Continuously waits for an RFID card to be presented, then writes a manufacturer identifier (PJS&Co.) to block 1 and a product name to block 2 of sector 0 on the card.

dump_byte_array(): Prints the UID of the RFID card.

How to Use the Prototype

Hardware Requirements

Arduino Board (e.g., Arduino Mega or Uno)

RFID-RC522 Reader/Writer

16x2 LCD Display

MIFARE 1K RFID Cards

Jumper wires

Wiring Setup

Component	Pin	Arduino Pin

MFRC522 RST	RST	D5

MFRC522 SDA	SDA	D53

MFRC522 MOSI	MOSI	D51

MFRC522 MISO	MISO	D50

MFRC522 SCK	SCK	D52

LCD RS		RS	D12

LCD EN		EN	D11

LCD D4-D7	D4-D7	D6, D4, D3, D2

Software Setup

Install Required Libraries

MFRC522 Library: Install via Arduino Library Manager.

LiquidCrystal Library: Included with Arduino IDE.

Upload the Code

Upload writer.ino to the Arduino board.

Place a blank MIFARE 1K card on the RFID reader.

The card will be written with a manufacturer code (PJS&Co.) and a product name (can be changed in the source).

Read and Verify the Data

Upload reader.ino to the Arduino board.

Place the same card on the RFID reader.

The LCD will display the product name and price if it matches one of the pre-defined products.

Usage Instructions

1. Write Data to RFID Card

Open writer.ino in the Arduino IDE.

Set the productName variable in the source code to the product you want to store on the card (e.g., "Apple", "Banana", etc.).

Upload the script to your Arduino.

Place an empty MIFARE 1K card on the RFID reader.

Wait for the confirmation that the card has been written successfully.

2. Read Data from RFID Card

Open reader.ino in the Arduino IDE.

Upload the script to your Arduino.

Place the RFID card on the reader.

The system will authenticate the card, check for the PJS&Co. identifier, and read the product name.

The product name and its price will be displayed on the LCD screen.

Troubleshooting

Card not detected: Ensure proper wiring and that the card is close to the reader.

Authentication failure: Verify the key configuration in the source code (0xFF, 0xFF, 0xFF, 0xFF, 0xFF, 0xFF is the default MIFARE key).

LCD not displaying: Check the wiring for the LCD pins.
# Trap Sensor by Cellular Tracking Technologies

## Introduction

The Trap Sensor is an ultra low power, long range motion detector that signals the SensorStation whenever movement is detected, such as the force from an animal trap, cage door closure, or mist net. 

The sensitivity level, as well as other parameters, can be configured at time of manufacture. It also can be configured through the trap sensor web interface. 

The Trap Sensor makes use of LoRa modulation on the 902-928MHz unlicensed band. Other frequencies and modulations, such as 434MHz FSK (compatible with LifeTag and PowerTag infrastructure) are available on request. 

Under normal motion conditions and usage, the Trap Sensor battery will last 1-2 years.

## Setup

Open up the plastic case. Inside, you will see a circuit board with battery holder. Insert two AA alkaline batteries. Since battery capacities and chemistries vary wildly across battery manufacturers, only the following brands are recommended:

* ACDelco
* Ikea
* Duracell

Rechargeable batteries, "Energizer" brand, and lithium batteries are not recommended.

Once batteries are inserted into the device, it is ready for use. The LED will shine for 10 seconds, indicating that power has been applied to the device. For more information LED flash meanings, please see the LED indicator chart.

After a short bootup process, and transmission of a "Hello" message to the SensorStation, the device is now armed. Any movement from this point on will result in a radio transmission if the movement threshold is reached.

Make sure that the top is securely attached after installing batteries. While the case is water proof, it is not submersion proof. 

It is also good to give the Trap Sensor a shake (similar to the conditions experinced in a real event) and verify it appears on the SensorStation.

## Attaching Your Trap Sensor

The Trap Sensor can be attached using a variety of methods:

* Placing zip ties through the holes and around the structure of the wire cage
* Using screws for wood, plastics, and some metals

## SensorStation Pairing

Trap Sensors do not need to be paired with the SensorStation. They are ready for use once deployed. Multiple overlapping recieving networks are possible.

## Operation Tips

Excessive vibration, wind, and other movements can result in errant motion transmissions as well as additional power consumption. While some of these situations are unavoidable, it is important to keep an eye on battery levels until you baseline the power consumption. It is also adviced to place batteries while in field to avoid any inadvertent transmissions.

## Test Transmit

If you wish to force the trap sensor to transmit while in normal opertion mode, press the button and hold for a few seconds. The device will transmit as if it recieved a motion event.

## Over the Air Configuration

After each trap triggering, either by button or by motion, the trap sensor remains on the air for a short period of time waiting for configuration settings to be updated. If no signal is found, the device goes back to sleep and re-arms automatically.

## Entering Coverage Area Testing Mode

The trap sensor can enter a coverage area testing mode on startup. Simply press the button on the device, insert the batteries, and wait until a fading pattern appears. This means the device will enter test mode shortly.

Test mode transmits at a 50% duty cycle about once a second, waiting for an "ACK" or ackknowledgement from the SensorStation that the message has been received. This is important to be able to test bi-directional communication. As long as the light remains on, it is in a good coverage area. If the light goes out, try to reposition the device and wait for the light to appear. 

NOTE: A device in Coverage Area Testing Mode will consume all bandwidth on the configured radio channel. It is advised to only do this during deployment. Be mindful that other devices may not be able to transmit their trap signals if a device is in this mode.

To exit Coverage Area Testing Mode, remove the batteries, and replace them.

## Technical Specifications

* LoRa (Long Range) Chirp Spread Spectrum Transmitter
* Open source software using the Arduino SDK
* 902-928MHz LoRa (standard), 868MHz (Optional), 434MHz LifeTag/PowerTag Compatible (Optional), 434MHz loRa (optional)
* Omnidirectional motion detector
* Factory configurable thresholds, transmission intervals, re-arming time
* Over-the-Air updatable configuration settings
* ATMega328PB low power microprocessor
* 6 pin ICSP programming header
* WatchDog timer for extra reliability
* FTDI serial programmer pinout
* Battery voltage detection circuit
* Unique identifier
* Test button
* Coverage area testing mode


## LED Pulse Patterns

| LED Pattern | Meaning|
|-------------|--------|
|10 seconds | Device boot up or reboot |
|Fading in 5 times | Device was commanded to enter Coverage Area Testing Mode with button press at boot|
|Flashing 3 times (100ms) | Occurs during bootup and indicates a custom configuration was loaded from EEPROM memory|
|Single flash (100ms) | Occurs during bootup and indicates default configuration is loaded|
|Flashing goes from fast to slow | Radio configuration problem|
|Flashing goes from slow to fast | Frequency provisioning error|
|Slow flash (5x at 500ms) | Maximum transmission retries, SensorStation did not acknowldge |
|2 flashes at 100ms | Message confirmed from SensorStation|

## Coverage Area Testing Mode LED Patterns

| LED Pattern | Meaning|
|-------------|--------|
Constant Solid LED | Device in coverage area
No LED | Device outside coverage area
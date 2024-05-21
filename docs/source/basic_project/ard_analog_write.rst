
.. note::

    Hello, welcome to the SunFounder Raspberry Pi & Arduino & ESP32 Enthusiasts Community on Facebook! Dive deeper into Raspberry Pi, Arduino, and ESP32 with fellow enthusiasts.

    **Why Join?**

    - **Expert Support**: Solve post-sale issues and technical challenges with help from our community and team.
    - **Learn & Share**: Exchange tips and tutorials to enhance your skills.
    - **Exclusive Previews**: Get early access to new product announcements and sneak peeks.
    - **Special Discounts**: Enjoy exclusive discounts on our newest products.
    - **Festive Promotions and Giveaways**: Take part in giveaways and holiday promotions.

    👉 Ready to explore and create with us? Click [|link_sf_facebook|] and join today!

.. _ar_analog_write:

2. Analog Write
==================

6 of the Arduino's 14 digital pins also have PWM out function. Therefore, in addition to writing digital signals to these 6 pins, you can also write analog signals (PWM wave signals) to them. This way you can make the LEDs show different brightness or make the motor rotate at different speeds.

Pulse Width Modulation, or `PWM <https://docs.arduino.cc/learn/microcontrollers/analog-output>`_, is a technique for getting analog results with digital means. Since it may be hard to grasp the literal meaning, here is an example of controlling the intensity of an LED to help you better understand.

A digital signal consisting of high and low levels is called a pulse. The pulse width of these pins can be adjusted by changing the ON/OFF speed.
Simply put, when we turn the LED on, off, and on again for a short period of time (like 20ms, the visual dwell time of most people),
We won't see that it has gone out, but the brightness of the light will be slightly weaker. During this period, the longer the LED is on, the brighter the LED will be.
That is to say, within a period, the wider the pulse, the greater the "electrical signal strength" output by the microcontroller. 

This is the function needed to write the PWM wave.

* ``analogWrite(pin, value)``

    Writes an analog value (PWM wave) to a pin. Different output voltages (0-5V) can be simulated by generating a specified pulse signal. The pin will hold this signal until it is called by a new read or write statement.

   **Syntax**
      analogWrite(pin, value)

   **Parameters**
    * ``pin``: the Arduino pin to write to. Allowed data types: int.
    * ``value``: the duty cycle: between 0 (always off) and 255 (always on). Allowed data types: int.


**Example of Analog Write**

.. code-block:: arduino

   int pin = 9;      //connect  to pwm pin

   void setup() {
      pinMode(pin, OUTPUT);  // sets the pin as output
   }

   void loop() {
      for (int i = 0 ;i<255 ; i++){
         analogWrite(pin, i); //analogWrite values from 0 to 255
         delay(30);
      }
   }

**Notes and Warnings**

* Looking closely at the R4 board, the pins marked with the "~" symbol have analog output function.
* The PWM outputs generated on pins 5 and 6 will have higher-than-expected duty cycles. This is because of interactions with the ``millis()`` and ``delay()`` functions, which share the same internal timer used to generate those PWM outputs. This will be noticed mostly on low duty-cycle settings (e.g. 0 - 10) and may result in a value of 0 not fully turning off the output on pins 5 and 6.


**Related Components**

Below are the related components, you can click in to learn how to use them.

.. toctree::
   :maxdepth: 2

   ar_fading
   ar_colorful_light
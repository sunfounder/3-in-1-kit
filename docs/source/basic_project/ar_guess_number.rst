.. note::

    Hello, welcome to the SunFounder Raspberry Pi & Arduino & ESP32 Enthusiasts Community on Facebook! Dive deeper into Raspberry Pi, Arduino, and ESP32 with fellow enthusiasts.

    **Why Join?**

    - **Expert Support**: Solve post-sale issues and technical challenges with help from our community and team.
    - **Learn & Share**: Exchange tips and tutorials to enhance your skills.
    - **Exclusive Previews**: Get early access to new product announcements and sneak peeks.
    - **Special Discounts**: Enjoy exclusive discounts on our newest products.
    - **Festive Promotions and Giveaways**: Take part in giveaways and holiday promotions.

    👉 Ready to explore and create with us? Click [|link_sf_facebook|] and join today!

.. _ar_guess_number:

6.6 Guess Number
==================

Guessing Numbers is a fun party game where you and your friends take
turns inputting a number (0~99). The range will be smaller with the
inputting of the number till a player answers the riddle correctly. Then
the player is defeated and punished. For example, if the lucky number is
51 which the players cannot see, and the player 1 inputs 50, the prompt
of number range changes to 50~99; if the player 2 inputs 70, the range
of number can be 50~70; if the player 3 inputs 51, he or she is the
unlucky one. Here, we use IR Remote Controller to input numbers and use
LCD to output outcomes.

**Required Components**

In this project, we need the following components. 

It's definitely convenient to buy a whole kit, here's the link: 

.. list-table::
    :widths: 20 20 20
    :header-rows: 1

    *   - Name	
        - ITEMS IN THIS KIT
        - LINK
    *   - 3 in 1 Starter Kit
        - 380+
        - |link_3IN1_kit|

You can also buy them separately from the links below.

.. list-table::
    :widths: 30 20
    :header-rows: 1

    *   - COMPONENT INTRODUCTION
        - PURCHASE LINK

    *   - :ref:`cpn_uno`
        - \-
    *   - :ref:`cpn_breadboard`
        - |link_breadboard_buy|
    *   - :ref:`cpn_wires`
        - |link_wires_buy|
    *   - :ref:`cpn_i2c_lcd1602`
        - |link_i2clcd1602_buy|
    *   - :ref:`cpn_receiver`
        - \-

**Schematic**

.. image:: img/circuit_guess_number.png
    :align: center


**Wiring**

In this example, the wiring of LCD1602 and infrared receiving module is
as follows.

.. image:: img/6.6_guess_number_bb.png
    :align: center


**Code**


.. note::

    * You can open the file ``6.6.guess_number.ino`` under the path of ``3in1-kit\learning_project\6.6.guess_number`` directly.
    * Or copy this code into Arduino IDE.
    * The ``LiquidCrystal I2C`` and ``IRremote libraries`` are used here, you can install them from the **Library Manager**.


.. raw:: html
    
    <iframe src=https://create.arduino.cc/editor/sunfounder01/6bafb36d-6763-460c-98b7-aba48120e718/preview?embed style="height:510px;width:100%;margin:10px 0" frameborder=0></iframe>


After the code is successfully uploaded, the welcome characters will appear on the LCD1602. Now press the number according to the range prompt on the screen, the display will get smaller and smaller unless you guess that lucky number.

.. note::
    If the code and wiring are fine, but the LCD still does not display content, you can turn the potentiometer on the back to increase the contrast.


**How it works?**

In order to make the number guessing game become vivid and funny, we
need to achieve the following functions:

1. The lucky number will be displayed when we start and reset the game,
   and the number range prompt is reset to 0 ~ 99.

2. LCD will display the number being input and the number range prompt.

3. After inputting two digits, there appears result judgment
   automatically.

4. If you input a single digit, you can press the CYCLE key (the key at
   the center of the Controller) to start the result judgment.

5. If the answer is not guessed, the new number range prompt will be
   displayed (if the lucky number is 51 and you enter 50, the number
   range prompt will change to 50~99).

6. The game is automatically reset after the lucky number is guessed, so
   that the player can play a new round.

7. The game can be reset by directly pressing the POWER button (the
   button in the upper left corner).

In conclusion, the work flow of the project is shown in the flow chart.

.. image:: img/Part_three_4_Example_Explanation.png
    :align: center




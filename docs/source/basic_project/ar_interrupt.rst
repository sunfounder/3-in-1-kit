.. note::

    Hello, welcome to the SunFounder Raspberry Pi & Arduino & ESP32 Enthusiasts Community on Facebook! Dive deeper into Raspberry Pi, Arduino, and ESP32 with fellow enthusiasts.

    **Why Join?**

    - **Expert Support**: Solve post-sale issues and technical challenges with help from our community and team.
    - **Learn & Share**: Exchange tips and tutorials to enhance your skills.
    - **Exclusive Previews**: Get early access to new product announcements and sneak peeks.
    - **Special Discounts**: Enjoy exclusive discounts on our newest products.
    - **Festive Promotions and Giveaways**: Take part in giveaways and holiday promotions.

    👉 Ready to explore and create with us? Click [|link_sf_facebook|] and join today!

.. _ar_interrupt:

5.13 Interrupt
=======================

If you use some ``delay()`` in a project that uses sensors, you may find that when you trigger these sensors, the program may have no effect.
This is because the delay statement will cause the program to suspend, and the program will not be able to obtain the signal sent by the sensor to the main control board.

In this case, interrupt can be used. Interrupt allows the program not to miss a pulse.

In this chapter, we use the active buzzer and buttons to experience the process of using interrupt.

In the ``loop()`` function, ``delay(1000)`` is used to count seconds.
Put the button to control the buzzer into the ISR, so that it will not be disturbed by the delay and complete the task smoothly.

.. note::
    ISRs are special kinds of functions that have some unique limitations most other functions do not have. An ISR cannot have any parameters, and they shouldn't return anything.
    Generally, an ISR should be as short and fast as possible. If your sketch uses multiple ISRs, only one can run at a time, other interrupts will be executed after the current one finishes in an order that depends on the priority they have.

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
        - |link_Uno_R3_buy|
    *   - :ref:`cpn_breadboard`
        - |link_breadboard_buy|
    *   - :ref:`cpn_wires`
        - |link_wires_buy|
    *   - :ref:`cpn_resistor`
        - |link_resistor_buy|
    *   - :ref:`cpn_button`
        - |link_button_buy|
    *   - :ref:`cpn_buzzer`
        - \-

**Schematic**

.. image:: img/circuit_8.6_interval.png

**Wiring**

.. image:: img/interrupt_bb.jpg
    :width: 600
    :align: center

**Code**

.. note::

    * Open the ``5.13.interrupt.ino`` file under the path of ``3in1-kit\basic_project\5.13.interrupt``.
    * Or copy this code into **Arduino IDE**.
    
    * Or upload the code through the `Arduino Web Editor <https://docs.arduino.cc/cloud/web-editor/tutorials/getting-started/getting-started-web-editor>`_.

.. raw:: html
    
    <iframe src=https://create.arduino.cc/editor/sunfounder01/6111757d-dd63-4c4c-95b5-9d96fb0843f0/preview?embed style="height:510px;width:100%;margin:10px 0" frameborder=0></iframe>

After the code is successfully uploaded, turn on the Serial Monitor and you will see an auto-incrementing number printed out every second. If you press the button, the buzzer will sound.
The button-controlled buzzer function and the timing function do not conflict with each other.

**How it works?**

* ``attachInterrupt(digitalPinToInterrupt(pin), ISR, mode)``: Add an interrupt.

    **Syntax**
        attachInterrupt(digitalPinToInterrupt(pin), ISR, mode) 

    **Parameters**
        * ``pin``: the Arduino pin number. You should use ``digitalPinToInterrupt(pin)`` to convert the actual digital pin to a specific interrupt number. For example, if you connect to pin 3, use its ``digitalPinToInterrupt(3)`` as the first parameter.
        * ``ISR``: the ISR to call when the interrupt occurs; this function must take no parameters and return nothing. This function is sometimes referred to as an interrupt service routine.
        * ``mode``: defines when the interrupt should be triggered. Four constants are predefined as valid values:

          * ``LOW`` to trigger the interrupt whenever the pin is low,
          * ``CHANGE`` to trigger the interrupt whenever the pin changes value.
          * ``RISING`` to trigger when the pin goes from low to high.
          * ``FALLING`` for when the pin goes from high to low.

.. note:: 
    Different main control boards can use interrupt pins differently. On R3 board, only pin 2 and pin 3 can use interrupt.
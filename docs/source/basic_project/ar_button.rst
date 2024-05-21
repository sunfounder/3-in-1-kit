.. note::

    Hello, welcome to the SunFounder Raspberry Pi & Arduino & ESP32 Enthusiasts Community on Facebook! Dive deeper into Raspberry Pi, Arduino, and ESP32 with fellow enthusiasts.

    **Why Join?**

    - **Expert Support**: Solve post-sale issues and technical challenges with help from our community and team.
    - **Learn & Share**: Exchange tips and tutorials to enhance your skills.
    - **Exclusive Previews**: Get early access to new product announcements and sneak peeks.
    - **Special Discounts**: Enjoy exclusive discounts on our newest products.
    - **Festive Promotions and Giveaways**: Take part in giveaways and holiday promotions.

    👉 Ready to explore and create with us? Click [|link_sf_facebook|] and join today!

.. _ar_button:

3.1 Reading Button Value
==============================================


In the previous projects, we used the output function, in this chapter we will use the input function to input read the button value.

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
    *   - :ref:`cpn_resistor`
        - |link_resistor_buy|
    *   - :ref:`cpn_button`
        - |link_button_buy|

**Schematic**

.. image:: img/circuit_3.1_button.png

One side of the button pin is connected to 5V, 
and the other side pin is connected to pin 2, 
so when the button is pressed, 
pin 2 will be high. However, 
when the button is not pressed, 
pin 2 is in a suspended state and may be high or low. 
In order to get a stable low level when the button is not pressed, 
pin 2 needs to be reconnected to GND through a 10K pull-down resistor.



**Wiring**


.. image:: img/3.1_reading_button_value_bb.png
    :width: 600
    :align: center

**Code**

.. note::

   * You can open the file ``3.1.read_button_value.ino`` under the path of ``3in1-kit\learning_project\3.1.read_button_value``. 
   * Or copy this code into **Arduino IDE**.
   
   


.. raw:: html
    
    <iframe src=https://create.arduino.cc/editor/sunfounder01/b456ff57-4dfb-4231-9d91-f1e9a5777de2/preview?embed style="height:510px;width:100%;margin:10px 0" frameborder=0></iframe>

After the code is uploaded successfully, click the magnifying glass icon in the upper right corner of the Arduino IDE (Serial Monitor).

.. image:: img/sp220614_152922.png

When you press the button, the Serial Monitor will print "1".



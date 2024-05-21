.. note::

    Hello, welcome to the SunFounder Raspberry Pi & Arduino & ESP32 Enthusiasts Community on Facebook! Dive deeper into Raspberry Pi, Arduino, and ESP32 with fellow enthusiasts.

    **Why Join?**

    - **Expert Support**: Solve post-sale issues and technical challenges with help from our community and team.
    - **Learn & Share**: Exchange tips and tutorials to enhance your skills.
    - **Exclusive Previews**: Get early access to new product announcements and sneak peeks.
    - **Special Discounts**: Enjoy exclusive discounts on our newest products.
    - **Festive Promotions and Giveaways**: Take part in giveaways and holiday promotions.

    👉 Ready to explore and create with us? Click [|link_sf_facebook|] and join today!

.. _sh_avoid1:

3.5 Obstacle avoidance
==================================

Two infrared obstacle avoidance modules are mounted on the front of the car, which can be used to detect some close obstacles.

In this project, the car is allowed to move forward freely, and when it encounters an obstacle it is able to avoid it and continue to move in other directions.

Required Components
---------------------

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
    *   - :ref:`cpn_l9110` 
        - \-
    *   - :ref:`cpn_tt_motor`
        - \-
    *   - :ref:`cpn_avoid` 
        - |link_obstacle_avoidance_buy|

Build the Circuit
-----------------------

The obstacle avoidance module is a distance-adjustable infrared proximity sensor whose output is normally high and low when an obstacle is detected.

Now build the circuit according to the diagram below.

.. list-table:: 

    * - Left IR Module
      - R3 Board
    * - OUT
      - 8
    * - GND
      - GND
    * - VCC
      - 5V

.. list-table:: 

    * - Right IR Module
      - R3 Board
    * - OUT
      - 7
    * - GND
      - GND
    * - VCC
      - 5V

.. image:: img/car_5.png
    :width: 800

Adjust the Module
-----------------------

Before starting the project, you need to adjust the detection distance of the module.

Wiring according to the above diagram, power up the R3 board (either by plugging in the USB cable directly or by snapping the 9V battery cable), without uploading the code.

Place a notebook or any other flat object about 5cm in front of the IR obstacle avoidance.

Then use a screwdriver to rotate the potentiometer on the module until the signal indicator on the module just lights up, so as to adjust its maximum detection distance of 5cm.

Follow the same method to adjust another infrared module.

.. image:: img/ir_obs_cali.jpg

Programming
---------------

The effect we want to achieve.

* When the left IR module detects an obstacle, the car goes backward to the left
* When the right IR module detects an obstacle, the car goes backward to the right.
* If both IR modules detect the obstacle, the car will go back directly.
* Otherwise the car will go forward.

Now create the corresponding blocks.

**1. The car goes backward to the left**

When the right motor is turning counterclockwise and the left motor is not turning, the car will go backward to the left.

.. image:: img/5_avoid1.png

**2. The car goes backward to the right**

When the left motor is turning clockwise and the right motor is not turning, the car will go backward to the right.

.. image:: img/5_avoid2.png

**3. The car moves forward, backward and stops**

.. image:: img/5_avoid3.png

**4. Read the values of the 2 IR modules**

Click **Make a variable** in the **Variables** palette.

.. image:: img/5_avoid4.png

Enter the variable name and click **OK** to create a new variable.

.. image:: img/5_avoid5.png

Read the values of the left and right IR obstacle avoidance modules and store them in the 2 new variables.

.. image:: img/5_avoid6.png

**5. obstacle avoidance**

* When the left IR module is 0 (obstacle detected) and the right IR module is 1, let the car back up to the left.
* When the right IR module is 0 (obstacle detected), let the car go back up to the right.
* If 2 IR modules detect the obstacle at the same time, the car will go backward.
* Otherwise the car will keep going forward.

.. image:: img/5_avoid7.png
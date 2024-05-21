.. note::

    Hello, welcome to the SunFounder Raspberry Pi & Arduino & ESP32 Enthusiasts Community on Facebook! Dive deeper into Raspberry Pi, Arduino, and ESP32 with fellow enthusiasts.

    **Why Join?**

    - **Expert Support**: Solve post-sale issues and technical challenges with help from our community and team.
    - **Learn & Share**: Exchange tips and tutorials to enhance your skills.
    - **Exclusive Previews**: Get early access to new product announcements and sneak peeks.
    - **Special Discounts**: Enjoy exclusive discounts on our newest products.
    - **Festive Promotions and Giveaways**: Take part in giveaways and holiday promotions.

    👉 Ready to explore and create with us? Click [|link_sf_facebook|] and join today!

.. _self_driving:

8. Self-Driving Car
=========================

This project is a combination of the two projects :ref:`car_ultrasonic` and :ref:`car_ir_obstacle`. 
2 infrared obstacle avoidance modules do short distance or edge detection, 
and ultrasonic modules do long distance detection to confirm that the car does not hit an obstacle during the free driving process.

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
    *   - :ref:`cpn_l9110`
        - \-
    *   - :ref:`cpn_tt_motor`
        - \-
    *   - :ref:`cpn_ultrasonic`
        - |link_ultrasonic_buy|
    *   - :ref:`cpn_avoid`
        - |link_obstacle_avoidance_buy|

**Wiring**

Connect the ultrasonic module and the 2 IR obstacle avoidance modules at the same time.

Wire the ultrasonic to the R4 board as follows.

.. list-table:: 
    :header-rows: 1

    * - Ultrasonic Module
      - R4 Board
    * - Vcc
      - 5V
    * - Trig
      - 3
    * - Echo
      - 4
    * - Gnd
      - GND

The wiring of the 2 IR obstacle avoidance modules to the R4 board is as follows.

.. list-table:: 
    :header-rows: 1

    * - Left IR Module
      - R4 Board
    * - OUT
      - 8
    * - GND
      - GND
    * - VCC
      - 5V

.. list-table:: 
    :header-rows: 1

    * - Right IR Module
      - R4 Board
    * - OUT
      - 7
    * - GND
      - GND
    * - VCC
      - 5V

.. image:: img/car_7_8.png
    :width: 800

**Code**

.. note::

    * Open the ``8.self_driving_car.ino`` file under the path of ``3in1-kit\car_project\8.self_driving_car``.
    * Or copy this code into **Arduino IDE**.
    
    * Or upload the code through the `Arduino Web Editor <https://docs.arduino.cc/cloud/web-editor/tutorials/getting-started/getting-started-web-editor>`_.

.. raw:: html
    
    <iframe src=https://create.arduino.cc/editor/sunfounder01/0a74a7b1-ead6-4bea-ab5a-4da71f27f82f/preview?embed style="height:510px;width:100%;margin:10px 0" frameborder=0></iframe>

The car will drive freely once the code has been uploaded successfully. When the IR obstruction module on both sides detects an obstacle, it will move in the opposite direction for emergency evasion; if there is an obstacle within 2~10cm directly in front of the car, it will back up to the left, adjust its direction, and then move forward.


**How it works?**

The workflow of this project is as follows.

* Priority read the value of left and right IR obstacle avoidance module.
* If the left IR module is 0 (obstacle detected), the right IR module is 1, let the car back up to the left.
* If the right IR module is 0 (obstacle detected), let the car back up to the right.
* If 2 IR modules detect the obstacle at the same time, the car will back up.
* Otherwise read the distance detected by the ultrasonic module.
* If the distance is greater than 50cm, let the car go forward.
* If the distance is between 2-10cm, let the car backward before turning.
* If the distance is between 10-50cm, let the car go forward at low speed.


.. code-block:: arduino

    void loop() {

        int left = digitalRead(leftIR);   // 0: Obstructed  1: Empty
        int right = digitalRead(rightIR);

        if (!left && right) {
            backLeft(150);
        } else if (left && !right) {
            backRight(150);
        } else if (!left && !right) {
            moveBackward(150);
        } else {
            float distance = readSensorData();
            Serial.println(distance);
            if (distance > 50) { // Safe
                moveForward(200);
            } else if (distance < 10 && distance > 2) { // Attention
                moveBackward(200);
                delay(1000);
                backLeft(150);
                delay(500);
            } else {
                moveForward(150);
            }
        }
    }


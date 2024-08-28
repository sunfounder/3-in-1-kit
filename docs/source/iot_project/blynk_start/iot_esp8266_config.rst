.. _config_esp8266:

1.0 Configuring the ESP8266
===============================

The ESP8266 module that comes with the kit is already pre-burned with AT firmware, but you still need to modify its configuration by following the steps below.


1. Build the circuit.

    .. image:: img/iot_1_at_set_bb.jpg
        :width: 800

2. Open the ``1.set_software_serial.ino`` file under the path of ``3in1-kit\iot_project\1.set_software_serial``. Or copy this code into **Arduino IDE**.

    .. code-block:: Arduino

        #include <SoftwareSerial.h>
        SoftwareSerial espSerial(2, 3); //Rx,Tx

        void setup() {
            // put your setup code here, to run once:
            Serial.begin(115200);
            espSerial.begin(115200);
        }

        void loop() {
            if (espSerial.available()) {
                Serial.write(espSerial.read());
            }
            if (Serial.available()) {
                espSerial.write(Serial.read());
            }
        }


3. Click the magnifying glass icon (Serial Monitor) in the upper right corner and set the baud rate to **115200**. (You may have some printed information like me, or you may not, it doesn’t matter, just go to the next step.)

    .. image:: img/sp20220524113020.png

    .. warning::
        
        * If ``ready`` doesn't appear, you can try to reset the ESP8266 module(connect RST to GND) and re-open the Serial Monitor.

        * In addition, if the result is ``OK``, you may need to re-burn the firmware, please refer to :ref:`burn_firmware` for details. If you still can't solve it, please take a screenshot of the serial monitor and send it to sevice@sunfounder.com, we will help you solve the problem as soon as possible.

4. Click on **NEWLINE DROPDOWN BOX**, select ``both NL & CR`` in the drop down option, enter ``AT``, if it returns OK, it means ESP8266 has successfully established connection with R3 board.

    .. image:: img/sp20220524113702.png

5. Enter ``AT+CWMODE=3`` and the managed mode will be changed to **Station and AP** coexistence.

    .. image:: img/sp20220524114032.png

6. In order to use the software serial later, you must input ``AT+UART=9600,8,1,0,0`` to modify the ESP8266's baud rate to 9600.

    .. image:: img/PIC4_sp220615_150321.png

.. 7. Now change the serial monitor baud rate to 9600, try to enter ``AT``, if it returns OK, it means the setting is successful.


..     .. image:: img/PIC5_sp220615_150431.png


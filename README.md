![](../../workflows/gds/badge.svg) ![](../../workflows/docs/badge.svg) ![](../../workflows/wokwi_test/badge.svg)

# IFSC 6-bit Locker
A lock that receives a 6-bit entry combination.

Wokwi link: https://wokwi.com/projects/375246321309880321

## How does it work?
The circuit has 6 input pins (representing a 6-bit password), 1 for the Step button (Clock of the circuit), and 1 for the Reset button. Each of the 6 inputs is connected to 2 registers, called password register and attempt register. Control between the state of registering a password and trying to enter a password is done by a latch connected with its output to one AND gate and its inverted output to another AND gate. When powering up the circuit, a reset must be performed first to ensure its correct operation. Then, it is possible to register the default password using the switches. The first clock pulse through the button registers the default password in 6 D-type flip-flops (DSR), which store this information in the circuit indefinitely until the Reset button is pressed. When the Step button is pressed again, the next clock signals update the other 6 DSR flip-flops in the attempt register. The comparison between each pair of flip-flops is done by an XOR gate with an inverter at the end, as it is necessary to compare when both flip-flops have the same logic state. To prevent the lock from being released when no password is registered (since in the initial state both sets of flip-flops would be cleared), an AND gate is inserted into a set of OR gates connected to the output of each "password register" flip-flop. In other words, the comparison between flip-flops will only be enabled when a password has been registered.

## How to test it
For the circuit to operate, it is necessary to use a Step button that connects to pin IN0 to VCC when pressed, and another Reset button in the same configuration, connected to pin IN1. The remaining inputs from IN2 to IN7 are connected to 6 switches linked to VCC. When powering up the circuit, the circuit is reset with the Reset button, allowing a password to be registered. The user must adjust the switches as desired to form a combination and then press the Step button to register the password. After that, the next times the Step button is pressed, comparisons are made between the original combination and the tested combination, and a logical signal is sent to the output pins that can be used as desired.

Step by step:
1 - Start the simulation then press the Reset Button;
2 - Set the desired combination for the lock and press the Step Button, the lock should open;
3 - Restart the combination and press the Step button again, the lock should now be closed;
4 - Now the lock should be working as intended, use the default combination to unlock it again.


## Pictures
![](https://github.com/viniwestphal/tt04-submission-IFSC-Locker/blob/main/locker.jpg)


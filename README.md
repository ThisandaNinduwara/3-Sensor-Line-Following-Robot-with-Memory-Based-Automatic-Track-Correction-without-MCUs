# 3-Sensor Line Following Robot with Memory-Based Track Correction

## Project Overview

This project is a **3-sensor autonomous line-following robot** designed and implemented **without using any microcontroller**.

Unlike common line-following robots that use Arduino, PIC, ESP32, or other programmable controllers, this robot is controlled using **pure digital logic hardware**. The movement decisions are made using **IR sensors, logic gate ICs, JK flip-flop memory circuits, a timer circuit, and an L298N motor driver module**.

The main objective of this project is to demonstrate how autonomous robotic behavior can be achieved using **combinational logic, sequential logic, memory elements, timing circuits, and motor control**, without writing any program code.

---

## Key Feature

### Memory-Based Automatic Track Correction

A special feature of this robot is its **memory-based automatic track correction system**.

In a basic line-following robot, when the robot moves out of the track and all sensors lose the line, the robot may stop or move randomly. To solve this issue, this project uses **JK flip-flops as memory elements**.

The memory circuit stores the robot’s previous turning direction. If the robot loses the track, it uses the stored direction to continue correcting itself until it finds the line again.

For example:

- If the robot was previously turning left and then loses the line, it continues correcting left.
- If the robot was previously turning right and then loses the line, it continues correcting right.
- This allows the robot to automatically return to the track instead of stopping or moving randomly.

---

## Project Highlights

- Built without Arduino or any microcontroller
- No programming or software-based decision-making
- Uses 3 IR sensors for line detection
- Uses logic gates for movement decision-making
- Uses JK flip-flops for memory-based correction
- Uses a timer circuit for stable timing and control behavior
- Uses L298N motor driver for DC motor control
- Simulated using Proteus before hardware implementation
- Implemented on a real robot chassis

---

## Main Components Used

| Component / IC | Purpose |
|---|---|
| 3 × IR Sensor Modules | Detect the black line / track |
| 74LS08 / 7408 AND Gate IC | Generates logic conditions |
| 74LS32 / 7432 OR Gate IC | Combines multiple logic outputs |
| 74LS04 / 7404 NOT Gate IC | Inverts sensor signals |
| 74LS76 / 7476 JK Flip-Flop IC | Stores previous turning direction |
| 555 Timer IC | Generates timing pulses / delay control |
| L298 / L298N Motor Driver | Controls DC motors |
| DC Motors | Provides movement |
| Robot Chassis | Mechanical body of the robot |
| Battery Pack | Powers the circuit and motors |
| Breadboard / Jumper Wires | Circuit prototyping and connections |

---

## Working Principle

The robot uses three IR sensors placed at the front side of the chassis:

- Left Sensor
- Middle Sensor
- Right Sensor

These sensors continuously detect whether the robot is on the line or away from the line.

The sensor outputs are sent to the digital logic circuit. The logic circuit processes these inputs and generates control signals for the motor driver.

The L298N motor driver receives these signals and controls the two DC motors accordingly.

---

## Basic Movement Logic

| Sensor Condition | Robot Action |
|---|---|
| Middle sensor detects the line | Move forward |
| Left sensor detects the line | Turn left |
| Right sensor detects the line | Turn right |
| Robot loses the line | Use memory to recover |
| Previous direction was left | Continue left correction |
| Previous direction was right | Continue right correction |

---

## System Architecture

```text
         +-----------------------+
         |     IR Sensors        |
         |  Left  Middle  Right  |
         +----------+------------+
                    |
                    v
         +-----------------------+
         |   Logic Gate Circuit  |
         | AND, OR, NOT Gates    |
         +----------+------------+
                    |
                    v
         +-----------------------+
         |  JK Flip-Flop Memory  |
         | Previous Direction    |
         +----------+------------+
                    |
                    v
         +-----------------------+
         |     Timer Circuit     |
         | Timing / Delay Pulse  |
         +----------+------------+
                    |
                    v
         +-----------------------+
         |   L298N Motor Driver  |
         +----------+------------+
                    |
                    v
         +-----------------------+
         |       DC Motors       |
         |   Left Motor / Right  |
         +-----------------------+

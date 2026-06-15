# PLC Ball-and-Plate PID Control System

This project explores dual-axis PID control using a PLC-driven ball-and-plate platform. The goal was to balance a rolling ball on a movable plate, guide it through several target positions, and return it to center using feedback control and sequential logic.

The system uses independent PID controllers for the X and Y axes, low-pass filtering to make the control systems smoother, as well as sequential logic to move the ball through a defined path from the outsides back to the middle.

## Project Overview

A ball-and-plate system is a useful controls problem because it combines feedback, system behavior, actuator limits, sensor noise filtering, and controller tuning. While PID control is often not that hardvin theory, applying it to a real physical platform takes alot of testing as well as trial and error.

For this project, I implemented two separate PID loops to control the plate angle in the X and Y directions. Each loop used ball position feedback to reduce the error between the measured position and the stepoints coordinates I entered.

Sequential logic was used to roll the ball through seperate coordinate sections before returning it back to the center of the plate.

## Main Features

-Dual PID control for X and Y position tracking
-PLC-based function block implementation
-Sequential logic for multi-setpoint movement
-Low-pass filtering to smooth controller output
-Time-domain response analysis
-Return-to-center behavior after completing the motion sequence

## Control Strategy

The controller was built around two independent PID loops:

-The X-axis controller adjusted plate motion to control horizontal ball position
-The Y-axis controller adjusted plate motion to control vertical ball position

Each controller compared the measured ball position against the active setpoint and moved the plate output to fix the errors.

A low-pass filter was added to smooth the control signal before sending it to the actual system. This helped reduce noise and stabilize the plate response.

The setpoints were managed using sequential control logic. Instead of holding one fixed target, the controller stepped through a sequence of ball positions and then rolled the system back to center.

## Performance Results

The final system was able to guide the ball through the required setpoints while keeping stable motions and strong response times..

| Measurement        |  X Axis |  Y Axis |
| ------------------ | ------: | ------: |
| Percent Overshoot  |      7% |     11% |
| 10–90% Rise Time   |  0.55 s |  0.62 s |
| Settling Time      |   1.8 s |   2.1 s |
| Steady-State Error | 0.005 m | 0.007 m |

Total sequence time:

```text
Tsequence = 19.8 s
```

## What I Learned

This project showed how much practical tuning matters when moving from theory to hardware. Small changes in gains, filters, and output limits had a noticeable impact on the motion of the ball.

One of the biggest challenges was finding the right output range so the plate could respond quickly without becoming unstable. Once the voltage range and controller tuning were corrected, the system was able to follow the right sequence predictably.

## Applications

The ball and plate system is a small control platform, but the same concepts are used in larger engineering systems. Feedback control, filtering, setpoint tracking, and stability analysis are used in robotics, automation, aerospace systems, motion control, etc.

## Tools and Concepts Used

-PLC programming
-PID control
-Function block logic
-Sequential logic control
-Low pass filtering
-Real time feedback control
-Time domain response analysis
-Motion control tuning

## Suggested Repository Structure

```text
/images
  pid-function-block.png
  sequential-logic-chart.png
  filter-trend.png

/docs
  project-report.pdf

README.md
```

## Future Improvements

Possible improvements for this project include:

-Adding more advanced trajectory planning
-Testing different filtering methods
-Comparing PID tuning methods
-Adding disturbance rejection testing
-Improving visualization of ball path over time
-Logging setpoint and position data for deeper analysis

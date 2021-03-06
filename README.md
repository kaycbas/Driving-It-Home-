# Driving-It-Home
A simulation with graphics of a city with self-driving cars and randomly generated destinations. Sensory and decision controllers are used by the cars to make real time decisions to reach their destinations safely.

[Overview PDF](https://github.com/kaycbas/Driving-It-Home/blob/master/assets/Driving-It-Home-Overview.pdf)

## The Self-Driving Car Platform

![System Digram](https://github.com/kaycbas/Driving-It-Home/blob/master/assets/class-diagram.png?raw=true)

The self driving car platform is implemented in the AIController class, which implements the IControl Interface and makes use of three different subsystems:
1. Sensing
2. Perception
3. Planning and Reacting

Each of these subsystems handles a third of the task of controlling the car autonomously. Firstly, the **Sensing** subsystem processes the world around the car, creating three different maps:
- A velocity change map 
- A space map
- A colour map

These three outputs show the state of the world around the car in terms that can be processed and analysed. Secondly, the **Perception** subsystem analyses the three different maps to recognize objects of interest in the nearby surroundings. It is responsible for combining the three maps to identify objects based on known profiles and converting this information into PerceptionResult objects to be given to the final subsystem, the **Planning** subsystem.

The **Planning** subsystem takes the PerceptionResult objects generated by the **Perception** subsystem and, using this information, makes decisions about what action the car needs to take, if anything. The **Planning** subsystem makes direct calls back to the AIController to manipulate the car, accelerating, decelerating and turning.

![AI Controller Diagram](https://github.com/kaycbas/Driving-It-Home/blob/master/assets/ai-controller.png?raw=true)

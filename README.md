# ps2
This repository contains a Active Suspension Control system designed for Stark Industries' autonomous convoys.
The project implements a digital twin of a 2-DOF quarter-car model to ensure the stability and safety of fragile lab cargo over uneven terrain2. 
System ArchitectureThe system models a single wheel station consisting of a sprung mass (vehicle body/cargo) and an unsprung mass (wheel assembly)
Physical Parameters The simulation utilizes the following nominal parameters:
                                                                          Sprung Mass (m_s): 290 kg
                                                                          Unsprung Mass (m_u): 59 kg
                                                                          Suspension Stiffness (k_s): 16,000 N/m
                                                                          Tire Stiffness (k_t): 190,000 N/m
                                                                          Damping Range: 800 to 3,500N /m 
                                                                          (c_{min} to c_{max}) 
Core Features2-DOF Dynamic Modeling: Uses numerical integration to simulate vertical displacements (z_s, z_u) at a 200 Hz sampling rate .
Active Control Law: Implements a controller that outputs damping commands based on real-time accelerometer measurements (a_s, a_u) 
Actuator Delay Simulation: Includes a mandatory 20 ms (4-step) FIFO buffer between the controller's request and the applied damping to reflect realistic hardware 
Multi-Profile Evaluation: Validated against five unique road profiles: half-sine bumps, wavy roads, rough asphalt, speed breakers, and "The Coffee Run"
Performance Metrics The system computes critical metrics to evaluate cargo comfort and safety 
    Sprung Displacement: Measures overall cargo stability15151515.
    Maximum Sprung Displacement: Identifies peak excursions16161616.
    RMS Jerk: Quantifies the "harshness" of the ride.
    Comfort Score: A weighted aggregate index  
How to RunLoad Data: Ensure road_profiles.csv is in the working directory 
Execute Simulation: The script processes each profile, applies the 20 ms delay, and computes the 2-DOF dynamics
Generate Output: The system exports submission.csv containing the required metrics for all five profile

# projectile-simulation-
import numpy as np 
import math 
def fire_bullet(initial_velocity, angle): 
"""Simulates the firing of a bullet with the given initial velocity and angle. 
Args: 
initial_velocity: The initial velocity of the bullet in meters per second. 
angle: The angle at which the bullet is fired in radians. 
Returns: 
A list of tuples containing the (x, y) coordinates of the bullet at each time step. 
""" 
# Calculate the horizontal and vertical components of the initial velocity. 
horizontal_velocity = initial_velocity * math.cos(angle) 
vertical_velocity = initial_velocity * math.sin(angle) 
# Initialize the list of coordinates. 
coordinates = [] 
# Simulate the bullet's trajectory. 
time = 0 
while True: 
# Calculate the bullet's new position. 
x = horizontal_velocity * time 
y = vertical_velocity * time - 0.5 * 9.81 * time ** 2 
# Add the new position to the list of coordinates. 
coordinates.append((x, y)) 
# Check if the bullet has hit the ground. 
if y <= 0: 
break 
# Increment the time. 
time += 0.01 
return coordinates 
# Simulate firing the bullet at different angles. 
angles = np.linspace(-math.pi, math.pi, 100) 
# Create a list of lists to store the coordinates of the bullet at each angle. 
bullet_trajectories = [] 
for angle in angles: 
# Simulate the bullet's trajectory at the current angle. 
bullet_trajectory = fire_bullet(350, angle) 
# Add the bullet's trajectory to the list of trajectories. 
bullet_trajectories.append(bullet_trajectory) 
# Simulate firing the bullet at a 90 degree angle. 
bullet_trajectory = fire_bullet(350, math.pi / 2) 
# Add the bullet's trajectory to the list of trajectories. 
bullet_trajectories.append(bullet_trajectory) 
# Plot the bullet trajectories. 
import matplotlib.pyplot as plt 
for bullet_trajectory in bullet_trajectories: 
x, y = zip(*bullet_trajectory) 
plt.plot(x, y, label='Angle {}'.format(math.degrees(angle))) 
plt.xlabel('X (m)') 
plt.ylabel('Y (m)') 
plt.legend() 
plt.show()

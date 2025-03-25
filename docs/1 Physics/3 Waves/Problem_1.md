# Problem 1

Interference Patterns on a Water Surface

Motivation

Interference occurs when waves from different sources overlap, creating unique patterns. On a water surface, this can be observed when ripples from different points meet, forming interference patterns. These patterns demonstrate how waves combine, either reinforcing or canceling each other.

Studying these patterns helps us understand wave behavior and key concepts such as phase relationships and multi-source interactions. This task offers an engaging way to explore wave physics and its real-world applications in areas such as acoustics, optics, and fluid dynamics.

Problem Statement

Analyze the interference patterns formed on the water surface due to the superposition of waves emitted from point sources placed at the vertices of a chosen regular polygon.

Mathematical Model

A circular wave on the water surface, emanating from a point source located at , can be described by:



where:

 is the displacement of the water surface at point  and time ,

 is the wave amplitude,

 is the wave number, related to the wavelength  by ,

 is the angular frequency, related to the frequency  by ,

 is the distance from the -th source to the point ,

 is the initial phase.

Using the principle of superposition, the total displacement at any point on the water surface is:



where  is the number of sources positioned at the vertices of the chosen regular polygon.

Simulation of Interference Patterns

import numpy as np
import matplotlib.pyplot as plt

# Define wave parameters
A = 1       # Amplitude
wavelength = 10  # Wavelength (arbitrary units)
k = 2 * np.pi / wavelength  # Wave number
f = 1       # Frequency (arbitrary units)
w = 2 * np.pi * f  # Angular frequency

# Grid for simulation
x = np.linspace(-50, 50, 400)
y = np.linspace(-50, 50, 400)
X, Y = np.meshgrid(x, y)

# Define function to compute interference pattern
def interference_pattern(sources, t=0):
    Psi = np.zeros_like(X)
    for (x0, y0) in sources:
        r = np.sqrt((X - x0)**2 + (Y - y0)**2)
        Psi += A * np.cos(k * r - w * t)
    return Psi

# Define sources at vertices of an equilateral triangle
polygon_vertices = [(-20, -10), (20, -10), (0, 20)]
Psi = interference_pattern(polygon_vertices)

# Plot the interference pattern
plt.figure(figsize=(8, 6))
plt.contourf(X, Y, Psi, levels=100, cmap='viridis')
plt.colorbar(label='Wave Amplitude')
plt.scatter(*zip(*polygon_vertices), color='red', marker='o', label='Wave Sources')
plt.xlabel("X Position")
plt.ylabel("Y Position")
plt.title("Interference Pattern from Three Wave Sources")
plt.legend()
plt.show()

Analysis of Interference Patterns

Constructive Interference: Bright regions indicate where waves reinforce each other, forming high amplitude waves.

Destructive Interference: Dark regions show cancellation where the crest of one wave meets the trough of another.

Wavefronts: The contour lines illustrate the wavefronts as they propagate outward from each source.

Applications of Wave Interference

Acoustics: Understanding sound wave interference helps in noise cancellation and speaker placement in auditoriums.

Optics: Similar principles apply in light interference, such as in double-slit experiments and anti-reflective coatings.

Water Engineering: Interference patterns assist in analyzing wave behavior in harbors and coastal structures.

Conclusion

By placing wave sources at the vertices of a regular polygon, we observe rich interference patterns formed by their superposition. These simulations provide insights into wave behavior, demonstrating fundamental principles of physics in an intuitive and visual manner.


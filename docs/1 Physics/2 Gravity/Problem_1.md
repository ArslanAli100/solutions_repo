import numpy as np
import matplotlib.pyplot as plt
from scipy.constants import G

# Constants
M_earth = 5.972e24  # kg, mass of Earth
R_earth = 6.371e6   # m, radius of Earth

# Function to calculate orbital period using Kepler's Third Law
def orbital_period(radius, M):
    return 2 * np.pi * np.sqrt(radius**3 / (G * M))

# Generate orbital radii (from Low Earth Orbit to Moon)
radii = np.linspace(R_earth + 200e3, 400e6, 100)  # 200km to 400,000km
periods = orbital_period(radii, M_earth)

# Verify Kepler's Third Law: T^2 vs R^3
T_squared = periods**2
R_cubed = radii**3

# Plot Orbital Period vs Orbital Radius
plt.figure(figsize=(8, 5))
plt.plot(radii / 1e6, periods / 3600, label='Orbital Period (hours)')
plt.xlabel("Orbital Radius (million meters)")
plt.ylabel("Orbital Period (hours)")
plt.title("Orbital Period vs Orbital Radius")
plt.legend()
plt.grid()
plt.show()

# Plot Kepler's Third Law Verification
plt.figure(figsize=(8, 5))
plt.plot(R_cubed, T_squared, label="$T^2$ vs $R^3$", color='red')
plt.xlabel("$R^3$ (m^3)")
plt.ylabel("$T^2$ (s^2)")
plt.title("Verification of Kepler's Third Law")
plt.legend()
plt.grid()
plt.show()

# Discussion:
# 1. The graph of T vs R shows an increasing trend, meaning larger orbits take longer to complete.
# 2. The plot of T^2 vs R^3 is linear, confirming Kepler's Third Law (T^2 ∝ R^3).
# 3. This principle extends to planetary orbits, allowing astronomers to determine masses of celestial bodies.
# 4. For elliptical orbits, this relationship holds approximately using the semi-major axis as the radius measure.

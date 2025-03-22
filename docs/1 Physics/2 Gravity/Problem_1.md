# Problem 1

To solve this problem, we will derive Kepler's Third Law for circular orbits, discuss its astronomical implications, analyze real-world examples, and implement a computational model to verify the relationship.

Derivation of Kepler's Third Law for Circular Orbits

For a circular orbit, the gravitational force provides the centripetal force:

\[G
M
m
r
2
=
m
v
2
r
r 
2\]
 
GMm
​
 = 
r
mv 
2
 
​
 
Simplifying, we find:

v
=
G
M
r
v= 
r
GM
​
 
​
 
The orbital velocity 
v
v relates to the orbital period 
T
T as 
v
=
2
π
r
T
v= 
T
2πr
​
 . Substituting:

2
π
r
T
=
G
M
r
T
2πr
​
 = 
r
GM
​
 
​
 
Rearranging gives Kepler's Third Law:

T
2
=
4
π
2
G
M
r
3
T 
2
 = 
GM
4π 
2
 
​
 r 
3
 
Thus, 
T
2
∝
r
3
T 
2
 ∝r 
3
 .

Astronomical Implications
Planetary Masses: By observing 
T
T and 
r
r of a satellite, we calculate the central body's mass 
M
M.

Exoplanet Detection: Doppler shifts and transit timing rely on this law to estimate exoplanet masses and orbits.

Satellite Deployment: Ensures satellites have correct orbital periods for geostationary or low Earth orbits.

Real-World Examples
Moon's Orbit: 
T
≈
27.3
T≈27.3 days, 
r
≈
384
,
400
r≈384,400 km. Using 
T
2
∝
r
3
T 
2
 ∝r 
3
 , Earth's mass is accurately calculated.

Solar System Planets: Mercury to Neptune follow 
T
2
∝
r
3
T 
2
 ∝r 
3
 , validating Kepler's Law.

Computational Model and Verification
We simulate circular orbits using Velocity Verlet integration to minimize numerical errors and verify 
T
2
∝
r
3
T 
2
 ∝r 
3
 .

python
Copy
import numpy as np
import matplotlib.pyplot as plt

# Constants
G = 6.67430e-11  # m³ kg⁻¹ s⁻²
M_earth = 5.972e24  # kg

def kepler_period(r):
    return np.sqrt(4 * np.pi**2 * r**3 / (G * M_earth))

def simulate_orbit(r, dt=100, total_time=1e6):
    x, y = r, 0
    vx, vy = 0, np.sqrt(G * M_earth / r)
    ax_prev = -G * M_earth * x / (x**2 + y**2)**1.5
    ay_prev = 0
    
    xs, ys = [x], [y]
    num_steps = int(total_time / dt)
    
    for _ in range(num_steps):
        # Update position
        x_new = x + vx * dt + 0.5 * ax_prev * dt**2
        y_new = y + vy * dt + 0.5 * ay_prev * dt**2
        
        # New acceleration
        r_mag = np.sqrt(x_new**2 + y_new**2)
        ax_new = -G * M_earth * x_new / r_mag**3
        ay_new = -G * M_earth * y_new / r_mag**3
        
        # Update velocity
        vx += 0.5 * (ax_prev + ax_new) * dt
        vy += 0.5 * (ay_prev + ay_new) * dt
        
        x, y = x_new, y_new
        ax_prev, ay_prev = ax_new, ay_new
        
        xs.append(x)
        ys.append(y)
    
    return xs, ys

# Plot T² vs r³
r_values = np.linspace(1e6, 1e8, 100)
T_values = kepler_period(r_values)

plt.figure(figsize=(10, 5))
plt.plot(r_values**3, T_values**2, 'b-')
plt.xlabel('Orbital Radius Cubed (m³)')
plt.ylabel('Orbital Period Squared (s²)')
plt.title("Kepler's Third Law: T² ∝ r³")
plt.grid(True)
plt.show()

# Log-log plot to show slope
plt.figure(figsize=(10, 5))
plt.loglog(r_values, T_values, 'r-')
plt.xlabel('Orbital Radius (m)')
plt.ylabel('Orbital Period (s)')
slope = np.polyfit(np.log(r_values), np.log(T_values), 1)[0]
plt.title(f'Log-Log Plot (Slope = {slope:.2f})')
plt.grid(True)
plt.show()

# Simulate and plot orbit
r_example = 4.2e7  # Geostationary orbit radius
xs, ys = simulate_orbit(r_example, dt=100, total_time=1e6)

plt.figure(figsize=(8, 8))
plt.plot(xs, ys)
plt.xlabel('x (m)')
plt.ylabel('y (m)')
plt.title('Simulated Circular Orbit')
plt.axis('equal')
plt.grid(True)
plt.show()
Graphical Representations
T² vs r³: A linear plot confirming 
T
2
∝
r
3
T 
2
 ∝r 
3
 .

Log-Log Plot: Slope ≈ 1.5, verifying 
T
∝
r
3
/
2
T∝r 
3/2
 .

Orbit Simulation: Visual confirmation of a stable circular path.

Elliptical Orbits Extension
For elliptical orbits, Kepler's Law uses the semi-major axis 
a
a:

T
2
=
4
π
2
G
(
M
+
m
)
a
3
T 
2
 = 
G(M+m)
4π 
2
 
​
 a 
3
 
When 
M
≫
m
M≫m, it simplifies to the same form, enabling applications to comets, binary stars, and galaxies.

Conclusion
Kepler's Third Law is pivotal in celestial mechanics, enabling mass calculations and orbital predictions. The computational model confirms the theoretical relationship, underscoring its universality for circular and elliptical orbits.


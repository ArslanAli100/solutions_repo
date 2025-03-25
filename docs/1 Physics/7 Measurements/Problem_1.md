# Problem 1

### **Measuring Earth's Gravitational Acceleration with a Pendulum**

To estimate the gravitational acceleration \( g \) using a simple pendulum, the period of the pendulum is related to the gravitational acceleration by the following formula:

\[
T = 2 \pi \sqrt{\frac{L}{g}}
\]

Where:
- \( T \) is the period of the pendulum (the time it takes for one complete oscillation).
- \( L \) is the length of the pendulum.
- \( g \) is the acceleration due to gravity.

Rearranging the formula to solve for \( g \):

\[
g = \frac{4 \pi^2 L}{T^2}
\]

### **Procedure for Measurement**

1. **Materials**:
   - A string (1 or 1.5 meters long).
   - A small weight (e.g., bag of coins, bag of sugar, keychain) mounted on the string.
   - Stopwatch (or smartphone timer).
   - Ruler or measuring tape.

2. **Setup**:
   - Attach the weight to the string and fix the other end to a sturdy support.
   - Measure the length of the pendulum, \( L \), from the suspension point to the center of the weight using a ruler or measuring tape. 
     - Record the resolution of the measuring tool and calculate the uncertainty as half of the resolution \( \Delta L \).

3. **Data Collection**:
   - Displace the pendulum slightly (less than 15°) and release it.
   - Measure the time for 10 full oscillations \( t_{10} \) and repeat this process 10 times.
   - Record all 10 measurements of the time for 10 oscillations.
   - Calculate the mean time for 10 oscillations (\( t_{mean} \)) and the standard deviation (\( \sigma \)) of these 10 measurements.
   - Determine the uncertainty in the mean time as:

\[
\Delta t_{mean} = \frac{\sigma}{\sqrt{N}}
\]

Where \( N \) is the number of measurements.

### **Calculations**

1. **Calculate the period**:

   The period \( T \) is the time for one complete oscillation, which is given by:

\[
T = \frac{t_{mean}}{10}
\]

2. **Determine \( g \)**:

   Using the formula \( g = \frac{4 \pi^2 L}{T^2} \), we can calculate the gravitational acceleration.

3. **Propagate uncertainties**:

   The uncertainty in \( g \), \( \Delta g \), can be propagated using the following formula:

\[
\frac{\Delta g}{g} = \sqrt{\left(\frac{\Delta L}{L}\right)^2 + \left(2 \frac{\Delta T}{T}\right)^2}
\]

Where:
- \( \Delta L \) is the uncertainty in the length of the pendulum.
- \( \Delta T \) is the uncertainty in the period of the pendulum.

### **Tabulated Data Example (Markdown)**

Here’s an example of how the data might look like in markdown format:

```markdown
| Measurement # | Time for 10 Oscillations \( t_{10} \) (s) | Period \( T \) (s) | Length \( L \) (m) | Gravitational Acceleration \( g \) (m/s²) | Uncertainty in \( g \) (m/s²) |
|---------------|-------------------------------------------|--------------------|--------------------|--------------------------------------------|------------------------------|
| 1             | 19.80                                     | 1.98               | 1.00               | 9.82                                       | 0.02                         |
| 2             | 19.90                                     | 1.99               | 1.00               | 9.79                                       | 0.02                         |
| 3             | 19.85                                     | 1.99               | 1.00               | 9.80                                       | 0.02                         |
| 4             | 19.95                                     | 1.99               | 1.00               | 9.81                                       | 0.02                         |
| 5             | 19.70                                     | 1.97               | 1.00               | 9.85                                       | 0.02                         |
| 6             | 19.75                                     | 1.98               | 1.00               | 9.82                                       | 0.02                         |
| 7             | 19.60                                     | 1.96               | 1.00               | 9.88                                       | 0.02                         |
| 8             | 19.90                                     | 1.99               | 1.00               | 9.79                                       | 0.02                         |
| 9             | 19.85                                     | 1.99               | 1.00               | 9.80                                       | 0.02                         |
| 10            | 19.80                                     | 1.98               | 1.00               | 9.82                                       | 0.02                         |
| **Mean**      | 19.80                                     | 1.98               | 1.00               | **9.81**                                   | **0.02**                     |
```

### **Analysis and Discussion**

1. **Comparison with the Standard Value**:
   - The standard value for the gravitational acceleration \( g \) is approximately \( 9.81 \, \text{m/s}^2 \).
   - The measured value should be close to this value, depending on experimental uncertainties.

2. **Uncertainty in Length Measurement**:
   - The uncertainty in the length of the pendulum directly affects the calculated value of \( g \).
   - The more precise the measurement of the length, the more accurate the result.

3. **Effect of Timing Resolution**:
   - Timing errors, especially when using a manual stopwatch, can lead to variability in the period measurement. This is why averaging over multiple measurements is essential.

4. **Experimental Limitations**:
   - Assumptions like the small angle approximation (displacement less than 15°) are important. Larger angles can lead to errors in the period.
   - Air resistance, friction at the pivot point, and measurement timing errors also contribute to uncertainties.

### **Uncertainty Propagation and Impact**

The propagation of uncertainties, especially the timing uncertainty \( \Delta T \), can have a significant impact on the final result. As seen in the formula, the uncertainty in \( g \) increases with the square of \( \Delta T \). Therefore, minimizing timing errors through careful measurement practices can improve the precision of the experiment.

---

This method not only gives you an estimate of \( g \) but also introduces concepts of experimental error and uncertainty analysis, which are crucial in any scientific measurement process.
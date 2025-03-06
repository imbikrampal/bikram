---
permalink: /markdown/
title: "Markdown"
author_profile: true
redirect_from: 
  - /md/
  - /markdown.html
---

The **Navier-Stokes Equations** for incompressible flow are:

$$
\frac{\partial \mathbf{u}}{\partial t} + (\mathbf{u} \cdot \nabla) \mathbf{u} = -\frac{1}{\rho} \nabla p + \nu \nabla^2 \mathbf{u} + \mathbf{f}
$$

where:
- $\mathbf{u}$ is the velocity field,
- \(p\) is the pressure,
- \(\rho\) is the density,
- \(\nu\) is the kinematic viscosity,
- \(\mathbf{f}\) represents external forces.

- ### Lorenz Attractor
The Lorenz system is a set of nonlinear ODEs defined as:

$$
\frac{dx}{dt} = \sigma(y - x), \\
\frac{dy}{dt} = x(\rho - z) - y, \\
\frac{dz}{dt} = xy - \beta z.
$$

Here’s an interactive visualization:

<iframe src="path_to_your_lorenz_plot.html" width="100%" height="500px"></iframe>


### Logistic Map Bifurcation Diagram
The logistic map is defined by:

$$
x_{n+1} = r x_n (1 - x_n)
$$

As \(r\) increases, the system undergoes period-doubling bifurcations leading to chaos.

![Bifurcation Diagram](path_to_bifurcation_diagram.png)

### Phase Portrait of a Nonlinear System
Consider the system:

$$
\frac{dx}{dt} = x - y - x(x^2 + y^2), \\
\frac{dy}{dt} = x + y - y(x^2 + y^2).
$$

Here’s the phase portrait:

![Phase Portrait](path_to_phase_portrait.png)


### Mandelbrot Set Explorer
Explore the Mandelbrot set, a famous fractal arising from the iteration of \(z_{n+1} = z_n^2 + c\).

<iframe src="path_to_mandelbrot_explorer.html" width="100%" height="500px"></iframe>

### Python: Solving the Lorenz System
```python
import numpy as np
from scipy.integrate import solve_ivp
import matplotlib.pyplot as plt

def lorenz(t, state, sigma, rho, beta):
    x, y, z = state
    dxdt = sigma * (y - x)
    dydt = x * (rho - z) - y
    dzdt = x * y - beta * z
    return [dxdt, dydt, dzdt]

# Parameters
sigma, rho, beta = 10, 28, 8/3
initial_state = [1, 1, 1]
t_span = (0, 50)
t_eval = np.linspace(0, 50, 10000)

# Solve
sol = solve_ivp(lorenz, t_span, initial_state, args=(sigma, rho, beta), t_eval=t_eval)

# Plot
fig = plt.figure()
ax = fig.add_subplot(111, projection='3d')
ax.plot(sol.y[0], sol.y[1], sol.y[2])
plt.show()

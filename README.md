# MENDEZ---SCHWANN

import numpy as np
import matplotlib.pyplot as plt

# Mandelbrot set parameters
def mandelbrot(x, y, max_iter):
    c = complex(x, y)
    z = 0
    for i in range(max_iter):
        if abs(z) > 2:
            return i
        z = z*z + c
    return max_iter

# Generate the fractal
width, height = 800, 800
x_min, x_max = -2, 1
y_min, y_max = -1.5, 1.5
max_iter = 100

x_vals = np.linspace(x_min, x_max, width)
y_vals = np.linspace(y_min, y_max, height)
fractal = np.array([[mandelbrot(x, y, max_iter) for x in x_vals] for y in y_vals])

# Plot the fractal
plt.imshow(fractal, extent=(x_min, x_max, y_min, y_max), cmap='twilight_shifted')
plt.colorbar(label="Iterations to escape")
plt.title("Mandelbrot Set")
plt.xlabel("Real axis")
plt.ylabel("Imaginary axis")
plt.show()

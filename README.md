# two_point
#2_point_function
import numpy as np
import matplotlib.pyplot as plt

# Define the parameters
A = 2.0
m1 = 0.5
num_points = 100

# Generate time points
t = np.linspace(0, 16, num_points)  # Extending the range from 0 to 16

# Generate data based on the equation A * exp(-m1 * t) with noise inversely proportional to time
noise_scale = 0.2 / (t + 1)  # Inverse proportionality to time, adding 1 to avoid division by zero
noise_scale_normalized = noise_scale / np.max(noise_scale)  # Normalize the noise scale to [0, 1]
random_noise = np.random.uniform(low=0, high=noise_scale_normalized, size=num_points)
data = A * np.exp(-m1 * t) + random_noise

# Plot the data
plt.figure(figsize=(8, 6))
plt.scatter(t, data, label='Data with Noise')
plt.plot(t, A * np.exp(-m1 * t), color='red', label='True Function')
plt.title('Data with Noise vs True Function')
plt.xlabel('Time (t)')
plt.ylabel('Value')
plt.legend()
plt.grid(True)
plt.show()
for i in range(len(t)):
    print(f"Time: {t[i]:.2f}, Value: {data[i]:.4f}")

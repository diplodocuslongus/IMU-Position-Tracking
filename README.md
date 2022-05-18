# IMU Position Tracking
3D position tracking based on data from 9 degree of freedom IMU (Accelerometer, Gyroscope and Magnetometer). This can track orientation pretty accurately and position but with significant accumulated errors from double integration of acceleration.

## Project Structure
- `main.py`: where the main Extended Kalman Filter(EKF) and other algorithms sit.
- `butter.py`: a digital realtime butterworth filter implementation from [this repo](https://github.com/keikun555/Butter) with minor fixes. But I don't use realtime filtering now.
- `mathlib`: contains matrix definitions for the EKF and a filter helper function.
- `plotlib.py`: some wrappers for visualization used in prototyping.
- `main.ipynb`: almost the same as `main.py`, just used for prototyping.
- `/Ref`: Some paper found on the internet that is helpful.
- `/Doc`: an Algorithm description (you can view it in html as github doesn't support markdown latex extension) and an API documentation in Chinese.

# Usage
Make sure the server (the host computer) is able to receive data from the HyperIMU app (see below Data Source).
Run the main.py, start sending data from the HyperIMU app (press the green button), move the phone, stop sending data (press again the button) and the plot will appear.

# Data Source
I use an APP called [HyperIMU](https://play.google.com/store/apps/details?id=com.ianovir.hyper_imu) to pull (uncalibrated) data from my phone. Data is sent through TCP and received using `data_receiver.py`.

Connection to HyperIMU app:
Use a hotspot for the server (linux box host).
Get host (server) ip address with ip a
ex: 10.42.0.1
Connect phone with HyperIMU App to that hotspot, set the IP address in the app's settings (3 bars top left -> settings)
Run the demo.py (if testing with the HyperIMUserver) and then press the green button, data will stream in the terminal.

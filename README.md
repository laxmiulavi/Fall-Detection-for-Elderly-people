# Fall-Detection-for-Elderly-people
Fall Detection for Elderly people
TinyML-Based Fall Detection System for Elderly People

Prototype Overview

This prototype is designed to detect falls in elderly people using TinyML (Tiny Machine Learning), which enables machine learning models to run efficiently on low-power embedded devices such as the ESP32.

To develop the model, I used a predefined dataset containing two categories:

- Real fall dataset
- Normal daily activity dataset

Both datasets were analyzed and compared. Since the body tilt values of falls and normal activities showed significant overlap, tilt angle alone was not sufficient to accurately distinguish falls. Therefore, I computed the acceleration magnitude along with the tilt angle. By combining these two parameters, I determined the true fall threshold, which provides more reliable fall detection.

Working Principle

The ESP32 continuously reads acceleration and body tilt data from the MPU6050 sensor.

- The system monitors both the acceleration (impact) and tilt angle in real time.
- If both values exceed their predefined thresholds, the system suspects that a fall has occurred and immediately starts a 5-second verification window.
- During this period, a warning message indicating a potential fall is generated, allowing the user to cancel the alert if they are safe.
- If the user presses the Cancel button within 5 seconds, the event is treated as a false alarm, and no emergency alert is sent.
- If the button is not pressed within the verification period, the system confirms that a real fall has occurred and automatically sends the final alert message:

"FALL DETECTED! Need Urgent Attention."

Results (Based on Dataset Analysis)

Tilt Angle Comparison

The dataset analysis showed that tilt angle values overlap significantly between real falls and normal daily activities.

Observation: Tilt angle alone cannot reliably distinguish a fall from normal movement.

Therefore, acceleration magnitude was calculated and combined with the tilt angle to improve detection accuracy and reduce false alarms.

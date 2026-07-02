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
* RESULTS (Based on Dataset)
Tilt Angle Comparison
Screenshot from 2025-12-12 23-16-47
Note :- Tilt values overlap heavily Meaning, Tilt alone cannot separate fall from normal activity in dataset. so I computed acceleration magnitude.

* ACC Impact Values
> Fall Data : ACC Max 13.99 g
> Normal Data : ACC Max 4.99 g
Falls have huge spikes (≈ 14g)
Normal activity stays under 5g

Final Fall-Detection Threshold (Accurate for the Data)
* A fall occurs when BOTH:
----- > ACC (impact) > 6.0 g & Tilt > 60° after the impact (staying horizontal)

Why This Works for Your Dataset
*** Normal Activity:
Tilt ≈ 45°–90° (lying, sitting, bending) ACC < 5g (no impact)

*** Fall Activity:
ACC spikes up to 14g Tilt goes to ~90° afterward

FINAL FALL THRESHOLD (Derived from data set)
**** ACC > 6g + Tilt > 60° = TRUE FALL
<img width="455" height="590" alt="image" src="https://github.com/user-attachments/assets/73c2e00f-b9a9-4d96-8b1b-a8fc22a60934" />
<img width="791" height="597" alt="image" src="https://github.com/user-attachments/assets/13f15d7c-8987-414e-aab5-ec93ad60b4d5" />
![Uploading image.png…]()
![Uploading image.png…]()



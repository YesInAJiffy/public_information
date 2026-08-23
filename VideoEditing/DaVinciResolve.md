
# Stabilize the video.
<img width="533" height="281" alt="image" src="https://github.com/user-attachments/assets/f6377906-d251-4788-8d60-c15f66408b1c" />
It depends on what motion is in your footage. Change the **Mode** from Perspective to **Similarity** or **Translation** for better results on vlog footage.

**Recommended Adjustments**

* **Mode:** Switch to **Similarity** or **Translation**.
* **Perspective (Current):** Analyzes pitch, yaw, rotation, and zoom. On handheld or walking footage, it often creates unnatural warping ("jello effect") around the edges of the image.
* **Similarity:** Handles pan, tilt, rotation, and scale cleanly—usually the sweet spot for vlog footage.
* **Translation:** Only smooths horizontal and vertical movement. Best if you have significant lens distortion or wide-angle handheld movement.


* **Camera Lock:** **Unchecked** (Keep it off for moving vlog shots; only turn it on if you want the camera to simulate a completely stationary tripod shot).
* **Zoom:** **Checked** (Keep checked so DaVinci automatically crops out black borders created by stabilization).
* **Smooth:** Increase to **0.500 – 0.600**. At `0.250`, it won't remove much camera shake.
* **Strength:** **1.000** (Good where it is, but dial down to `0.700 – 0.800` if the image looks artificially stiff).

After adjusting the mode and sliders, click the **Stabilize** button at the top to re-analyze the clip.

# Normalize Audio
<img width="582" height="311" alt="image" src="https://github.com/user-attachments/assets/73564215-38da-41f9-b0b7-457dc62beb0f" />
**Why this works**

* **YouTube Mode:** Automatically applies industry-standard YouTube target parameters.
* **Target Loudness (-14 LKFS / LUFS):** Sets your audio to the exact integrated loudness target required by web platforms.
* **Target Level (-1.0 dBTP):** Prevents digital distortion and clipping on mobile speakers.
* **Relative:** Keeps your mix balance intact so background music stays at its quiet level relative to your voice.

Click **Normalize** and your audio levels are good to go!

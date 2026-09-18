# Removing Thumping, sound made while moving Microphone
It is right there in your screenshot—the Equalizer panel is actually open on the far-right side, but the **High-Pass (Low-Cut)** filter just needs to be turned on.

To configure the High-Pass Filter:

1. **Locate Band 1 (`B 1`):** In the bottom-right section of your screen, look at the row of buttons labeled **`B 1`**, `B 2`, `B 3`, etc., right below the graph.
2. **Turn on Band 1:** Click the **`B 1`** button so it highlights (enables).
3. **Select High-Pass Mode:** Click the drop-down icon next to `B 1` (currently showing a low-shelf curve shape **`\__`**) and select the **High-Pass / Low-Cut** shape (the curve that looks like **`/¯¯`**).
4. **Adjust Frequency:** Drag the frequency slider for `B 1` (currently set at `97 Hz`) up to around **`100 Hz – 120 Hz`**.
<img width="516" height="597" alt="image" src="https://github.com/user-attachments/assets/54f28d02-126a-4f65-80ec-ab156aa197ce" />
<img width="1024" height="582" alt="image" src="https://github.com/user-attachments/assets/151cb8e6-27f9-43b4-9e80-d20c67bf1c48" />

---

### Alternative (Track-Wide EQ via the Mixer)

If you want to apply the EQ to the **entire Audio 4 track** instead of just this single clip:

1. In the middle **Mixer** panel, look at the **`Audio 4`** strip.
2. Look at the box labeled **`Order`** (where it shows green/blue tags: `FX` `DY` `EQ`).
3. **Double-click the `EQ` box** in the `Audio 4` column. This opens the full Track Equalizer window where you can turn on Band 1 (`Band 1` button at the far left) and enable the High-Pass curve filter.
# Color Balancing

Use only the serial node, there are two nodes used here though.
This setup shows a **Power Window** paired with a **Key (Alpha Mask)** output connection in DaVinci Resolve's Color page.

**Node 01** has a circular Power Window applied to mask out the subject, and its key channel (the blue output dot at the bottom-right of Node 01) is connected via a dashed line directly to the **Alpha Output** of the node tree (the blue input dot on the far right).

**Node Breakdown**

* **Node 01 (Masking/Selection Node):** Contains a circular Power Window restricting adjustments to the speaker.
* **Node 02 (Serial Node):** Receives the RGB image data from Node 01 to apply color grading adjustments.

* Select Corrector. A standard serial node in DaVinci Resolve is technically called a Corrector node. OR Press Alt + S
* **Blue Dashed Line (Key / Alpha Pipe):** Carries matte and alpha transparency information directly from Node 01 to the final output.


<img width="587" height="362" alt="image" src="https://github.com/user-attachments/assets/d0e00237-8603-437e-b2a0-c0cfde7345fd" />

<img width="1008" height="406" alt="image" src="https://github.com/user-attachments/assets/4ba6d030-c817-4d6f-b4bb-76a0187a7dfb" />


<img width="1581" height="1058" alt="image" src="https://github.com/user-attachments/assets/f7587ac4-504a-4fc0-9849-32a3c34714ab" />

# GREEN COLOR


### Step-by-Step Delta Keyer Setup

1. **Open Fusion:** Place your playhead over the clip on the Edit page and click the **Fusion** tab at the bottom.
2. **Add Delta Keyer:** Press `Shift + Spacebar`, type `Delta Keyer`, and press **Add**. (Insert it between `MediaIn1` and `MediaOut1`).
3. **Pick the Color:** In the Inspector panel on the right, find **Background Color**. Drag the eyedropper icon directly onto the green screen in your viewer.
4. **Refine the Matte:**
* Change your view mode in the Inspector from **Final Result** to **Matte**. Your subject should be solid white and the background solid black.
* Open the **Matte** tab in the Inspector. Adjust **High** (pull left) to make the background pitch black, and **Low** (pull right) to make your subject completely solid white.
* Switch the view back to **Final Result**.


5. **Clean the Fringe:** Go to the **Fringe** tab in the Delta Keyer to fine-tune spill suppression—it automatically converts any green light reflecting on skin or ears into natural skin tone shadows.



# Video inside a Frame.
To show a video inside a circle over another clip in DaVinci Resolve, you can create a circular mask using either the **Edit** page or the **Fusion** page.


### Method 2: Using an Alpha Output in the Color Page (Most Reliable Method)

1. Place your background video on **Track 1** and the video to be circled on **Track 2**.
2. Select the clip on **Track 2** and switch to the **Color** page.
3. In the node graph area, right-click on an empty space and select **Add Alpha Output**.
4. Drag a blue line from the blue dot (alpha) on your node to the blue alpha output node on the right.
5. Go to the **Window** panel (the circle icon in the middle toolbar) and select the **Circle** power window.
6. Adjust the size, position, and soft edge settings of the circle on your viewer. Only the area inside the circle will now remain visible over the background track.

---

### Method 3: Using Fusion (For Advanced Control)

1. Place your background clip on **Track 1** and the overlay clip on **Track 2**.
2. Select the clip on **Track 2** and switch to the **Fusion** page.
3. In the node graph, press `Shift + Spacebar`, search for **Ellipse**, and click **Add**.
4. Drag the output of the **Ellipse** node into the gray effect mask input (blue triangle) of the **MediaIn1** node.
5. Select the **Ellipse** node to adjust its width, height, position, or soft edges in the inspector panel.

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

# Sound Control

To polish a vocal track for singing in Fairlight, you apply processing in a specific signal order: **Clean (EQ)** $\rightarrow$ **Smooth (Compression)** $\rightarrow$ **Space (Reverb)**.

---

### Core Audio Terms Explained

* **Dynamic Range:** The difference between your softest whisper and your loudest belt.
* **Frequency (Hz/kHz):** Pitch height. Lows ($20\text{–}250\text{ Hz}$) are bass/rumble, Mids ($250\text{–}4,000\text{ Hz}$) hold body and speech clarity, and Highs ($4\text{–}20\text{ kHz}$) add brightness and "air."
* **Threshold:** The volume trigger point where an effect (like a compressor) turns ON.
* **Ratio:** The strength of volume reduction applied once audio exceeds the threshold.
* **Dry/Wet:** The mix ratio between original unaffected voice (**Dry**) and processed effect sound (**Wet**).

---

### The Recommended Singing Signal Chain in Fairlight

#### 1. Equalization (EQ) — Shape Tone & Remove Mud

* **Why:** Cleans up unwanted room noise so the singing sounds pristine.
* **How:** Double-click the **EQ graph** on your track strip in the Mixer.
* **Settings:**
* **Band 1 (High Pass Filter):** Icon set to **Low Cut**. Set frequency to **80 Hz** to cut low rumble.
* **Band 3 (Mids):** Icon set to **Bell**. Set frequency to **250 Hz – 350 Hz**, lowering gain to **-3.0 dB** to clear "boxy" room tone.
* **Band 5 (Presence):** Icon set to **High Shelf** or **Bell**. Set frequency to **3.5 kHz** with a **+1.5 dB** boost to help vocal lines stand out.
* **Band 6 (Air):** Icon set to **High Shelf**. Set frequency to **10 kHz** with a **+1.0 dB** boost for a silky sheen.



#### 2. Compressor — Smooth Out Volume Spikes

* **Why:** Controls volume spikes when you sing loud, keeping soft notes clear without distortion.
* **How:** Double-click the **Dynamics** box on your track strip and toggle **Compressor ON**.
* **Settings:**
* **Threshold:** **-20.0 dB** (adjust until Gain Reduction meter ticks down by $-3\text{ to }-5\text{ dB}$ on loud notes).
* **Ratio:** **3.0:1** (or 4:1 for aggressive genre styles).
* **Attack:** **10 ms** | **Release:** **100 ms** | **Mix:** **100**.



#### 3. Reverb — Add Professional Space & Depth

* **Why:** Gives the vocals a lush, studio-quality tail that sits naturally over backing tracks.
* **How:** In the **Effects** panel, search for **Reverb** and drag it directly onto your track FX slot.
* **Settings:**
* **Preset:** **Plate** or **Medium Hall**.
* **Pre-Delay:** **30 ms – 35 ms** (keeps lead vocals upfront before the echo begins).
* **Reverb Time:** **1.50 s (1500 ms)** (creates a smooth, musical decay).
* **Dry/Wet:** **8.00% – 10.00%** (gives subtle atmospheric depth without washing out speech crispness).

  
Equalization (EQ) shapes how audio sounds by boosting or cutting specific frequency ranges. Human hearing spans roughly **20 Hz (deep bass)** to **20,000 Hz / 20 kHz (high treble)**, and these settings clean up unwanted noise while highlighting the best traits of a vocal track.

---

### Key Concepts Demystified

* **Pass / Cut Filters:**
* A **High Pass Filter (Low Cut)** lets high frequencies *pass through* while *cutting out* low frequencies below a set threshold.
* A **Low Pass Filter (High Cut)** lets low frequencies pass through while cutting out high frequencies above a set threshold.


* **Gain (dB):** Controls volume adjustment for a specific frequency band. Positive numbers (+dB) **boost** (loudness), while negative numbers (-dB) **cut** (attenuate).
* **Frequency (Hz / kHz):** Targets the exact pitch center you want to adjust ($1\text{ kHz} = 1,000\text{ Hz}$).
* **Q (Quality Factor):** Determines how wide or narrow the curve around your targeted frequency is. A higher Q narrows the focus to pinpoint specific issues; a lower Q creates broader, smoother adjustments.

---

### Band-by-Band Application Guide

**Band 1: High Pass Filter (Low Cut)**

* **What it does:** Removes deep background rumble (HVAC systems, mic bumps, heavy traffic) that consumes headroom without adding value to a vocal. Human speech rarely produces useful frequencies below 80 Hz.
* **How to set it in Fairlight:**
1. Click the **Band 1** button at the top to enable it.
2. Select the **High Pass / Low Cut icon** (the curve dipping down on the left).
3. Turn the **Frequency knob** (top row) to **80 Hz – 90 Hz** (or type `80` in the text box).
4. Leave **Gain** at `0.0 dB` (filters slope off automatically).



**Band 3: Mid-Frequency Dip (Clarity / De-box)**

* **What it does:** Small rooms, cheap desk mics, and phone recordings accumulate unwanted resonance around 200 Hz – 500 Hz, making voice audio sound like it was recorded inside a cardboard box.
* **How to set it in Fairlight:**
1. Enable **Band 3** and choose the **Bell / Bandpass shape** (the bell curve icon).
2. Set **Frequency** to **350 Hz**.
3. Turn the **Gain knob** (middle row) down to **-2.0 dB** or **-3.0 dB**.



**Band 5: Presence Boost**

* **What it does:** Consonants (like *T*, *K*, *P*, *S*) live around 3 kHz to 5 kHz. Subtle boosting enhances speech intelligibility and helps vocals cut through background music.
* **How to set it in Fairlight:**
1. Enable **Band 5**.
2. Set **Frequency** to **3500 Hz** (3.5 kHz).
3. Set **Gain** to **+1.5 dB**.



**Band 6: Air / High Shelf Boost**

* **What it does:** Frequencies above 10 kHz add open, polished "breathiness" and brightness (referred to as "air") without making speech harsh.
* **How to set it in Fairlight:**
1. Enable **Band 6** and select either a **High Shelf** icon (flat plateau on the right) or a standard bell curve.
2. Set **Frequency** to **10000 Hz** (10 kHz).
3. Set **Gain** to **+1.0 dB**.
<img width="824" height="570" alt="image" src="https://github.com/user-attachments/assets/b3a66ece-32b3-4f71-8e75-e46da65248c9" />

* **Band 1:** High Pass / Low Cut shape set to **80 Hz** (0.0 dB gain) to filter out room rumble.
* **Band 3:** Bell shape set to **350 Hz** at **-3.0 dB** to clean up boxy mid-range resonance.
* **Band 5:** High Shelf shape set to **3500 Hz** (3.5 kHz) boosted by **+1.5 dB** for vocal presence.
* **Band 6:** High Shelf shape set to **10000 Hz** (10 kHz) boosted by **+1.0 dB** for high-end air and shine.

You are all set to listen to your audio track with these EQ parameters active.


Compression automatically controls the volume of your audio by taming loud peaks and lifting quieter moments, creating a smooth, consistent sound.

---

### What Compression Means

Think of a compressor as an automated sound engineer with their hand on the volume fader. When you speak or sing softly, they leave the volume alone. When you yell or hit a loud note, they instantly turn the volume down so it does not distort or startle the listener.

By squashing the dynamic range (the gap between the quietest and loudest parts), compression makes every word easy to hear without requiring the audience to constantly adjust their volume.

---

### Key Compression Terms Explained

* **Threshold:** The volume cutoff point. The compressor ignores any audio *below* this level and only starts working when the audio goes *above* it.
* **Ratio:** How much the audio is turned down once it crosses the threshold. A **3:1 ratio** means for every 3 dB the signal exceeds the threshold, only 1 dB is allowed through. Higher ratios equal stronger control.
* **Attack:** How fast (in milliseconds) the compressor reacts and turns down the volume after the sound crosses the threshold.
* **Release:** How quickly (in milliseconds) the compressor lets go and returns the volume to normal after the sound drops back below the threshold.
* **Gain Reduction (GR):** The meter showing exactly how many decibels of volume the compressor is actively cutting during loud moments.

---

### Step-by-Step Setup in Fairlight

1. **Open Dynamics:** On your track strip in the Fairlight Mixer, double-click the **Dynamics** box (located just above or below the EQ box).
2. **Enable Compressor:** Click the **Compressor** toggle switch to turn it on (it will highlight yellow/orange).
3. **Set Ratio:** Adjust the **Ratio** knob or type in `3.0` (or `4.0` for punchier control).
4. **Set Attack & Release:**
* Set **Attack** to `10 ms` (fast enough to catch loud peaks, slow enough to preserve natural word punch).
* Set **Release** to `100 ms` (smoothly fades back to normal without creating an unnatural "pumping" sound).


5. **Adjust Threshold while Listening:** Play your audio track. Lower the **Threshold** knob down toward `-18 dB` to `-20 dB`.
* Watch the **Gain Reduction (GR)** meter.
* Aim for the GR meter to tick down by **-2 dB to -5 dB** during your louder spoken words or notes. If it never moves, lower the threshold further; if it stays pinned down constantly, raise the threshold.

<img width="1199" height="966" alt="image" src="https://github.com/user-attachments/assets/fa56faf2-b9a1-4357-8b8c-8f4f7390af6d" />

Your setup is **100% correct** and perfectly matches all required compression parameters.

**Verification Breakdown:**

* **Compressor Status:** **ON** (red indicator illuminated above the section).
* **Threshold:** Set to **-20.0 dB** (ideal spot for catching loud spoken peaks).
* **Ratio:** Set to **3.0:1** (provides smooth, natural volume control).
* **Attack:** Set to **10 ms** (preserves initial word clarity before compressing).
* **Release:** Set to **100 ms** (recovers smoothly without volume pumping).
* **Mix:** Set to **100** (fully applying the compressed audio to your track).
* **Expander/Gate & Limiter:** Correctly left **OFF**.

You can see the green dots on the transfer graph displaying your live audio passing right through the compression threshold. Your vocal track is now set up with both proper EQ and smooth compression.

For singing, reverb needs to sound smooth, expansive, and flattering without muddying up the vocal tone or drowning out the words.

Here are the ideal settings to apply in the Fairlight Reverb panel:

---

### Recommended Settings for Singing

* **Preset:** Change top preset from *Small Theatre* to **Plate** or **Medium Hall** (provides a classic, silky vocal trailing sound).
* **Reverb Time:** Set between **1.20 s and 1.80 s** (gives a smooth, musical tail instead of cutting off abruptly at 286 ms).
* **Pre-Delay:** Set to **30 ms – 50 ms** (delays the onset of reverb slightly so the lead voice stays crisp and upfront before the echo fills in).
* **Dry/Wet:** Set to **8.00% – 12.00%** (blends enough effect to make the voice sound rich without hiding it in the background).
* **Brightness:** Set around **50% – 60%** (keeps the reverb tail warm rather than harsh or metallic).

---

### Step-by-Step Adjustments on Your Current Screen

1. Turn the **Reverb Time** knob up from **286 ms** to around **1.50 s (1500 ms)**.
2. Turn the **Pre-Delay** knob up from **20** to **35 ms**.
3. Keep **Dry/Wet** around **8.00% to 10.00%** (adjust to taste—less for subtle polish, more for dramatic ballads).
4. Under **Reverb Tone**, lower **Hi Gain** slightly to **-3.0 dB** to prevent harsh sibilance (*S* and *T* sounds) from ringing out in the reverb.

<img width="1277" height="984" alt="image" src="https://github.com/user-attachments/assets/0c74e51c-be9f-43f3-b861-44680f0b653a" />

Your reverb settings are **spot on for singing**! Everything aligns with a high-quality vocal production chain.

---

### Verification Checklist

* **Preset:** **Plate*** (Ideal choice for smooth, classic vocal reverberation).
* **Pre-Delay:** **30 ms** (Leaves space for the lead vocals to stay crisp and up-front).
* **Reverb Time:** **1500 ms (1.5 s)** (Creates a rich, musical decay tail).
* **Brightness:** **58.81%** (Keeps the vocal tail warm and natural).
* **Hi Gain (Reverb Tone):** **-3.0 dB** (Prevents harsh *S* and *T* sibilance from cluttering the tail).
* **Dry/Wet:** **10.00%** (Sits right in the sweet spot for a lush vocal blend).

---

### Final Mixing Tip

Play your song with the backing music turned on. If the singing feels a bit too far away in the mix, nudge **Dry/Wet** down to **8.00%**. If you want a more dramatic, atmospheric ballad feel, bump it up to **12.00%**.

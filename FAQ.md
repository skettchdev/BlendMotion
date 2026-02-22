# FAQ — BlendMotion

> **Frequently Asked Questions**  
> Can't find your answer? Email us at [skettch.dev@gmail.com](mailto:skettch.dev@gmail.com)

---

## Getting Started

### What is BlendMotion?

BlendMotion turns your iPhone into a real-time 6DoF (6 Degrees of Freedom) camera controller for Blender. Hold your phone, move it around, and the Blender camera follows your motion instantly over Wi-Fi.

### What do I need to use BlendMotion?

- **iPhone 6S or newer** (any ARKit-capable device)
- **iOS 12.0 or later**
- **Blender 4.0+** on your computer (Windows, macOS, or Linux)
- **Same Wi-Fi network** for both devices
- The BlendMotion Blender addon (available on Blender Market)

### How do I install the Blender addon?

1. Purchase the addon from [Blender Market](https://blendermarket.com/products/blendmotion)
2. Download the `.zip` file
3. In Blender, go to `Edit → Preferences → Add-ons → Install`
4. Select the zip file and enable it
5. Find the panel in `3D Viewport → Sidebar (N key) → BlendMotion` tab

### How do I find my computer's IP address?

| OS | Steps |
|---|---|
| **Mac** | System Settings → Wi-Fi → Details → IP Address |
| **Windows** | Open CMD → type `ipconfig` → look for "IPv4 Address" |
| **Linux** | Open terminal → type `ip addr` or `hostname -I` |

Your IP will look something like `192.168.1.xxx`.

---

## Usage

### How do I connect my iPhone to Blender?

1. In Blender, open the BlendMotion panel and click **Start**
2. On your iPhone, enter your computer's IP address and the port (default: `9090`)
3. Tap **Connect**
4. The Blender panel will show "Connected" with your phone's IP

### How should I hold my phone?

Hold your iPhone in **landscape orientation** (sideways, with the home button or notch on the right). This matches the natural camera orientation and gives the best ARKit tracking results.

### What does Sensitivity do?

**Sensitivity** controls how much the Blender camera rotates relative to your phone movement. A value of `1.0` means 1:1 tracking. Higher values amplify rotation — useful for small desk movements. Lower values smooth things out for larger gestures.

### What does Position Scale do?

**Position Scale** multiplies your physical movement in Blender space. The default is `5.0`, meaning moving your phone 1 meter moves the camera 5 meters in Blender. Increase it for large scenes, decrease it for tabletop-scale work.

### What does Smoothing do?

**Smoothing** reduces hand shake and creates more cinematic camera motion.

| Value | Effect |
|---|---|
| `0.0` | No smoothing — raw, direct tracking |
| `0.3–0.5` | Recommended for most use cases |
| `0.7–0.9` | Very smooth, but adds noticeable lag |

### How do I record camera animation?

Tap the **Record** button on your iPhone. BlendMotion will automatically insert keyframes on every frame in Blender. Tap **Stop** when done. Your animation will be saved on the Blender timeline — ready to render or edit.

### What does Recalibrate do?

**Recalibrate** resets the origin point. Your current phone position becomes the new "zero" — the camera stays where it is, and all future movements are calculated relative to this new position. Use this if the camera drifts or jumps unexpectedly.

---

## Troubleshooting

### The camera isn't moving in Blender

Check the following:

- Both devices are on the **same Wi-Fi network** (not one on Wi-Fi and one on mobile data)
- The **IP address** entered in the app is correct
- Your **firewall** is not blocking UDP port `9090`
- The Blender panel shows **"Connected"** (not just "Listening")
- There is an **active camera** in your Blender scene

### The tracking says "Low features" or "Initializing"

ARKit needs visual features to track spatial position. Try:

- Make sure the room has **good lighting**
- Point the camera at a **textured surface** with contrast — not a plain white wall
- Move the phone **slowly** at first to let ARKit build its map
- Avoid **highly reflective** surfaces (glass, mirrors, glossy floors)

### The camera movement feels wrong or reversed

- Make sure you're holding the phone in **landscape orientation**
- The app is designed for **landscape-right** mode (home button / notch on the right)
- If the camera drifts over time, tap **Recalibrate** in Blender

### There's noticeable lag between movement and Blender

- Switch to a **5GHz Wi-Fi** network (2.4GHz is slower and more congested)
- Lower **Smoothing** to `0.0–0.2`
- Keep both devices **close to the router**
- Avoid network congestion — pause large downloads or streams

### Can I use a different port than 9090?

Yes. Change the port number in both the Blender panel and the iPhone app to any value between `1024` and `65535`. Make sure your firewall allows UDP traffic on that port.

---

## General

### Does BlendMotion work with iPad?

iPad support is planned for a future update. Currently BlendMotion is **iPhone only**.

### Does it work with Maya, Cinema 4D, or other 3D software?

Currently BlendMotion only supports **Blender 4.0+**. Support for other software may be added in future versions.

### Is BlendMotion free?

The iPhone app is **$2.99** on the App Store. The Blender addon is **$2.99** on Blender Market *(limited-time launch price — regular price will be $8.88)*.

### Does BlendMotion collect my data?

No. BlendMotion does not collect, store, or transmit any personal data. Camera tracking data stays entirely on your local network and is never sent to any external server. See the full [Privacy Policy](PRIVACY_POLICY.md).

### I'm on the alpha — what should I expect?

BlendMotion v1.0.0-Alpha is pre-release software. Core functionality works, but you may encounter bugs, performance issues, or missing features. Your feedback directly shapes the development. Please report any issues to [skettch.dev@gmail.com](mailto:skettch.dev@gmail.com).

### How do I contact support?

📧 [skettch.dev@gmail.com](mailto:skettch.dev@gmail.com)  
We typically respond within 24–48 hours.

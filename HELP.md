# Usage Guide — BlendMotion

> Full documentation for BlendMotion v1.0.0-Alpha  
> For quick answers, see [FAQ.md](FAQ.md)

---

## Table of Contents

1. [Overview](#overview)
2. [Setup](#setup)
3. [The Blender Addon Panel](#the-blender-addon-panel)
4. [The iPhone App](#the-iphone-app)
5. [Recording Camera Animation](#recording-camera-animation)
6. [Tips for Best Results](#tips-for-best-results)
7. [Firewall Setup](#firewall-setup)
8. [Known Limitations](#known-limitations)

---

## Overview

BlendMotion has two components that work together:

- **iOS App** — Captures real-time 6DoF pose data from ARKit and streams it over UDP
- **Blender Addon** — Listens for UDP packets and applies the received position/rotation to a camera object

Data flows in one direction: **iPhone → Blender**. No internet connection is required. Everything stays on your local network.

---

## Setup

### Step 1 — Install the Blender Addon

1. Purchase the addon from [Blender Market](https://blendermarket.com/products/blendmotion)
2. In Blender, go to `Edit → Preferences → Add-ons`
3. Click **Install** (top right)
4. Select the downloaded `.zip` file
5. Check the checkbox next to **BlendMotion** to enable it
6. The panel is now available at: `3D Viewport → Sidebar → BlendMotion` tab *(press `N` to open the sidebar)*

### Step 2 — Find Your Computer's IP Address

BlendMotion communicates over your local Wi-Fi network. You need to enter your computer's **local** IP address in the iPhone app.

**Mac:**
```
System Settings → Wi-Fi → (click your network) → Details → IP Address
```

**Windows:**
```
Start → CMD → ipconfig
Look for: "IPv4 Address . . . . . . : 192.168.x.xxx"
```

**Linux:**
```bash
ip addr show
# or
hostname -I
```

Your local IP will look like `192.168.1.xxx` or `10.0.0.xxx`. Do **not** use `127.0.0.1` (that's localhost — your iPhone can't reach it).

### Step 3 — Start Blender Listening

1. In the BlendMotion panel, confirm the **Port** (default: `9090`)
2. Select the camera object you want to control in the **Camera** field (or leave blank to use the active scene camera)
3. Click **▶ Start**
4. The status indicator should show **"Listening on port 9090..."**

### Step 4 — Connect the iPhone App

1. Open **BlendMotion** on your iPhone
2. Enter your computer's **IP address**
3. Enter the **Port** (must match Blender — default `9090`)
4. Tap **Connect**
5. The Blender panel status changes to **"Connected"** and shows the iPhone's IP

You're now connected. Hold your phone and move it — the Blender camera follows in real time.

---

## The Blender Addon Panel

Located in: `3D Viewport → Sidebar (N) → BlendMotion`

### Connection

| Control | Description |
|---|---|
| **Port** | UDP port to listen on. Default: `9090`. Must match the iPhone app. |
| **Camera** | The camera object to control. Defaults to the active scene camera. |
| **Start / Stop** | Start or stop listening for incoming data. |
| **Status** | Shows current connection state (Idle / Listening / Connected). |

### Motion Settings

| Parameter | Default | Range | Description |
|---|---|---|---|
| **Position Scale** | `5.0` | `0.1 – 50.0` | Multiplies physical movement. 1m phone movement = Scale × 1m in Blender. |
| **Sensitivity** | `1.0` | `0.1 – 5.0` | Rotation amplifier. 1.0 = 1:1. Higher = more responsive. |
| **Smoothing** | `0.3` | `0.0 – 0.95` | Low-pass filter for movement. 0 = raw, higher = smoother but laggier. |

### Controls

| Control | Description |
|---|---|
| **Recalibrate** | Resets the origin to your current phone position/rotation. Use if the camera drifts or jumps. |
| **Reset Camera** | Returns the camera to its original transform (before BlendMotion moved it). |

---

## The iPhone App

### Connection Screen

Enter the **IP Address** and **Port** of your computer running Blender, then tap **Connect**.

### Live Screen

Once connected, the app shows live ARKit tracking data (position XYZ, rotation).

| Button | Description |
|---|---|
| **Record** | Start recording — keyframes are inserted in Blender on every frame |
| **Stop** | Stop recording — animation is preserved on the Blender timeline |
| **Recalibrate** | Same as Blender's Recalibrate — resets the origin point |
| **Disconnect** | Stops streaming and disconnects |

### Holding Your Phone

Hold your iPhone in **landscape orientation** with the home button (or notch) on the **right side**. This is the reference orientation that BlendMotion uses to map ARKit's coordinate space to Blender's.

---

## Recording Camera Animation

BlendMotion integrates with Blender's keyframe system for recording:

1. Set up your Blender scene and timeline
2. Connect your iPhone to Blender
3. Position your camera where you want the animation to start
4. Click **Recalibrate** to set the origin
5. Press **Record** on your iPhone
6. Move your phone to create the camera move
7. Press **Stop** when done

Keyframes are inserted automatically on every frame at Blender's current FPS setting. The resulting animation is fully editable in the **Graph Editor** and **Dope Sheet** — smooth it, adjust timing, or mix with other animation data.

---

## Tips for Best Results

### For Smoother Tracking

- Start with **Smoothing at 0.3–0.5** — reduces hand tremor without too much lag
- Move the phone **deliberately** — slow, intentional movements track much better than fast flicks
- Let ARKit **initialize for 2–3 seconds** before recording (look around slowly at first)

### For Better ARKit Accuracy

- **Good lighting** is the single biggest factor — brightly and evenly lit rooms track much better
- Aim at **textured surfaces** — walls with pictures, bookshelves, furniture, etc.
- Avoid **plain white walls**, **dark rooms**, and **highly reflective** surfaces (glass tables, mirrors)
- Don't cover the **rear camera** with your fingers

### For Network Performance

- Use **5GHz Wi-Fi** — it's less congested and has lower latency than 2.4GHz
- Keep your phone and computer **on the same router** (not a mesh extender)
- Pause large downloads or video streams while recording

### Matching Scale to Your Scene

- **Architecture / large environments:** Position Scale `10–20`
- **Character animation / medium scenes:** Position Scale `3–7` (default range)
- **Product shots / tabletop work:** Position Scale `0.5–2`

---

## Firewall Setup

BlendMotion uses **UDP** on port `9090` (or your custom port). You may need to allow this through your firewall.

**Windows Defender Firewall:**
1. Search for "Windows Defender Firewall with Advanced Security"
2. Click **Inbound Rules → New Rule**
3. Select **Port → UDP → Specific local port:** `9090`
4. Select **Allow the connection**
5. Apply to all profiles and give it a name (e.g. `BlendMotion`)

**macOS:**
macOS generally doesn't block UDP by default. If you have third-party firewall software, allow UDP on port `9090` for the Python/Blender process.

**Linux:**
```bash
sudo ufw allow 9090/udp
```

---

## Known Limitations (Alpha)

- **iPhone only** — iPad not yet supported
- **Blender 4.0+ only** — no support for older versions or other 3D software
- **ARKit drift** — long sessions may show position drift; use Recalibrate to reset
- **Single camera only** — cannot control multiple cameras simultaneously
- **No offline recording** — must be connected to Blender while recording
- May not work reliably over **VPN** or **hotspot** connections

---

## Support

If you run into issues not covered here, please email us:

📧 [skettch.dev@gmail.com](mailto:skettch.dev@gmail.com)

Include your **iPhone model**, **iOS version**, **Blender version**, and a short description of the problem. We typically respond within 24–48 hours.

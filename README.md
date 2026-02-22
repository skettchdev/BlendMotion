[README.md](https://github.com/user-attachments/files/25471674/README.2.md)
# BlendMotion 📷

**Turn your iPhone into a real-time camera controller for Blender.**

BlendMotion uses Apple ARKit to stream 6DoF (6 Degrees of Freedom) camera motion from your iPhone to Blender over Wi-Fi — wirelessly, with no cables or mocap equipment.

> ⚠️ **Alpha Release (v1.0.0-Alpha)** — Core functionality is working, but expect rough edges. Bug reports and feedback are very welcome!

---

## Demo

*Coming soon — GIF/video of BlendMotion in action*

---

## How It Works

1. The **iOS app** captures your iPhone's position and rotation using ARKit
2. Data is streamed wirelessly over **UDP** to your computer
3. The **Blender addon** receives the data and drives your scene camera in real time
4. Optionally **record keyframes** to capture camera animation

---

## Requirements

| | Minimum |
|---|---|
| **iPhone** | iPhone 6S or newer (ARKit capable) |
| **iOS** | 12.0 or later |
| **Blender** | 4.0 or later |
| **Network** | Both devices on the same Wi-Fi network |

---

## Installation

### 1. iOS App

Download **BlendMotion** from the [App Store](#) — **$2.99**

### 2. Blender Addon

1. Purchase the addon from [Blender Market](https://blendermarket.com/products/blendmotion) — **$2.99** *(launch price — regular $8.88)*
2. In Blender: `Edit → Preferences → Add-ons → Install`
3. Select the downloaded `.zip` file and enable **BlendMotion**
4. Open the panel: `3D Viewport → Sidebar (N) → BlendMotion tab`

---

## Quick Start

1. Open Blender, go to the **BlendMotion panel** and click **Start**
2. Find your computer's local IP address (`ipconfig` on Windows, `System Settings → Wi-Fi` on Mac)
3. In the iPhone app, enter the **IP address** and tap **Connect**
4. Hold your phone in **landscape orientation** and move — the camera follows!
5. Tap **Record** to capture keyframes

---

## Parameters

| Parameter | Default | Description |
|---|---|---|
| **Port** | `9090` | UDP port — must match on both devices |
| **Sensitivity** | `1.0` | Rotation multiplier. Higher = more responsive |
| **Position Scale** | `5.0` | Movement multiplier. 1m phone = 5m in Blender |
| **Smoothing** | `0.3` | Hand-shake reduction. 0 = raw, 0.9 = very smooth |

---

## Coordinate System

ARKit and Blender use different axes. BlendMotion handles the conversion automatically:

| ARKit | Blender |
|---|---|
| +X (right) | +X (right) |
| +Y (up) | +Z (up) |
| -Z (forward) | +Y (forward) |

Rotation is transmitted as **quaternions** to avoid gimbal lock and converted to Blender's native format on arrival.

---

## Network Protocol

Lightweight UDP packets — **32 bytes per frame** at up to **60 Hz**:

```
[timestamp: float32]
[pos_x: float32] [pos_y: float32] [pos_z: float32]
[quat_w: float32] [quat_x: float32] [quat_y: float32] [quat_z: float32]
```

No data leaves your local network. No servers, no cloud.

---

## Troubleshooting

**Camera not moving?**
- Make sure both devices are on the **same Wi-Fi network**
- Check the IP address is correct
- Make sure the firewall isn't blocking **UDP port 9090**
- Verify Blender panel shows **"Connected"**

**Tracking says "Initializing"?**
- Point the camera at a **textured surface** (not a blank wall)
- Ensure **good lighting**
- Move the phone **slowly** at first

**Too much lag?**
- Use **5GHz Wi-Fi** instead of 2.4GHz
- Lower **Smoothing** to 0.0–0.2
- Reduce network congestion

See [FAQ.md](FAQ.md) for more.

---

## Roadmap

- [ ] iPad support
- [ ] Android support
- [ ] Support for Maya, Cinema 4D, Unreal Engine
- [ ] Face tracking / head tracking mode
- [ ] Multi-device tracking

---

## Privacy

BlendMotion collects **no personal data**. All tracking data stays on your local network and is never sent to any server. See [PRIVACY_POLICY.md](PRIVACY_POLICY.md).

---

## Contact & Support

📧 [skettch.dev@gmail.com](mailto:skettch.dev@gmail.com)  
🛒 [Blender Market](https://blendermarket.com/products/blendmotion)

We typically respond within 24–48 hours.

---

## License

See [LICENSE](LICENSE) for details.

---

*BlendMotion is not affiliated with or endorsed by the Blender Foundation or Apple Inc.*  
*"Blender" is a registered trademark of the Blender Foundation. "ARKit", "iPhone", "App Store" are trademarks of Apple Inc.*

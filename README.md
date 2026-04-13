[README.md](https://github.com/user-attachments/files/26674216/README.md)
# BlendMotion — Real-time ARKit Camera Tracking for Blender

> Turn your iPhone into a 6DoF camera controller for Blender.

BlendMotion captures real-time motion data from your iPhone's ARKit sensors and streams it to Blender over Wi-Fi, giving you natural, handheld camera movement for your 3D scenes.

## Requirements

| Component | Minimum |
|-----------|---------|
| **iPhone** | iPhone XS or newer |
| **iOS** | 17.0 or later |
| **Blender** | 4.0 or later |
| **Network** | Both devices on the same Wi-Fi network |

The BlendMotion iOS app is available separately on the [App Store](https://apps.apple.com/app/blendmotion).

## Installation

1. Download the latest addon `.zip` from [GitHub Releases](https://github.com/skettchdev/BlendMotion/releases)
2. In Blender, go to **Edit → Preferences → Add-ons → Install**
3. Select the downloaded `.zip` file
4. Enable the addon by checking the box next to **BlendMotion**
5. The panel appears in **View3D → Sidebar (N key) → BlendMotion** tab

> **Note:** Install the `.zip` file directly — do not extract it first.

## Quick Start

1. **Check Preflight** — Open the BlendMotion panel. The Preflight Checklist verifies your IP address, active camera, port, and scene FPS automatically.
2. **Connect iPhone** — Copy the IP address shown in the checklist, enter it in the BlendMotion iOS app, and tap Connect. The app remembers your last-used IP address.
3. **Start Tracking** — Click **Start** in the Blender panel. Hold your iPhone in landscape and move it to control the camera.
4. **Record** — Tap the Rec button on your iPhone to capture keyframes on the Blender timeline.
5. **Stop & Render** — Click **Stop** when finished. Your camera animation is ready to render.

## Features

- **Real-time 6DoF tracking** — Position and rotation streamed at 60 fps over UDP
- **Viewport preview** — Live Blender viewport streamed to iPhone at 24 FPS so you can see what the camera sees
- **Motion presets** — Handheld, Cinematic, Dolly, Crane, and Raw modes
- **Parent-aware tracking** — Works correctly with parented cameras and rigs
- **Retake** — Delete recorded keyframes and rewind the timeline with one tap
- **Pause / Resume / Reset** — Pause tracking mid-session, resume with auto-recalibration, or reset camera to start position
- **On-device controls** — Adjust Sensitivity, Position Scale, and Record FPS directly from the iPhone
- **Smooth Keyframes** — Post-processing to clean up recorded animation curves
- **Bake to World** — Convert parented animation to world-space keyframes
- **Preflight Checklist** — Automatic verification of network, camera, and scene settings
- **IP persistence** — iPhone remembers the last-used IP address

## Troubleshooting

- **Can't connect?** Ensure both devices are on the same Wi-Fi network. Use a 5 GHz network if available. Check that no firewall is blocking UDP port 9090.
- **Laggy movement?** Close other heavy Blender addons during tracking. Disable viewport overlays you don't need.
- **No active camera?** Add a camera with `Shift+A → Camera` and press `Ctrl+Numpad 0` to set it as active.

## Support

- **Documentation:** [skettchdev.github.io/BlendMotion](https://skettchdev.github.io/BlendMotion)
- **Email:** [skettchdev@gmail.com](mailto:skettchdev@gmail.com)

## License

BlendMotion Blender Addon is licensed under the [GNU General Public License v3.0](https://www.gnu.org/licenses/gpl-3.0.html).

© 2026 Skettch

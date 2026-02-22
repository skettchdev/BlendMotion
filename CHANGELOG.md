# Changelog — BlendMotion

All notable changes to BlendMotion will be documented here.

Format follows [Keep a Changelog](https://keepachangelog.com/en/1.0.0/).  
Versioning follows [Semantic Versioning](https://semver.org/).

---

## [1.0.0-Alpha] — 2026-02-22

### 🎉 Initial Alpha Release

This is the first public release of BlendMotion. Core functionality is working end-to-end. Expect rough edges — this is alpha software.

### Added

**iOS App**
- Real-time 6DoF camera tracking using Apple ARKit
- UDP streaming of position (X, Y, Z) and rotation (quaternion) at up to 60 Hz
- Connect/Disconnect to any local IP address and port
- Live tracking status display (position + rotation values)
- Record / Stop recording — triggers keyframe insertion in Blender
- Recalibrate button — resets origin point to current pose
- Landscape orientation support

**Blender Addon**
- UDP listener running as a background modal operator
- Real-time camera object transform updates from iPhone data
- ARKit → Blender coordinate system conversion (automatic)
- Quaternion → Euler rotation conversion (automatic)
- Configurable parameters: Port, Position Scale, Sensitivity, Smoothing
- Start / Stop controls with connection status indicator
- Recalibrate operator — resets origin offset
- Reset Camera operator — returns camera to original transform
- Compatible with Blender 4.0+

### Known Issues

- ARKit position may drift during long sessions — use Recalibrate to reset
- Tracking quality degrades in low-light or low-texture environments
- No iPad support yet
- Only supports Blender 4.0+ (no older versions)
- Does not work reliably over VPN or mobile hotspot connections
- Single camera control only (no multi-camera support)

---

## Upcoming

### [1.1.0] — Planned

- [ ] iPad support
- [ ] Improved ARKit drift compensation
- [ ] Connection stability improvements
- [ ] In-app tutorial / onboarding

### [1.2.0] — Planned

- [ ] Android support
- [ ] Adjustable send rate (30 / 60 / 120 Hz)
- [ ] Camera path preview in Blender viewport

### [Future]

- [ ] Support for Maya, Cinema 4D, Unreal Engine
- [ ] Face tracking / head tracking mode
- [ ] Multi-device tracking

---

> Have a bug to report or a feature to suggest?  
> 📧 [skettch.dev@gmail.com](mailto:skettch.dev@gmail.com)

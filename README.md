# MPV Player Configuration Profiles

A comprehensive collection of MPV player configurations optimized for different hardware capabilities and use cases.

## Table of Contents
1. [Quick Installation](#quick-installation)
2. [Profile Selection Guide](#profile-selection-guide)
3. [Configuration Profiles](#configuration-profiles)
   - [Low Quality Software](#low-quality-software-profile)
   - [Low Quality Hardware](#low-quality-hardware-profile)
   - [High Quality](#high-quality-profile)
   - [High Quality with Interpolation](#high-quality--interpolation-profile)
   - [Ultra High Quality](#ultra-high-quality-profile)
4. [Advanced Features](#advanced-features)
5. [Troubleshooting](#troubleshooting)

## Quick Installation
```batch
# Windows
mkdir %APPDATA%\mpv
copy mpv.conf %APPDATA%\mpv\
copy input.conf %APPDATA%\mpv\
```

## Profile Selection Guide
Choose your profile based on your hardware:
- Ancient/Low-end PC → Low Quality SW
- Basic GPU → Low Quality HW
- Modern GPU → High Quality
- Gaming/High-end PC → High Quality + Interpolation
- Custom Experience → Ultra High Quality

## Configuration Profiles

### Low Quality Software Profile
**Purpose:** Maximum compatibility and performance on very old or limited hardware
**Location:** `/low quality sw/mpv.conf`

```properties
hwdec=no          # Forces CPU decoding
profile=fast      # Maximum performance focus
save-position-on-quit
fs                # Start in fullscreen
```

**Best For:**
- Very old computers
- Systems without GPU
- Troubleshooting compatibility issues
- Minimal resource usage

### Low Quality Hardware Profile
**Purpose:** Basic hardware acceleration for older GPUs
**Location:** `/low quality hw/mpv.conf`

```properties
vo=gpu            # GPU-based video output
hwdec=auto-safe   # Hardware decoding with fallback
profile=fast      # Performance-oriented settings
save-position-on-quit
fs
```

**Optional Vulkan Enhancement:**
```properties
gpu-api=vulkan    # Enable for compatible GPUs
hwdec=vulkan      # Vulkan-based decoding
```

### High Quality Profile
**Purpose:** Quality-focused playback for modern systems
**Location:** `/high quality without interpolation/mpv.conf`

```properties
vo=gpu-next       # Modern GPU renderer
hwdec=auto-safe   # Hardware decoding
profile=gpu-hq    # High quality preset
scale=ewa_lanczos4sharpest    # Superior scaling
cscale=ewa_lanczos4sharpest   # Chroma scaling
dscale=ewa_lanczos4sharpest   # Downscaling
correct-downscaling=yes       # Prevent detail loss
deband=yes        # Remove color banding
deinterlace=auto  # Handle interlaced content
```

### High Quality + Interpolation Profile
**Purpose:** Smooth motion playback for high-end systems
**Location:** `/high quality with interpolation/mpv.conf`

```properties
vo=gpu-next       # Modern renderer
hwdec=auto-safe   # Hardware decoding
profile=gpu-hq    # Quality preset
scale=ewa_lanczos4sharpest    # Quality scaling
cscale=ewa_lanczos4sharpest   # Color scaling
interpolation=yes             # Frame interpolation
tscale=oversample            # Temporal scaling
video-sync=display-resample  # Smooth playback
deband=yes                   # Remove banding
```

### Ultra High Quality Profile
**Purpose:** Maximum quality with custom enhancements
**Location:** `/actual personal configuration/mpv.conf`

```properties
vo=gpu-next       # Modern renderer
gpu-api=vulkan    # Vulkan API
hwdec=auto-safe   # Hardware decode
profile=gpu-hq    # Quality preset
scale=ewa_lanczos4sharpest    # All scaling set to highest
cscale=ewa_lanczos4sharpest
dscale=ewa_lanczos4sharpest
correct-downscaling=yes
deband=yes        # Remove banding
deinterlace=no    # No deinterlacing
saturation=50     # Enhanced colors
brightness=10     # Increased brightness
```

## Advanced Features

### Custom Controls
**Location:** `/input.conf`
```properties
# Sharpness control (Only for vo=gpu)
Ctrl+2 add sharpen +0.100    # Increase sharpness
Ctrl+1 add sharpen -0.100    # Decrease sharpness
```

### Performance Impact Guide

| Feature | GPU Load | CPU Load | Quality Impact |
|---------|----------|----------|----------------|
| Basic Scaling | 1-2% | Minimal | Low |
| Lanczos Scaling | 5-10% | Low | High |
| Interpolation | 15-30% | Medium | Very High |
| HDR Processing | 5-15% | Low | High |

## Troubleshooting

### Common Issues & Solutions
1. **High CPU Usage**
   - Enable hardware decoding
   - Use lighter scaling
   - Disable interpolation

2. **Video Stuttering**
   - Try different `vo` settings
   - Disable interpolation
   - Lower scaling quality

3. **Quality Issues**
   - Check hardware decode support
   - Update GPU drivers
   - Adjust scaling options

### Performance Monitoring
Press `Shift+I` while playing to show:
- Frame timing
- Hardware decode status
- GPU/CPU load
- Dropped frames

Remember: Start with the profile matching your hardware and adjust settings based on performance and quality needs.

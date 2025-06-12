# MPV Player Configuration Profiles

A collection of optimized MPV player configurations for different hardware capabilities and use cases.

## Quick Start Guide

1. Choose your profile based on your hardware:
   - Ancient/Low-end PC → Low Quality SW
   - Basic GPU → Low Quality HW
   - Modern GPU → High Quality
   - Gaming/High-end PC → High Quality + Interpolation

2. Installation:
   ```batch
   # Windows
   mkdir %APPDATA%\mpv
   copy mpv.conf %APPDATA%\mpv\
   copy input.conf %APPDATA%\mpv\
   ```

## Configuration Profiles

### 1. Low Quality Software (SW) Profile
Best for: Very old computers, compatibility testing
```properties
hwdec=no          # CPU decoding
profile=fast      # Maximum performance
```

**Minimum Requirements:**
- Any CPU (even single core)
- 2GB RAM
- No GPU needed

### 2. Low Quality Hardware (HW) Profile
Best for: Basic laptops, older computers with GPU
```properties
vo=gpu            # GPU rendering
hwdec=auto-safe   # Hardware decoding
profile=fast      # Performance focus
```

**Minimum Requirements:**
- Dual-core CPU
- 2GB RAM
- Basic GPU (Intel HD 4000+)

### 3. High Quality Profile
Best for: Modern computers, quality-focused playback
```properties
vo=gpu-next       # Modern renderer
hwdec=auto-safe   # Hardware decoding
profile=gpu-hq    # High quality
scale=ewa_lanczos4sharpest
correct-downscaling=yes
```

### 4. High Quality + Interpolation
Best for: High-end systems, smooth motion
```properties
vo=gpu-next
interpolation=yes
tscale=oversample
video-sync=display-resample
```

## Advanced Features Explained

### 1. Scaling Quality Levels
From lowest to highest quality:

1. **Basic (Low-end):**
   ```properties
   scale=bilinear
   cscale=bilinear
   ```
   - Minimal GPU load
   - Acceptable for SD content

2. **Balanced (Mid-range):**
   ```properties
   scale=spline36
   cscale=spline36
   ```
   - Good quality/performance ratio
   - Recommended for 1080p

3. **Maximum (High-end):**
   ```properties
   scale=ewa_lanczos4sharpest
   cscale=ewa_lanczos4sharpest
   correct-downscaling=yes
   ```
   - Best possible quality
   - Heavy GPU load
   - Great for 4K content

### 2. Hardware Decoding Options

1. **Software Decoding (`hwdec=no`):**
   - Uses CPU only
   - Maximum compatibility
   - Highest CPU usage

2. **Hardware Decoding (`hwdec=auto-safe`):**
   - Automatic GPU selection
   - Supports: H.264, H.265, VP9, AV1
   - Lower CPU usage

3. **Vulkan Decoding:**
   ```properties
   gpu-api=vulkan
   hwdec=vulkan
   ```
   - Best performance on modern GPUs
   - Requires Vulkan 1.1+ support

### 3. Performance Impact Guide

| Feature | GPU Load | CPU Load | Quality Impact |
|---------|----------|----------|----------------|
| Basic Scaling | 1-2% | Minimal | Low |
| Lanczos Scaling | 5-10% | Low | High |
| Interpolation | 15-30% | Medium | Very High |
| HDR Processing | 5-15% | Low | High |

## Troubleshooting

### Common Issues & Solutions

1. **High CPU Usage**
   - Switch to hardware decoding
   - Use a lighter scaling method
   - Disable interpolation

2. **Stuttering**
   - Try different `vo` settings
   - Disable interpolation
   - Lower scaling quality

3. **Quality Problems**
   - Verify hardware decoding support
   - Check GPU driver updates
   - Adjust scaling settings

## Performance Monitoring
Press `I` while playing to show:
- Frame timing
- Hardware decode status
- GPU/CPU load
- Dropped frames

Remember: Start with the profile matching your hardware, then adjust settings as needed.

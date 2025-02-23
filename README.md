# MPV Player Configuration Repository 🎥

Welcome to the **MPV Player Configuration Repository**! This repository contains a collection of configuration files (`mpv.conf`) and input bindings (`input.conf`) for the MPV media player, organized into four distinct folders based on different performance and quality needs. Whether you're aiming for the highest video quality, balanced performance, or low-resource usage, this repository has the right configuration for you.

## Folder Structure 📂

The repository is organized into four folders, each containing a specific configuration tailored to different use cases:

### 1. **High Quality with Interpolation** 🌟
   - **Folder**: `high-quality-with-interpolation`
   - **Description**: This configuration is designed for users who want the **best visual experience** with smooth video playback. It includes settings for **interpolation** to make motion smoother, along with high-quality rendering and debanding.
   - **Key Features**:
     - `vo=gpu-next` for advanced GPU rendering.
     - `hwdec=auto-safe` for hardware decoding.
     - **Interpolation** enabled for smoother motion (`interpolation=yes`, `tscale=robidouxsharp`, `video-sync=display-resample`).
     - **Debanding** to reduce visual artifacts.
     - Saves playback position and starts in fullscreen mode.

### 2. **High Quality without Interpolation** ⚖️
   - **Folder**: `high-quality-without-interpolation`
   - **Description**: This configuration offers **high-quality video playback** but **disables interpolation** for better performance. It's ideal for users who want great visuals without the extra processing overhead of interpolation.
   - **Key Features**:
     - `vo=gpu-next` for advanced GPU rendering.
     - `hwdec=auto-safe` for hardware decoding.
     - **Interpolation disabled** (commented out in the config).
     - **Debanding** to reduce visual artifacts.
     - Saves playback position and starts in fullscreen mode.

### 3. **Low Quality (Hardware Decoding)** 💻
   - **Folder**: `low-quality-hw`
   - **Description**: This configuration is optimized for **performance** while still using **hardware decoding**. It's perfect for users with mid-range hardware who want a balance between quality and speed.
   - **Key Features**:
     - `vo=gpu` for standard GPU rendering.
     - `hwdec=auto-safe` for hardware decoding.
     - `profile=fast` for optimized performance.
     - **Audio-video synchronization** enabled (`video-sync=audio`).
     - Saves playback position and starts in fullscreen mode.

### 4. **Low Quality (Software Decoding)** 🐢
   - **Folder**: `low-quality-sw`
   - **Description**: This configuration is designed for **low-end systems** or situations where hardware decoding is not available. It relies on **software decoding** and is optimized for minimal resource usage.
   - **Key Features**:
     - `hwdec=no` to disable hardware decoding.
     - `profile=fast` for optimal CPU performance.
     - **Audio-video synchronization** enabled (`video-sync=audio`).
     - Saves playback position and starts in fullscreen mode.

### 5. **Custom Sharpness Controls** 🔍
   - **File**: `input.conf`
   - **Description**: This file provides **keyboard shortcuts** to adjust video sharpness. It's compatible with configurations that use `vo=gpu` (not `gpu-next`).
   - **Key Features**:
     - **Ctrl+1**: Decrease sharpness.
     - **Ctrl+2**: Increase sharpness.

## How to Use These Configurations? 🛠️

1. **Clone the repository** or download the configuration files.
2. Navigate to the folder that matches your desired configuration (e.g., `high-quality-with-interpolation`).
3. Copy the `mpv.conf` and `input.conf` files to your MPV configuration directory:
   - **Linux**: `~/.config/mpv/`
   - **Windows**: `\mpv\`
   - **macOS**: `~/.config/mpv/`
4. Restart MPV to apply the new settings.

## Customization and Contributions 🤝

Feel free to customize these configurations to suit your needs! If you have improvements or additional configurations, contributions are welcome. Just fork the repository, make your changes, and submit a pull request.

## Why Use These Configurations? 🎯

- **High Quality with Interpolation**: Perfect for users who want the **smoothest and most visually stunning** playback experience.
- **High Quality without Interpolation**: Ideal for users who want **great visuals** but prefer **better performance**.
- **Low Quality (Hardware Decoding)**: Great for **mid-range systems** that need a balance between quality and speed.
- **Low Quality (Software Decoding)**: Designed for **low-end systems** or situations where hardware decoding is not available.
- **Custom Sharpness Controls**: Gives you **fine-tuned control** over video sharpness.

**Note**: These configurations are not officially affiliated with the MPV project. They are community-driven and designed to enhance your MPV experience.

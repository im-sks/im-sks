# Video to GIF Conversion Guide

This guide provides step-by-step instructions for converting MP4 videos to GIF format for use in GitHub README files.

## Why Convert to GIF?

GitHub's markdown renderer doesn't support HTML `<video>` tags, but it does support GIF images. Converting your video demonstrations to GIF format ensures they display properly and are accessible to all viewers.

## Optimal GIF Settings for GitHub

- **File size**: Keep under 25MB (GitHub's limit for repository files)
- **Dimensions**: Recommended maximum 800x600 pixels for good performance
- **Frame rate**: 10-15 FPS for good balance between quality and file size
- **Duration**: Keep under 30 seconds when possible
- **Colors**: 256 colors or fewer to reduce file size

## Conversion Methods

### Method 1: Online Tools (Easiest)

#### Using ezgif.com
1. Go to [ezgif.com](https://ezgif.com/video-to-gif)
2. Click "Choose File" and select your MP4 video
3. Click "Upload video!"
4. Adjust settings:
   - **Size**: Resize if needed (recommend max 800px width)
   - **Frame rate**: Set to 10-15 FPS
   - **Start/End time**: Trim if needed
5. Click "Convert to GIF!"
6. Download the generated GIF

#### Using CloudConvert.com
1. Go to [cloudconvert.com](https://cloudconvert.com/mp4-to-gif)
2. Upload your MP4 file
3. Click on the settings icon to adjust options:
   - **Width/Height**: Set maximum dimensions (e.g., 800x600)
   - **FPS**: 10-15 for optimal size
   - **Quality**: Medium to High
4. Click "Start Conversion"
5. Download the result

### Method 2: Command-Line Tools (Advanced)

#### Using FFmpeg
First, install FFmpeg on your system:

**Windows:**
```bash
# Using chocolatey
choco install ffmpeg

# Or download from https://ffmpeg.org/download.html
```

**macOS:**
```bash
# Using Homebrew
brew install ffmpeg
```

**Linux (Ubuntu/Debian):**
```bash
sudo apt update
sudo apt install ffmpeg
```

**Basic conversion:**
```bash
ffmpeg -i "input_video.mp4" -vf "fps=10,scale=800:-1:flags=lanczos" -c:v gif "output.gif"
```

**Advanced conversion with better optimization:**
```bash
ffmpeg -i "input_video.mp4" -vf "fps=10,scale=800:-1:flags=lanczos,split[s0][s1];[s0]palettegen[p];[s1][p]paletteuse" -loop 0 "output.gif"
```

**Parameters explained:**
- `fps=10`: Set frame rate to 10 FPS
- `scale=800:-1`: Resize to 800px width, maintain aspect ratio
- `flags=lanczos`: High-quality scaling algorithm
- `palettegen` and `paletteuse`: Generate optimized color palette

### Method 3: Desktop Applications

#### Using GIMP (Free)
1. Open GIMP
2. Go to **File > Import > Video Frames**
3. Select your MP4 file
4. Choose frame range and select every nth frame (e.g., every 3rd frame for lower FPS)
5. Once imported, go to **File > Export As**
6. Choose GIF format and adjust animation settings
7. Set loop options and optimize for web

#### Using Adobe Photoshop
1. Open Photoshop
2. Go to **File > Import > Video Frames to Layers**
3. Select your MP4 file
4. Choose "Selected Range Only" if you want to trim
5. Limit frames (e.g., every 3 frames for lower FPS)
6. Go to **Window > Timeline** to see animation
7. **File > Export > Save for Web (Legacy)**
8. Choose GIF format and optimize settings

## File Size Optimization Tips

1. **Reduce dimensions**: Smaller videos = smaller file sizes
2. **Lower frame rate**: 10-15 FPS is usually sufficient for demos
3. **Reduce colors**: Use 128-256 colors instead of full color
4. **Trim duration**: Keep only the essential parts of your demo
5. **Crop unnecessary areas**: Focus on the important parts of the screen

## After Conversion

1. **Test the GIF**: Open it in a browser to ensure it plays correctly
2. **Check file size**: Ensure it's under 25MB for GitHub
3. **Upload to your repository**: Add the GIF file to your repo
4. **Update your README**: Replace the `<video>` tag with standard markdown image syntax:

```markdown
![Description of your demo](path/to/your/demo.gif)
```

Or with HTML for more control:
```html
<img src="path/to/your/demo.gif" alt="Description" width="100%" style="max-width:800px"/>
```

## Troubleshooting

- **File too large**: Reduce dimensions, frame rate, or duration
- **Poor quality**: Increase the color palette or frame rate slightly
- **Won't loop**: Ensure loop settings are enabled during conversion
- **Doesn't display on GitHub**: Check file path and ensure GIF is properly uploaded to the repository

---

**Note**: Always keep your original MP4 files as backups, as GIF conversion is lossy and you may need to re-convert with different settings.
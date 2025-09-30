# Pexels Video Generator with Voiceover

A Python script that searches for videos on Pexels based on predefined tags, generates voice narration using Edge TTS, and creates a compiled video with background music.

## Features

- Search for videos on Pexels using predefined tags
- Generate voice narration from text using Microsoft Edge TTS
- Add background music support (up to 3 music files)
- Automatic video processing with fade effects
- Web interface for easy video generation
- Automatic cleanup of temporary files

## Requirements

- Python 3.7+
- Flask
- edge-tts
- requests
- pydub
- FFmpeg (must be installed on your system)

## Installation

1. Clone this repository
2. Install the required packages:
   ```
   pip install flask edge-tts requests pydub
   ```
3. Install FFmpeg on your system:
   - **Windows**: Download from [ffmpeg.org](https://ffmpeg.org/download.html) and add to PATH
   - **macOS**: `brew install ffmpeg`
   - **Linux**: `sudo apt install ffmpeg` (Ubuntu/Debian)

## Configuration

1. Get your Pexels API key from [pexels.com/api](https://www.pexels.com/api/)
2. Replace the placeholder API key in the script:
   ```python
   PEXELS_API_KEY = "your_api_key_here"
   ```
3. Modify the predefined tags if needed:
   ```python
   TAGS_PREDEFINIDOS = ["cosmos", "galaxia", "islam", ...]
   ```

## Usage

1. Run the script:
   ```
   python script_name.py
   ```
2. Open your browser and go to `http://localhost:5000`
3. Enter your text in the text area
4. Select a voice from the dropdown
5. Optionally upload up to 3 music files
6. Click "Generate Video"
7. Wait for the process to complete
8. Download your video when ready

## Video Search Behavior

The script searches for videos based on tags in the following way:

- For each part of the text, it searches for videos using multiple tags
- By default, it searches for up to 25 videos per tag
- If you want to get more videos from a single tag, modify the `max_results` parameter in the `search_videos` function call within `create_video_part`

To get 100 videos from a single tag:
```python
# In create_video_part function
urls = search_videos(tag, max_results=100)
```

## File Structure

```
project/
├── script_name.py       # Main script
├── outputs/             # Generated videos (auto-created)
└── README.md           # This file
```

## API Limits

- Pexels API has a rate limit of 200 requests per hour
- Maximum of 80 videos per page (pagination would be needed for more)
- Videos are automatically deleted after 2 hours

## Troubleshooting

- **FFmpeg not found**: Make sure FFmpeg is installed and added to your system PATH
- **No videos found**: Check your Pexels API key and try different tags
- **Voice generation fails**: Verify your internet connection and try a different voice

## License

This project is for educational purposes. Please respect the Pexels API license terms and the video licenses when using generated content.

# 🎬 TikTok Video Downloader - Direct Links & Downloads

![Sample Output](https://raw.githubusercontent.com/DZ-ABDLHAKIM/tiktok-video-downloader/refs/heads/main/tiktok-scraper-sample-output.png)

Extract direct download links from TikTok videos with complete metadata and automatic video downloads using intelligent resource allocation. Built for content creators, researchers, and businesses who need reliable access to TikTok content without watermarks.

## Key Benefits & Use Cases

### For Researchers & Analysts
- Archive TikTok videos for research and trend analysis
- Extract metadata for social media studies and engagement analytics
- Build datasets with downloadable video files and comprehensive statistics

### For Content Creators & Marketers
- Download competitor content for inspiration and analysis
- Archive your own TikTok videos as backup with full metadata
- Extract engagement metrics and performance data

### For Media & Entertainment
- Archive viral content and trending videos
- Extract video files for editing and repurposing
- Monitor brand mentions and user-generated content

## 🔎 Complete Data Extraction

### Video Intelligence
- **Metadata**: ID, title, description, creation date, duration, dimensions
- **Engagement**: Views, likes, shares, comments count
- **Technical**: File size, quality (540p/720p), FPS selection (30/60)
- **Creator**: Author name, author ID, profile information

### Smart Download System
- **Direct URLs**: Instant access to playable video links without TikTok watermarks
- **Automatic Downloads**: Optional video file downloads with intelligent resource allocation
- **Quality Selection**: Choose between 30 FPS or 60 FPS video quality
- **Memory Optimization**: Dynamic resource calculation based on file size

**Note**: Videos are extracted directly from TikTok's CDN servers, providing clean video files without the standard TikTok watermark overlay that appears in the mobile app.

### Intelligent Resource Management

When video downloads are enabled, the Actor uses smart memory allocation powered by our specialized [Universal File Downloader](https://apify.com/dz_omar/universal-file-downloader) to optimize performance:

**Dynamic Resource Calculation**: Analyzes video file size and allocates optimal memory (128MB to 32GB) and timeout settings automatically.

**Prevents Failures**: Eliminates Out-Of-Memory errors by calculating exact requirements before download.

**Cost Efficient**: Only uses the memory needed for each specific video, preventing resource waste.

## ⚙️ Configuration Options

### 🔗 Input URLs
Process individual TikTok videos or batch multiple URLs:

```json
{
  "videoUrls": [
    "https://www.tiktok.com/@dummyuser/video/7234567890123456789"
  ]
}
```

### 🎞️ Video Quality Selection

**📺 preferredFps** (String)
- Default: "60"
- Options: "30" (Standard) or "60" (Smooth)  
- Use Case: Choose video frame rate based on your needs
- Note: Actor automatically selects best available bitrate within chosen FPS

### ⏱️ Processing Control

**⏰ timeout** (Integer)
- Default: 30
- Range: 10-120 seconds
- Purpose: Maximum time to wait for each video extraction
- Use Case: Adjust based on network conditions and video complexity

## 📊 Sample Output Structure

![Sample Output](https://raw.githubusercontent.com/apifytech/store-assets/master/actors/tiktok-scraper/tiktok-scraper-sample-output.png)


```json
{
  "videoUrl": "https://www.tiktok.com/@dummyuser/video/7234567890123456789",
  "directUrl": "https://v16-webapp-prime.tiktok.com/video/tos/alisg/example-url...",
  "title": "Sample TikTok Video Title",
  "author": "dummyuser",
  "authorId": "1234567890123456789",
	"Cover": "https://p16-pu-sign-no.tiktokcdn-eu.com/tos-no1a-p-0037-no/o0gWBfoTDFe...",
  "duration": 30,
  "viewCount": 1500000,
  "likeCount": 150000,
  "shareCount": 12000,
  "commentCount": 8500,
  "width": 576,
  "height": 1024,
  "quality": "540p",
  "fileSize": "5826163",
  "videoId": "7234567890123456789",
  "extractedAt": "2025-09-20T12:00:00.000Z",
  "download": {
    "available": true,
    "url": "https://api.apify.com/v2/key-value-stores/example-store/records/video.mp4",
    "format": "mp4",
    "requested": true,
    "status": "completed",
    "error": null,
    "fileSize": 5826163,
    "fileSizeHuman": "5.55 MB",
    "downloadSpeed": "4.2 MB/s",
    "duration": "1.3s",
    "runId": "exampleRunId123"
  },
  "processingTime": 4200,
  "success": true
}
```

The extracted videos are clean without TikTok watermarks, as they're obtained directly from TikTok's content delivery network rather than through the mobile app interface.

## 🎯 Configuration Examples

### Basic Video Extraction
```json
{
  "videoUrls": [
    "https://www.tiktok.com/@samplecreator/video/7234567890123456789"
  ],
  "preferredFps": "60"
}
```

### Batch Processing with Custom Settings
```json
{
  "videoUrls": [
    "https://www.tiktok.com/@creator1/video/7111111111111111111",
    "https://www.tiktok.com/@creator2/video/7222222222222222222",
    "https://www.tiktok.com/@creator3/video/7333333333333333333"
  ],
  "preferredFps": "30",
  "timeout": 45
}
```

### High Quality Processing
```json
{
  "videoUrls": [
    "https://www.tiktok.com/@qualitycreator/video/7444444444444444444"
  ],
  "preferredFps": "60",
  "timeout": 60
}
```

## 🔄 Advanced Features

### Reliability & Performance
- **Smart Rate Limiting**: 2-second delays between requests to avoid detection
- **Error Recovery**: Robust error handling with detailed failure reporting
- **Batch Processing**: Efficient handling of multiple URLs with progress tracking
- **Resource Optimization**: Dynamic memory allocation for download operations

### Content Processing
- **FPS-Based Selection**: Intelligent video quality selection based on preferred frame rate
- **Bitrate Optimization**: Automatically selects highest quality within chosen FPS
- **Multiple CDN Support**: Handles various TikTok CDN endpoints and formats
- **Cookie Management**: Proper session handling for reliable video access

### Data Quality
- **Complete Metadata**: Comprehensive video and creator information
- **Engagement Metrics**: Real-time view counts, likes, shares, and comments
- **Technical Details**: File sizes, dimensions, duration, and quality information
- **Timestamp Tracking**: Processing times and extraction timestamps

## 🛠️ Troubleshooting

### Video Extraction Issues
- **No Direct URL**: Video may be private, deleted, or region-restricted
- **Quality Issues**: Try different FPS settings if preferred quality unavailable
- **Access Denied**: Some videos require authentication or have geographic restrictions

### Download Problems
- **File Size Errors**: Large videos require more memory - Actor handles this automatically
- **Timeout Issues**: Increase timeout setting for slow network conditions
- **Authentication**: Ensure APIFY_TOKEN is properly set for download functionality

### Performance Issues
- **Slow Processing**: Check TikTok server status and network connectivity
- **Rate Limiting**: Actor includes built-in delays, but TikTok may still impose limits
- **Memory Usage**: Downloads automatically allocate optimal memory based on file size

## 📈 Resource Requirements

### Memory Allocation
- **Basic Extraction**: 128-256 MB (default)
- **With Downloads**: Auto-calculated based on video file sizes
- **Batch Processing**: Scales automatically per video

### Processing Times
- **Single Video**: 3-8 seconds average
- **Batch Processing**: ~5 seconds per video + 2-second delays
- **Large Files**: Download time varies based on file size and network speed

## ⚠️ Important Notes

### Legal & Ethical Usage
- **Respect Copyright**: Only download content you have rights to use
- **Platform Terms**: Use responsibly and respect TikTok's terms of service
- **Rate Limiting**: Built-in delays help maintain respectful usage patterns
- **Content Rights**: Extracted content belongs to original creators

### Technical Limitations
- **Maximum URLs**: 50 videos per batch to ensure reliable processing
- **Public Content**: Only processes publicly accessible TikTok videos
- **CDN Availability**: Direct URLs have expiration times set by TikTok
- **Geographic Restrictions**: Some content may not be available in all regions

---

## 🤝 Support & Resources

### **Getting Help**
- **📧 Email**: [fridaytechnolog@gmail.com](mailto:fridaytechnolog@gmail.com)
- **🐙 GitHub**: [DZ-ABDLHAKIM](https://github.com/DZ-ABDLHAKIM)
- **🐦 Twitter**: [@DZ_45Omar](https://x.com/DZ_45Omar)
- **🔧 Apify**: [dz_omar](https://apify.com/dz_omar)

---

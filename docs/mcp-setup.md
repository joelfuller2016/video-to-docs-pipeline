# MCP Server Setup Guide

## Installation

1. Install the MCP server:
```bash
npx @video-to-docs/mcp-server
```

2. Add to your MCP configuration file:

```json
{
  "mcpServers": {
    "video-to-docs": {
      "command": "npx",
      "args": ["@video-to-docs/mcp-server"]
    }
  }
}
```

## Available Tools

### `processVideo`
Main pipeline function that processes a video file through the complete workflow.

**Parameters:**
- `videoPath` (string): Path to input video file
- `outputDir` (string): Directory for generated documentation
- `options` (object): Processing options

**Options:**
- `analysisDepth`: "basic" | "detailed" | "comprehensive"
- `screenshotQuality`: "standard" | "high" | "ultra"
- `outputFormat`: "markdown" | "html" | "pdf"
- `whisperModel`: "tiny" | "base" | "small" | "medium" | "large"

### `extractAudio`
Extract audio track from video file.

**Parameters:**
- `videoPath` (string): Input video file
- `outputPath` (string): Output audio file path
- `quality` (string): Audio quality setting

### `transcribeAudio`
Transcribe audio file using OpenAI Whisper.

**Parameters:**
- `audioPath` (string): Input audio file
- `model` (string): Whisper model to use
- `outputFormat` (string): Output format ("json" | "txt" | "srt")

### `analyzeTranscription`
Analyze transcription to identify key moments.

**Parameters:**
- `transcriptionPath` (string): Path to transcription file
- `analysisDepth` (string): Depth of analysis

### `extractScreenshots`
Extract screenshots at specified timestamps.

**Parameters:**
- `videoPath` (string): Input video file
- `timestamps` (array): Array of timestamp objects
- `outputDir` (string): Screenshot output directory
- `quality` (string): Screenshot quality

### `generateDocumentation`
Generate final documentation from processed components.

**Parameters:**
- `transcriptionPath` (string): Transcription file path
- `screenshotsDir` (string): Screenshots directory
- `analysisData` (object): Analysis results
- `outputPath` (string): Final documentation output path
- `format` (string): Output format

## Configuration

Create a `.video-to-docs.json` configuration file:

```json
{
  "defaultSettings": {
    "whisperModel": "base",
    "analysisDepth": "detailed",
    "screenshotQuality": "high",
    "outputFormat": "markdown"
  },
  "paths": {
    "tempDir": "./temp",
    "outputDir": "./output"
  },
  "advanced": {
    "ffmpegPath": "ffmpeg",
    "whisperPath": "whisper",
    "maxVideoLength": 7200,
    "parallelProcessing": true
  }
}
```

## Error Handling

The MCP server includes comprehensive error handling:

- File validation and format checking
- Graceful degradation for processing failures
- Detailed error messages with suggested solutions
- Automatic cleanup of temporary files

## Performance Tips

1. **GPU Acceleration**: Install CUDA support for faster processing
2. **Model Selection**: Use smaller Whisper models for faster transcription
3. **Parallel Processing**: Enable parallel processing for large videos
4. **Temporary Storage**: Use SSD storage for temporary files

## Troubleshooting

### Common Issues

**FFmpeg not found:**
```bash
# Install FFmpeg
winget install ffmpeg
# Or add to PATH manually
```

**Whisper installation issues:**
```bash
# Reinstall with all dependencies
pip uninstall openai-whisper
pip install openai-whisper[all]
```

**Permission errors:**
```bash
# Run with appropriate permissions
# Ensure write access to output directories
```

**Memory issues with large videos:**
- Use smaller Whisper models
- Process video in chunks
- Increase system memory or use swap
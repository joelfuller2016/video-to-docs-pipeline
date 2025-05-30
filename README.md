# Video-to-Documentation Pipeline

🎥 **Automated Video-to-Documentation Pipeline**: Convert local videos into professional how-to guides with AI transcription, intelligent analysis, and synchronized screenshots.

## 🚀 Features

- **Intelligent Video Processing**: Extract audio and analyze video content using FFmpeg
- **AI-Powered Transcription**: High-quality speech-to-text with precise timestamps using OpenAI Whisper
- **Smart Content Analysis**: Identify key instructional moments using advanced reasoning algorithms
- **Automated Screenshot Extraction**: Capture relevant frames at identified important timestamps
- **Professional Documentation**: Generate comprehensive how-to guides with synchronized screenshots and text
- **Multiple Implementation Options**: Available as MCP server or n8n workflow

## 🏗️ Architecture

```
Local Video → Audio Extraction → Whisper Transcription → 
AI Analysis → Key Moment Identification → Screenshot Extraction → 
Professional How-To Documentation
```

### Core Components

1. **FFmpeg Video Processing**: Video/audio extraction and frame capture
2. **OpenAI Whisper**: Speech-to-text transcription with timestamps
3. **MCP Reasoning Tools**: Intelligent analysis of transcription content
4. **Screenshot Automation**: Synchronized frame extraction
5. **Document Generation**: Professional guide creation

## 📦 Implementation Options

### Option 1: MCP Server (Recommended)
- Single-call interface for complete pipeline
- Integrates seamlessly with Claude Desktop
- Zero-configuration after setup

### Option 2: n8n Workflow
- Visual workflow automation
- Customizable pipeline steps
- Integration with external services

### Option 3: CLI Tool
- Command-line interface for batch processing
- Scriptable automation
- Perfect for CI/CD integration

## 🛠️ Installation

### Prerequisites

```bash
# Install FFmpeg
winget install ffmpeg

# Install OpenAI Whisper
pip install openai-whisper

# Install MCP Screenshot tool
npx mcp-screenshot
```

### MCP Server Installation

```bash
# Install the MCP server
npx @video-to-docs/mcp-server

# Add to MCP configuration
# Configuration instructions in docs/mcp-setup.md
```

### n8n Workflow Installation

```bash
# Import workflow
cp workflows/video-to-docs.json ~/n8n/workflows/

# Configuration instructions in docs/n8n-setup.md
```

## 🎯 Quick Start

### Using MCP Server

```typescript
// Single call to process video
const result = await processVideoToDocumentation({
  videoPath: "./tutorial.mp4",
  outputDir: "./documentation",
  analysisDepth: "detailed",
  screenshotQuality: "high"
});
```

### Using n8n Workflow

1. Upload video to input folder
2. Trigger workflow via webhook or schedule
3. Receive generated documentation in output folder

### Using CLI

```bash
video-to-docs process \
  --input "tutorial.mp4" \
  --output "./docs" \
  --analysis-depth detailed \
  --screenshot-quality high
```

## 📁 Project Structure

```
video-to-docs-pipeline/
├── src/
│   ├── mcp-server/          # MCP server implementation
│   ├── n8n-workflows/       # n8n workflow definitions
│   ├── cli/                 # Command-line interface
│   └── core/                # Shared pipeline logic
├── docs/                    # Documentation
├── examples/                # Example videos and outputs
├── tests/                   # Test suite
└── workflows/               # Pre-built workflow files
```

## 🔧 Configuration

### Environment Variables

```bash
# Optional: OpenAI API key for enhanced analysis
OPENAI_API_KEY=your_key_here

# Optional: Custom models
WHISPER_MODEL=base  # tiny, base, small, medium, large
ANALYSIS_MODEL=gpt-4

# Output settings
OUTPUT_FORMAT=markdown  # markdown, html, pdf
SCREENSHOT_FORMAT=png   # png, jpg, webp
```

## 📊 Pipeline Workflow

### Step 1: Video Analysis
- Extract metadata and basic information
- Determine optimal processing parameters

### Step 2: Audio Extraction
- Extract high-quality audio track
- Optimize for transcription accuracy

### Step 3: Transcription
- Generate text with precise timestamps
- Include confidence scores and speaker detection

### Step 4: Content Analysis
- Identify key instructional moments
- Detect topic transitions and important actions
- Score sections by instructional value

### Step 5: Screenshot Extraction
- Extract frames at identified key moments
- Apply quality enhancement and cropping
- Generate descriptive captions

### Step 6: Documentation Generation
- Structure content logically
- Synchronize screenshots with transcription
- Generate professional formatting

## 🎬 Example Output

Input: 20-minute software tutorial video  
Output: Professional how-to guide with 15 key screenshots and step-by-step instructions

## 🤝 Contributing

Contributions welcome! Please read [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines.

## 📄 License

MIT License - see [LICENSE](LICENSE) for details.

## 🙏 Acknowledgments

- OpenAI Whisper team for excellent transcription capabilities
- FFmpeg developers for comprehensive video processing
- MCP (Model Context Protocol) for seamless AI integration
- n8n community for workflow automation framework
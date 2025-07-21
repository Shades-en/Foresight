# Foresight 🔍

**An Image to Text conversational workflow specifically for Partially Blind usecases achieving Object Grounding**

Foresight is a complete open-source solution that combines state-of-the-art AI models to create an accessible conversational interface for visually impaired users. The system provides detailed image descriptions, object detection, and voice-controlled navigation to help users better understand their visual environment.

## ✨ Features

- **🖼️ Image-to-Text Conversion**: Advanced visual understanding using LLaVA-1.5 model
- **🎯 Object Grounding**: Precise object detection and segmentation with Detectron2
- **💬 Conversational Interface**: Natural language interactions powered by Gemma 7B
- **🎤 Voice Control**: Speech-to-text functionality using OpenAI's Whisper model
- **🔍 Reduced Hallucinations**: Multi-model approach for more accurate descriptions
- **♿ Accessibility-First**: Designed specifically for partially blind users

## 🏗️ Architecture

The system integrates multiple AI models to provide a comprehensive visual assistance solution:

- **LLaVA-1.5**: Large Language and Vision Assistant for image understanding
- **Gemma 7B**: Google's lightweight language model for conversational responses
- **Detectron2**: Facebook's object detection and segmentation framework
- **Whisper**: OpenAI's speech recognition model for voice input
- **FastAPI**: High-performance web framework for API endpoints

## 🚀 Quick Start

### Prerequisites

- Python 3.8+
- CUDA-compatible GPU (recommended)
- 8GB+ RAM

### Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/Shades-en/Foresight.git
   cd Foresight
   ```

2. **Install dependencies**
   ```bash
   pip install -r requirements.txt
   ```

3. **Set up environment variables**
   ```bash
   cp .env.example .env
   # Add your API keys and configuration
   ```

4. **Run the application**
   ```bash
   uvicorn main:app --reload --port 8000
   ```

The API will be available at `http://localhost:8000`

## 📚 API Endpoints

### Core Conversation Endpoints

- **POST `/begin_conversation`**
  - Start a new conversation with an image
  - Parameters: `prompt` (string), `image` (file)
  - Returns: Initial response and processed image

- **POST `/converse`**
  - Continue an existing conversation
  - Parameters: `prompt` (string)
  - Returns: Conversational response

- **GET `/get_convo_history`**
  - Retrieve conversation history
  - Returns: Complete chat history

### Voice Control

- **POST `/transcribe`**
  - Convert speech to text
  - Parameters: `file` (audio file)
  - Returns: Transcribed text

## 🛠️ Usage Example

```python
import requests

# Start a conversation with an image
with open('image.jpg', 'rb') as img:
    response = requests.post(
        'http://localhost:8000/begin_conversation',
        data={'prompt': 'What objects do you see in this image?'},
        files={'image': img}
    )

# Continue the conversation
response = requests.post(
    'http://localhost:8000/converse',
    data={'prompt': 'Can you tell me more about the objects on the left?'}
)
```

## 🔧 Configuration

The system uses several configurable models:

- **LLaVA Model**: 4-bit quantization for memory efficiency
- **Detectron2**: COCO instance segmentation model
- **Gemini**: Google's generative AI model
- **Whisper**: Automatic speech recognition

## 📁 Project Structure

```
Foresight/
├── main.py                 # FastAPI application entry point
├── requirements.txt        # Python dependencies
├── controllers/           
│   └── chatController.py   # Main conversation logic
├── utils/
│   ├── llava_utils.py     # LLaVA model utilities
│   ├── whisper_utils.py   # Whisper model utilities
│   ├── detectron_utils.py # Detectron2 utilities
│   ├── coreChat.py        # Core chat functionality
│   └── llms/
│       └── gemini_utils.py # Gemini model utilities
└── static/                # Static files and generated images
```

## 🤝 Contributing

We welcome contributions to make Foresight more accessible and effective! Please feel free to:

- Report bugs and issues
- Suggest new features
- Submit pull requests
- Improve documentation

## 📄 License

This project is open-source and available under the [MIT License](LICENSE).

## 🙏 Acknowledgments

- **LLaVA Team** for the vision-language model
- **Google** for Gemma and Gemini models
- **Facebook Research** for Detectron2
- **OpenAI** for Whisper
- **FastAPI** for the excellent web framework

## 📞 Support

If you encounter any issues or have questions about using Foresight, please:

1. Check the [Issues](https://github.com/Shades-en/Foresight/issues) page
2. Create a new issue with detailed information
3. Join our community discussions

---

**Made with ❤️ for accessibility and inclusion**

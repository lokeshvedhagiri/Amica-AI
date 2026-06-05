# Amica - Your Compassionate AI Companion

![Amica](Untitled.gif)

## 🌟 Overview

**Amica** is an intelligent, warm, and empathetic AI companion specifically designed for **older adults** and **couples living alone**. Amica provides a lifeline of companionship, healthcare support, and emotional connection through natural multilingual conversations in **Tamil, English, and Tanglish**.

Amica goes beyond simple chatbots—she's engineered to understand the unique needs of elderly users, providing healthcare tips, medication reminders, social connectivity, and genuine emotional support through expressive voice interactions.

### 💡 Key Features

- **🗣️ Voice-Based Conversation**: Natural, expressive speech interaction using advanced TTS (Text-to-Speech)
- **🌍 Multilingual Support**: Fluent in Tamil, English, and Tanglish (Tamil-English blend)
- **❤️ Emotional Intelligence**: SSML-enhanced voice output with warmth, empathy, and personality
- **💊 Health & Wellness**: Medication reminders, health tips, and appointment management
- **📞 Social Connectivity**: Easy contact management and calling capabilities
- **👥 Companion Conversations**: Engaging discussions tailored for senior citizens
- **📱 GUI & CLI Modes**: Both graphical interface (PyQt6) and command-line options
- **🧠 Memory & Personalization**: Learns and remembers user preferences and important details

---

## 🎯 Who Is Amica For?

Amica is ideal for:
- **Elderly individuals** seeking daily companionship and emotional connection
- **Couples living alone** who want an additional support system
- **People managing chronic conditions** requiring medication reminders and health tracking
- **Anyone seeking a compassionate, always-available conversational partner**

---

## 🛠️ Technology Stack

### Core Technologies
- **Python 3.11+** - Main programming language
- **PyQt6** - GUI framework for desktop application
- **FastAPI** - Web framework for backend services

### AI & Speech Processing
- **Faster Whisper** - High-performance speech-to-text (STT)
- **JAX Whisper** - Alternative STT with Tamil language support
- **ElevenLabs** - Advanced text-to-speech with emotional SSML support
- **LLMs** - Cloud-based language models for intelligent conversation

### Audio Processing
- **FFmpeg** - Audio format conversion and processing
- **Librosa** - Audio analysis and features extraction
- **Soundfile** - Audio I/O operations
- **PyAudio** - Real-time audio input/output

### NLP & Deep Learning
- **Transformers** - Hugging Face transformers for NLP tasks
- **JAX / Flax** - High-performance numerical computing
- **Torch / TensorFlow** - Deep learning frameworks for audio models
- **Datasets** - Efficient data loading and processing

### Cloud & Infrastructure
- **AWS** - Cloud storage and services
- **Boto3** - AWS SDK for Python
- **Docker** - Containerization support
- **Twilio** - VoIP integration for calling features

### Additional Libraries
- **Pydantic** - Data validation and settings management
- **Pydantic Settings** - Configuration management
- **Click** - CLI framework
- **Fire** - Python Fire for simple CLIs

See [requirements.txt](requirements.txt) for the complete dependency list.

---

## 📁 Project Structure

```
aalok/
├── amica.py                      # Main Amica application (GUI enabled)
├── amica_nogui.py               # CLI-only version without GUI
├── qamica.py                     # Question & Answer assistant module
├── recorder.py                   # Audio recording utilities
├── portals/                      # Modular service providers
│   ├── llm_cloud.py             # Cloud-based LLM integration
│   ├── stt_fast.py              # Faster Whisper STT module
│   ├── stt_jax.py               # JAX-based STT module
│   ├── tts_cloud.py             # ElevenLabs TTS service
│   ├── tts_local.py             # Local TTS processing
│   └── utils.py                 # Utility functions
├── _local_test/                 # Local testing modules
│   ├── fastwhisp.py             # Faster Whisper tests
│   ├── jaxwhisper_tamil.py      # Tamil Whisper tests
│   ├── tts_local.py             # Local TTS tests
│   ├── wakeword_usingtiny.py    # Wake word detection
│   └── test.py                  # General tests
├── _test_audios/                # Test audio files
├── audios/                       # User audio recordings
├── userinfo.json                # User profile data
├── contactlist.json             # Contact information
├── medicalrecords.json          # Health records
├── reminders.json               # Scheduled reminders
├── sys_instruction.txt          # System prompts and behavior rules
└── requirements.txt             # Python dependencies
```

---

## 🚀 Getting Started

### Prerequisites
- Python 3.11 or higher
- pip or conda package manager
- Audio input/output devices
- Internet connection (for cloud services)

### Installation

1. **Clone the repository**:
   ```bash
   git clone <repository_url>
   cd aalok
   ```

2. **Create a virtual environment** (recommended):
   ```bash
   python3 -m venv amica_env
   source amica_env/bin/activate  # On Windows: amica_env\Scripts\activate
   ```

3. **Install dependencies**:
   ```bash
   pip install -r requirements.txt
   ```

4. **Configure API Keys** (if using cloud services):
   - ElevenLabs API key for TTS
   - LLM cloud service credentials
   - AWS credentials (if using cloud storage)

### Running Amica

#### **GUI Mode** (Recommended for end users):
```bash
python amica.py
```
This launches the PyQt6-based graphical interface with the waveform visualization and voice interaction.

#### **CLI Mode** (No GUI):
```bash
python amica_nogui.py
```
Suitable for server deployments or testing without a graphical environment.

#### **Local Testing**:
```bash
python local_test.py
```

---

## 💬 How Amica Works

### Conversation Flow

```
User speaks 
    ↓
Audio captured → STT (Speech-to-Text)
    ↓
Text input processed → LLM generates response
    ↓
Response formatted with personality & SSML tags
    ↓
TTS (Text-to-Speech) with emotional voice output
    ↓
User hears warm, expressive reply
```

### Key Capabilities

#### 1. **Voice Interaction**
- Captures user speech via microphone
- Converts to text using Faster Whisper or JAX Whisper
- Processes with language understanding models
- Generates expressive audio response

#### 2. **Health & Wellness Management**
- **Medication Reminders**: Set recurring reminders for pills and treatments
- **Appointment Tracking**: Remember and remind about doctor visits
- **Health Tips**: Provides personalized wellness advice
- **Medical History**: Stores user health records (optional, privacy-focused)

#### 3. **Social Connectivity**
- **Contact Management**: Maintains list of family and friends
- **Call Integration**: Initiates calls to contacts via Twilio
- **Message Relay**: Can deliver messages on user's behalf

#### 4. **Personalization & Memory**
- Learns user preferences and important details
- Remembers family members' names, dates of events
- Adapts conversation style based on user feedback
- Stores important information in `important: []` field

#### 5. **Emotional Intelligence**
- Uses SSML tags for voice modulation
- Responds with appropriate emotional tone (cheerful, empathetic, supportive)
- Uses warm interjections and phrases
- Maintains 5-8 sentence responses (concise and digestible)

---

## 🎛️ Configuration

### System Instructions
Edit `sys_instruction.txt` to customize Amica's behavior, personality, and tone.

### User Information
- **userinfo.json**: Personal details, preferences
- **contactlist.json**: Contacts for calling and messaging
- **medicalrecords.json**: Health information (optional, encrypted storage recommended)
- **reminders.json**: Scheduled reminders and recurring tasks

### Environment Variables
Create a `.env` file for sensitive credentials:
```env
ELEVENLABS_API_KEY=your_api_key
LLM_API_KEY=your_api_key
AWS_ACCESS_KEY_ID=your_key
AWS_SECRET_ACCESS_KEY=your_secret
```

---

## 🔧 Development

### Module Overview

- **amica.py / amica_nogui.py**: Entry points for the application
- **qamica.py**: Question-Answer assistant and LLM integration
- **recorder.py**: Audio recording and processing
- **portals/**: Modular service architecture
  - **stt_fast.py**: Faster Whisper integration
  - **stt_jax.py**: JAX-based STT (Tamil support)
  - **tts_cloud.py**: ElevenLabs cloud TTS
  - **tts_local.py**: Local TTS processing
  - **llm_cloud.py**: Cloud LLM services
  - **utils.py**: Helper functions

### Extending Amica

To add new features:
1. Implement in appropriate module (`portals/`, `qamica.py`, etc.)
2. Update tool definitions in `sys_instruction.txt`
3. Test with local test files
4. Update documentation

---

## 🧪 Testing

Run local tests to validate components:
```bash
python _local_test/test.py               # General tests
python _local_test/fastwhisp.py          # STT tests
python _local_test/jaxwhisper_tamil.py   # Tamil STT tests
python _local_test/tts_local.py          # TTS tests
python _local_test/wakeword_usingtiny.py # Wake word detection
```

---

## 📋 JSON Data Formats

### userinfo.json
```json
{
  "name": "User Name",
  "age": 65,
  "language_preference": "Tamil",
  "timezone": "Asia/Kolkata"
}
```

### contactlist.json
```json
{
  "contacts": [
    {"name": "Arjun", "phone": "+91-98765-43210"},
    {"name": "Priya", "phone": "+91-87654-32109"}
  ]
}
```

### reminders.json
```json
{
  "reminders": [
    {
      "time": "09:00",
      "date": "today",
      "repeatdays": "1234567",
      "message": "Take your morning medications"
    }
  ]
}
```

---

## 🎤 Example Interaction

**User**: "அமிகா, நாளைக்கு காலை 8 மணிக்கு என்னை medicine எடுக்க remind பன்னு" 
*(Amica, remind me to take medicine at 8 AM tomorrow)*

**Amica**: "அப்படியா, நாளைக்கு காலை 8 மணிக்கு உங்கள் medicine ஏற்றம் பண்ணும்படி reminder அமைக்கிறேன். உங்கள் ஆரோக்கியத்தில் நான் கவனம் வைக்கிறேன்." 
*(Of course! I'll set a reminder for you at 8 AM tomorrow. I'm looking after your health.)*

---

## 🔒 Privacy & Security

- **Local Storage**: User data stored locally in JSON files (consider encryption for sensitive data)
- **Cloud Services**: API calls to external services encrypted via HTTPS
- **Audio**: Voice recordings stored locally; can be deleted after processing
- **Data Access**: Medical and personal information kept private and secure

---

## 🤝 Contributing

Contributions are welcome! Please:
1. Fork the repository
2. Create a feature branch
3. Test thoroughly
4. Submit a pull request with documentation

---

## 📞 Support & Contact

For issues, questions, or feature requests, please open an issue on GitHub or contact the development team.

---

## 📄 License

[Specify your license here - e.g., MIT, GPL-3.0, etc.]

---

## 🙏 Acknowledgments

Built with compassion for older adults and couples seeking companionship. Special thanks to:
- ElevenLabs for expressive TTS
- Faster Whisper for efficient STT
- The open-source AI community

---

## 🌈 Future Roadmap

- [ ] Enhanced healthcare integration (EMR systems)
- [ ] Video calling support
- [ ] Multilingual support (Hindi, Kannada, etc.)
- [ ] Wearable device integration
- [ ] Advanced health analytics
- [ ] Community features (connect users)
- [ ] Mobile app versions

---

**Amica: Companion When You Need One Most** ❤️

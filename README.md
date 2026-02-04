# ScamBotGPT 🛡️

An AI-powered scam awareness and detection chatbot that helps non-technical users quickly evaluate whether emails, text messages, job offers, or phone call transcripts are likely scams.

[![Python 3.11+](https://img.shields.io/badge/python-3.11+-blue.svg)](https://www.python.org/downloads/)
[![FastAPI](https://img.shields.io/badge/FastAPI-0.104+-green.svg)](https://fastapi.tiangolo.com)
[![OpenAI](https://img.shields.io/badge/OpenAI-GPT--4o--mini-orange.svg)](https://platform.openai.com)

## 🎯 Overview

ScamBotGPT is a real-time scam detection assistant that provides accessible cybersecurity guidance to everyday users. Unlike enterprise fraud detection systems that are expensive and complex, ScamBotGPT offers immediate, clear assessments through a conversational interface.

### Key Features

- **Multi-Modal Analysis**
  - 📝 Text analysis for suspicious messages
  - 🖼️ Image analysis for fake checks and phishing screenshots
  - 🎤 Audio analysis for voice phishing recordings

- **Explainable AI**
  - Clear verdicts with specific red flags
  - Risk scores (0-100) for quantifiable danger assessment
  - Actionable next steps and recommendations

- **Conversational Interface**
  - Natural language responses
  - Context-aware follow-up questions
  - No technical jargon

- **Real-Time Performance**
  - Text analysis: ~2-5 seconds
  - Image analysis: ~6-8 seconds
  - Audio analysis: ~8-10 seconds

## 🚀 Quick Start

### Prerequisites

- Python 3.9 or higher (Python 3.11 recommended)
- OpenAI API key ([Get one here](https://platform.openai.com/api-keys))
- 4GB RAM minimum (8GB recommended)
- Modern web browser

### Installation

1. **Clone the repository**
```bash
git clone https://github.com/Charithaarigela/ScamBotGPT.git
cd ScamBotGPT
```

2. **Create virtual environment**
```bash
python -m venv venv

# On Windows:
venv\Scripts\activate

# On macOS/Linux:
source venv/bin/activate
```

3. **Install dependencies**
```bash
pip install -r requirements.txt
```

4. **Configure API key**

Create a `.env` file in the project root:
```env
OPENAI_API_KEY=sk-your-actual-key-here
```

5. **Start the server**
```bash
uvicorn main:app --reload --host 0.0.0.0 --port 8000
```

6. **Access the application**

Open your browser and navigate to:
```
http://localhost:8000
```

## 📁 Project Structure

```
ScamBotGPT/
├── main.py                 # FastAPI backend
├── requirements.txt        # Python dependencies
├── .env.example           # Environment variables template
├── README.md              # This file
├── public/
│   ├── index.html        # Frontend interface
│   └── logo.png          # Application logo
└── .gitignore
```

## 🔧 Technical Architecture

### Backend
- **FastAPI**: Python web framework
- **OpenAI Python SDK**: API integration
- **Pydantic**: Data validation
- **python-dotenv**: Configuration management
- **Uvicorn**: ASGI server

### Frontend
- Plain HTML/CSS/JavaScript (no frameworks)
- Chat-style interface with message bubbles
- File upload handlers for images and audio
- Asynchronous fetch API for backend communication

### AI Models
- **GPT-4o-mini**: Text chat and image vision analysis
- **Whisper** (gpt-4o-transcribe): Audio transcription

## 💡 Usage Examples

### Text Analysis
```
User: "Your bank account will be suspended in 24 hours. Click here to verify: http://secure-login-verify.com"

Bot: 🚨 This is definitely a scam!
Risk Score: 92/100
Red Flags:
- Urgency tactics ("24 hours")
- Suspicious URL
- Impersonation of bank
- Requests for verification

Recommended Actions:
1. Do NOT click the link
2. Contact your bank directly using official phone number
3. Report to FTC at reportfraud.ftc.gov
```

### Image Analysis
Upload a screenshot of a suspicious check or phishing email, and ScamBotGPT will:
- Extract text and visual elements
- Identify fraud indicators
- Provide evidence-based assessment
- Recommend verification steps

### Audio Analysis
Upload a recording of a suspicious phone call, and the system will:
- Transcribe speech to text using Whisper
- Analyze for voice phishing patterns
- Identify pressure tactics and scam indicators
- Provide guidance on next steps

## 🧪 Testing

The system has been tested with:
- ✅ 15 real scam examples from FTC reports
- ✅ PhishTank verified phishing emails
- ✅ Recorded voice scam examples
- ✅ Self-generated fake check images
- ✅ 100% detection rate on tested samples

### Run Quick Tests

1. **Text Test**: Type a suspicious message like "Your account will be suspended, click here to verify"
2. **Image Test**: Upload any image file via the "+" button
3. **Audio Test**: Upload an audio recording for transcription and analysis

## 📊 Performance Metrics

| Input Type | Avg Response Time | 90th Percentile |
|-----------|------------------|-----------------|
| Text (short, <100 words) | 2.3s | 3.1s |
| Text (long, 300+ words) | 3.8s | 5.2s |
| Image upload + analysis | 6.7s | 9.1s |
| Audio upload + transcription | 8.4s | 12.3s |

## 💰 Cost Analysis

Based on OpenAI pricing (as of December 2024):

| Query Type | Cost per Query | 1000 Queries |
|-----------|---------------|--------------|
| Text only | ~$0.00012 | ~$0.12 |
| With images | ~$0.00019 | ~$0.19 |
| With audio | ~$0.007 | ~$7.00 |

## 🔒 Privacy & Security

- **No persistent storage** of user submissions
- **Files deleted immediately** after analysis
- **No user accounts** or tracking
- **Session-only memory** that clears on restart
- **API calls** follow OpenAI's zero-retention policy

## ⚠️ Limitations

- **Language Support**: Currently English-only
- **Session Memory Only**: Memory clears on server restart
- **API Dependency**: Requires OpenAI service availability
- **Novel Scams**: May miss brand-new tactics not in training data
- **Not 100% Accurate**: Should be used as a guidance tool, not a guarantee

## 🚢 Production Deployment

### Deploy to Render

1. Create `render.yaml` in project root
2. Set environment variables in Render dashboard
3. Connect GitHub repository
4. Automatic deployment on push to main branch

### Production Considerations
- ✅ Enable HTTPS (Render provides automatically)
- ✅ Set up monitoring and logging
- ✅ Implement rate limiting to prevent abuse
- ✅ Add user analytics (with privacy protections)
- ✅ Consider API cost management strategies

## 🛠️ Troubleshooting

### Common Issues

**"ModuleNotFoundError: No module named 'fastapi'"**
```bash
pip install -r requirements.txt
```

**"RuntimeError: OPENAI_API_KEY is not set"**
- Ensure `.env` file exists with valid API key
- Check for extra spaces in the key

**"Address already in use"**
```bash
uvicorn main:app --reload --port 8001
```

**Browser shows "Connection refused"**
- Ensure server is running
- Check terminal for error messages
- Verify firewall isn't blocking port 8000

## 🤝 Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## 📄 License

This project was developed as a Master's thesis project at Gannon University.

## 👥 Authors

- **Charitha Arigela**

**Advisor**: Dr. Mei-Huei Tang, PhD

## 🎓 Academic Context

This project was submitted to Gannon University graduate faculty in partial fulfillment for the degree Master of Science in Information Assurance & Cybersecurity (December 2025).

## 📚 References

1. [OpenAI GPT-4o API Documentation](https://platform.openai.com/docs)
2. [Federal Trade Commission - Scam Alerts](https://consumer.ftc.gov/scams)
3. [Anti-Phishing Working Group](https://apwg.org)
4. [FastAPI Documentation](https://fastapi.tiangolo.com)
5. [OpenAI Whisper - Speech Recognition](https://openai.com/research/whisper)

## 📞 Support

For questions, issues, or feedback:
- Open an issue on GitHub
- Email: [charithaarigela03@gmail.com]

## 🌟 Acknowledgments

Special thanks to:
- Dr. Mei-Huei Tang for guidance throughout this project
- Cybersecurity faculty at Gannon University
- FTC and PhishTank for scam examples used in testing
- OpenAI for providing the API and models

---

**⚠️ Disclaimer**: ScamBotGPT is a guidance tool, not a guarantee. Always verify through official channels and use your judgment when dealing with suspicious communications. When in doubt, don't click or respond.

**🛡️ Stay Safe Online!**

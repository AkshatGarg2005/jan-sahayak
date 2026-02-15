# 🇮🇳 Jan-Sahayak — Voice-First Civil Caseworker

> *Democratizing access to Indian welfare schemes through natural voice conversations in vernacular dialects.*

---

## 📖 Overview

**Jan-Sahayak** is an AI-powered, voice-first system that bridges the welfare scheme utilization gap across India. It enables rural citizens to **discover** their eligibility for government welfare schemes, **check** qualification criteria, and **generate** filled application forms — all through natural voice conversations in their local dialect.

### The Problem

Millions of eligible Indian citizens miss out on welfare benefits due to:
- **Literacy barriers** — Complex forms in English or formal Hindi
- **Language barriers** — Schemes documented in languages citizens don't speak
- **Accessibility barriers** — No digital literacy or smartphone access
- **Middlemen dependency** — Exploitation by intermediaries charging fees for form-filling

### The Solution

Jan-Sahayak eliminates these barriers by providing a **voice-first, vernacular-native** AI assistant accessible via **WhatsApp** and **toll-free phone numbers**, covering schemes across **5 major sectors**.

---

## 🏗️ Architecture

The system follows a **microservices architecture** with clear separation of concerns:

```
┌─────────────┐     ┌─────────────┐
│  WhatsApp   │     │  Toll-Free  │
│  Interface  │     │  Interface  │
└──────┬──────┘     └──────┬──────┘
       │                   │
       └────────┬──────────┘
                │
         ┌──────▼──────┐
         │ API Gateway  │
         └──────┬──────┘
                │
      ┌─────────▼─────────┐
      │ Conversation Mgr  │
      └──┬──┬──┬──┬──┬────┘
         │  │  │  │  │
    ┌────┘  │  │  │  └────┐
    ▼       ▼  ▼  ▼       ▼
  ASR    Intent Elig.  Form   TTS
 Engine  Class. Engine  Gen.  Engine
                │
         ┌──────▼──────┐
         │   Scheme     │
         │  Database    │
         └─────────────┘
```

### Core Components

| Component | Responsibility |
|---|---|
| **Voice Input Module** | Accept & validate audio from WhatsApp / Toll-Free |
| **Speech Recognition Engine** | Convert vernacular speech to text (85%+ accuracy) |
| **Intent Classifier** | Map user queries to relevant welfare schemes |
| **Eligibility Engine** | Evaluate user eligibility against scheme rules |
| **Conversation Manager** | Orchestrate multi-turn dialogues & maintain context |
| **Form Generator** | Create filled PDF application forms |
| **Text-to-Speech Engine** | Convert responses back to vernacular speech |
| **Scheme Database** | Store 100+ central & state welfare schemes |

---

## 🎯 Sectors Covered

### 🌾 Agriculture
Crop damage relief, PM-KISAN, agricultural subsidies, land-related benefits

### ♿ Disability Support
UDID registration, disability pensions, ADIP scheme, assistive devices, special education

### 👩 Women Empowerment
Maternity benefits (PM-MVY), Beti Bachao Beti Padhao, entrepreneurship support, widow pensions, safety helplines (181, 1091)

### 🏥 Health
Ayushman Bharat (PM-JAY), state health insurance, TB support, cancer treatment assistance, maternal health

### 🎓 Education Scholarships
Pre-matric & post-matric scholarships, PM-YASASVI, minority scholarships, merit-cum-means, girl child education

---

## 🗣️ Supported Languages

| Language | Code | Dialects |
|---|---|---|
| Hindi | `hi` | Awadhi |
| Bhojpuri | `bho` | — |
| Maithili | `mai` | — |
| Marathi | `mr` | Warli |
| Bengali | `bn` | — |
| Tamil | `ta` | — |
| Telugu | `te` | — |
| Gujarati | `gu` | — |
| Punjabi | `pa` | — |
| Kannada | `kn` | — |

The system also handles **code-mixing** (Hindi-English, vernacular-Hindi).

---

## 📱 Channels

### WhatsApp
- Accessible on basic smartphones
- Supports voice messages and text
- PDFs compressed to < 2 MB for low-bandwidth
- Session resumption within 24 hours

### Toll-Free Number
- Works on **any phone** (no smartphone needed)
- IVR menu for language selection
- DTMF fallback for poor call quality
- Supports 100+ concurrent calls

---

## 🔄 End-to-End Workflow

```
1. 🎤 Citizen describes their problem in local dialect
        ↓
2. 🧠 System identifies the problem category
        ↓
3. 📋 Best matching schemes are recommended
        ↓
4. ✅ Eligibility is checked via conversational Q&A
        ↓
5. 📄 Filled application form (PDF) is generated
        ↓
6. 📍 Nearby service centers (MP Online / Jan Seva Kendra) are located
        ↓
7. 🎥 Video tutorial links are shared
        ↓
8. 📞 Relevant helpline numbers are provided
```

---

## 🔒 Privacy & Security

- **TLS 1.3+** encryption for all data in transit
- **AES-256** encryption for data at rest
- Voice recordings anonymized after transcription
- No third-party data sharing without consent
- Full data deletion within 48 hours on request
- Compliant with Indian data protection regulations

---

## ⚡ Performance

| Metric | Target |
|---|---|
| Response time (P95) | < 10 seconds |
| Minimum bandwidth | 2G (32 kbps) |
| Concurrent users | 10,000+ |
| Session duration | Up to 30 minutes |
| Offline resumption | Up to 24 hours |

---

## 📂 Project Structure

```
jan-sahayak/
├── README.md              # Project overview (this file)
├── requirements.md        # Detailed requirements & acceptance criteria
└── design.md              # Technical design document & architecture
```

---

## 🛠️ Tech Stack

- **Speech-to-Text**: Google Speech / Azure Speech / Bhashini
- **NLP Models**: mBERT, IndicBERT (fine-tuned on scheme data)
- **Text-to-Speech**: Natural vernacular voice synthesis
- **Session Store**: Redis
- **Rule Engine**: JSON Logic for eligibility evaluation
- **Form Generation**: PDF templating with official government formats
- **Messaging**: WhatsApp Business API
- **Telephony**: IVR / SIP-based toll-free provider

---

## 🚀 Getting Started

> 🏗️ *This project is currently in the design and requirements phase. Implementation instructions will be added as development progresses.*

### Prerequisites

- Node.js 18+ / Python 3.10+
- Redis instance
- WhatsApp Business API access
- Telephony provider credentials
- Speech API credentials (Google / Azure / Bhashini)

---

## 🤝 Contributing

Contributions are welcome! Please read the requirements and design documents before submitting changes:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/your-feature`)
3. Commit your changes (`git commit -m 'Add your feature'`)
4. Push to the branch (`git push origin feature/your-feature`)
5. Open a Pull Request


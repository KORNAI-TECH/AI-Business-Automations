# 🤖 AI Meeting Secretary

[Russian version below](#russian-version)

An intelligent Telegram bot designed to automate the process of transcribing and analyzing business meetings, phone calls, and voice notes. It converts audio into structured business protocols with high accuracy using advanced AI models.

---

## 🌟 Key Features

*   **Multi-format Support**: Processes voice messages, audio files (mp3, ogg, m4a), and Telegram video notes ("circles").
*   **Deep Transcription (STT)**: Powered by **OpenAI Whisper V3** (via Groq API) for near-perfect speech-to-text conversion.
*   **Intelligent Diarization**: Automatically separates speakers and identifies roles based on linguistic context and voice patterns.
*   **Structured Business Reports**:
    *   **Topic Identification**: Summarizes the meeting's core objective.
    *   **Participant Roles**: Identifies speakers and their professional roles (e.g., "Ivan — Project Manager").
    *   **Action Items**: Generates a clear, numbered list of tasks with assignees and deadlines.
    *   **Detailed Summary**: Provides a 3-4 paragraph narrative of the discussion flow.
*   **Verbatim Transcript**: Delivers a full, line-by-line dialogue script in the final document.
*   **Document Export**: Generates professional `.docx` (Microsoft Word) files with clean formatting and page breaks.
*   **Hybrid AI Fallback**: Seamlessly switches between AI models (Gemini Flash <-> Groq Llama) to ensure 100% uptime and bypass rate limits.

---

## 🏗 Architecture (Data Flow)

```text
[ User Audio ]
      |
      ▼
[ Telegram Bot (aiogram 3.x) ]
      |
      ▼
[ Groq Whisper V3 ] ———▶ [ Raw Text Transcription ]
      |                         |
      ▼                         ▼
[ AI Analysis Engine ] ◀———— [ Logic Layer (Python) ]
(Gemini Flash / Llama 70B)      |
      |                         ▼
      |             [ Format Splitter (Chat vs File) ]
      ▼                         |
[ Structured Report ] ———————▶ [ Docx Generator ]
      |                         |
      ▼                         ▼
[ Telegram UI (Summary) ]   [ Microsoft Word File ]
```

---

## 🛠 Tech Stack

*   **Language**: Python 3.11+
*   **Framework**: Aiogram 3.x (Asynchronous)
*   **AI Models**:
    *   Groq Whisper-V3 (Speech-to-Text)
    *   Llama-3.3-70b-versatile (LLM Analysis)
    *   Gemini-1.5-flash (Diarization)
*   **Documents**: Python-docx
*   **Infrastructure**: Render PaaS

---


## 🚀 Quick Start

### 1. Installation
```bash

pip install -r requirements.txt

TELEGRAM_TOKEN=your_token
GROQ_API_KEY=your_groq_key
GEMINI_API_KEY=your_gemini_key

python bot.py
```

---


<a name="russian-version"></a>
# 🇷🇺 Русская версия

## AI Meeting Secretary: Интеллектуальный корпоративный ассистент

Инновационный Telegram-бот для автоматизации протоколирования встреч и телефонных звонков. Сервис преобразует аудиозаписи в профессиональные бизнес-протоколы.

### ✨ Основные функции:
*   **100% Полнота**: Захват речи с первой секунды, включая приветствия и переводы звонков.
*   **Умная диаризация**: Идентификация участников и их должностей по контексту разговора.
*   **Задачи блоками**: Четкое разделение поручений, ответственных и сроков.
*   **Экспорт в Word**: Генерация готового документа `.docx` с корпоративной версткой.
*   **Отказоустойчивость**: Система автоматического переключения между нейросетями при сбоях (Gemini <-> Groq).

---
---

👨‍💻 **Developer:** Nothingtham <br>
📬 **Reach me at:** [Telegram: @AlexeiKornienko](https://t.me/AlexeiKornienko)
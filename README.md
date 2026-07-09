# ⚡ J.A.R.V.I.S.
### Just A Rather Very Intelligent System
*Your Iron Man-style AI voice assistant for Windows PC*

---

```
╔═══════════════════════════════════════════════════════════════╗
║  ░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░  ║
║  ░                                                         ░  ║
║  ░      ██╗ █████╗ ██████╗ ██╗   ██╗██╗███████╗          ░  ║
║  ░      ██║██╔══██╗██╔══██╗██║   ██║██║██╔════╝          ░  ║
║  ░      ██║███████║██████╔╝██║   ██║██║███████╗          ░  ║
║  ░ ██   ██║██╔══██║██╔══██╗╚██╗ ██╔╝██║╚════██║          ░  ║
║  ░ ╚█████╔╝██║  ██║██║  ██║ ╚████╔╝ ██║███████║          ░  ║
║  ░  ╚════╝ ╚═╝  ╚═╝╚═╝  ╚═╝  ╚═══╝  ╚═╝╚══════╝          ░  ║
║  ░                                                         ░  ║
║  ░   Just A Rather Very Intelligent System  v2.0.0        ░  ║
║  ░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░  ║
╚═══════════════════════════════════════════════════════════════╝
```

---

## 🎯 Features

| Feature | Description |
|---------|-------------|
| 🗣️ **Voice AI** | Speak naturally — JARVIS listens and responds |
| 🇮🇳 **Hinglish** | Talks in mixed Hindi + English like a real Indian assistant |
| 📱 **Open Apps** | "Open Chrome", "Kholo Notepad", "Start VS Code" |
| 🔍 **Google Search** | "Search for latest news" → Opens Google |
| 🌤️ **Weather** | "Mumbai ka mausam kya hai?" → Real-time weather |
| ⏰ **Date & Time** | "Kitne baje hain?" → Instant answer |
| 🎨 **Iron Man HUD** | Black/cyan animated UI with Arc Reactor |
| ⚙️ **Settings Panel** | Configure API keys, voice, name without coding |
| 🔗 **MCP / n8n** | Trigger automation workflows via webhook |
| 📸 **Screenshots** | "Take a screenshot" → Saved to Pictures |
| 🔊 **Volume Control** | "Volume up/down/mute" |
| 💻 **System Control** | Shutdown, restart, sleep commands |

---

## 🚀 Quick Start (Windows)

### Option 1: Installer Script (Recommended)
```powershell
# 1. Open PowerShell in the jarvis folder
# 2. Run the installer:
.\install.ps1

# 3. Then start JARVIS:
assistant start
```

### Option 2: Manual Install
```bash
# 1. Install Python dependencies
pip install -r requirements.txt

# 2. Install the 'assistant' command
pip install -e .

# 3. First-time setup
assistant setup

# 4. Launch JARVIS
assistant start
```

### Option 3: Direct Python
```bash
# Setup
python assistant.py setup

# Start GUI
python assistant.py start

# Start in CLI mode (no GUI needed)
python assistant.py start --cli
```

---

## 📋 Prerequisites

- **Python 3.9+** from [python.org](https://python.org)
- **OpenAI API key** from [platform.openai.com](https://platform.openai.com/api-keys)
- **Microphone** (for voice input)
- **Windows 10/11** (main target; also works on Mac/Linux in CLI mode)

### Optional
- **OpenWeatherMap API key** (free) for weather: [openweathermap.org/api](https://openweathermap.org/api)
- **n8n** for automation workflows: [n8n.io](https://n8n.io)

---

## 🎮 Voice Commands

| Say | Action |
|-----|--------|
| `"Open Chrome"` / `"Chrome kholo"` | Opens Google Chrome |
| `"Open VS Code"` | Opens Visual Studio Code |
| `"Search for Python tutorials"` | Google search |
| `"Mumbai ka mausam batao"` | Weather for Mumbai |
| `"Kitne baje hain?"` | Current time |
| `"Aaj kaunsa din hai?"` | Current date |
| `"Screenshot le"` | Takes screenshot |
| `"Volume badhao"` | Volume up |
| `"Calculate 25 * 48"` | Math calculation |
| `"Shutdown karo"` | Schedules PC shutdown |
| `"Bye / Alvida"` | Exit JARVIS |

---

## ⚙️ Configuration

JARVIS stores config at: `C:\Users\YourName\.jarvis\config.json`

Key settings:
```json
{
  "assistant_name": "JARVIS",
  "user_name": "Boss",
  "city": "Mumbai",
  "openai_api_key": "sk-...",
  "weather_api_key": "...",
  "hinglish_mode": true,
  "wake_word": "jarvis",
  "n8n_webhook_url": "https://your-n8n.app/webhook/jarvis"
}
```

---

## 🔗 MCP / n8n Integration

JARVIS sends POST requests to your n8n webhook:
```json
{
  "intent": "workflow_name",
  "data": { "query": "user's command" },
  "user": "Boss",
  "assistant": "JARVIS",
  "timestamp": "2024-01-01T12:00:00"
}
```

Configure the webhook URL in Settings → Integrations tab.

---

## 📁 Project Structure

```
jarvis/
├── assistant.py          # Main entry point, CLI
├── setup.py              # pip install setup
├── requirements.txt      # Python dependencies
├── start_jarvis.bat      # Windows quick launcher
├── install.ps1           # PowerShell installer
│
├── config/
│   ├── settings.py       # Config management (~/.jarvis/config.json)
│   └── setup_wizard.py   # First-time setup wizard
│
├── core/
│   ├── brain.py          # AI brain (OpenAI GPT + Hinglish prompts)
│   ├── voice_engine.py   # STT (Whisper) + TTS (pyttsx3/OpenAI)
│   └── cli_mode.py       # Terminal mode
│
├── tools/
│   └── executor.py       # App launcher, weather, web, system tools
│
└── ui/
    ├── main_window.py    # PyQt6 Iron Man HUD GUI
    └── settings_dialog.py # In-app settings panel
```

---

## 🛠️ Troubleshooting

**PyAudio install fails?**
```bash
pip install pipwin
pipwin install pyaudio
```

**No microphone detected?**
- Check Windows mic permissions: Settings → Privacy → Microphone
- JARVIS will fall back to text input automatically

**GUI doesn't open?**
```bash
pip install PyQt6
# Or use CLI mode:
assistant start --cli
```

**OpenAI API errors?**
- Verify key at platform.openai.com
- Check billing/credits
- Run `assistant setup` to re-enter key

---

## 📄 License

MIT License — Free to use, modify, and distribute.

---

*"Sometimes you gotta run before you can walk." — Tony Stark*

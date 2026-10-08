# 🤖 Telegram AI Chatbot with n8n

An AI-powered Telegram chatbot built with **n8n, Telegram, OpenAI, Simple Memory, and Gmail**.

## 🚀 Workflow

```text
Telegram User
      ↓
Telegram Trigger
      ↓
AI Agent
   ↙      ↘
OpenAI   Simple
Model    Memory
   ↘      ↙
    AI Response
        ↓
Telegram Send Message
        ↓
   Telegram User


✨ Features
- 💬 Telegram chatbot
- 🤖 OpenAI-powered AI Agent
- 🧠 Conversation memory using Simple Memory
- 📱 Sends AI responses back to Telegram
- 📧 Gmail tool connected to the AI Agent
- ⚡ Fully automated with n8n
- 🔄 Telegram chat ID used as the memory session key
🛠️ Technologies
- n8n
- Telegram Bot API
- OpenAI Chat Model
- GPT-5 mini
- n8n AI Agent
- Simple Memory
- Gmail
📋 Workflow Nodes
  Node                      Purpose
  Telegram Trigger          Receives Telegram messages
  AI Agent                  Processes the user's message and generates a response
  OpenAI Chat Model         Provides the AI model
  Simple Memory             Maintains conversation context
  Send a message in Gmail   Allows the AI Agent to send emails
  Send a text message       Sends the AI response back to Telegram
⚙️ Setup
1. Create a Telegram Bot
Open Telegram and contact @BotFather.
Run:
/newbot
Follow the instructions and copy the bot token.
Add the token to an n8n Telegram credential.
2. Configure OpenAI
Create an OpenAI API credential in n8n and connect it to the OpenAI
Chat Model node.
The current workflow uses:
gpt-5-mini
3. Configure Simple Memory
The workflow uses the Telegram chat ID as the session key:
{{ $('Telegram Trigger').item.json.message.chat.id }}
This allows separate Telegram conversations to maintain separate memory
sessions.
The workflow currently uses a context window of:
100
interactions.
4. Configure Telegram Reply
The Send a text message node sends the AI Agent output back to
Telegram.
Chat ID:
{{ $('Telegram Trigger').item.json.message.chat.id }}
Message:
{{ $('AI Agent').item.json.output }}
5. Configure Gmail
Connect your Gmail OAuth credential to the Send a message in Gmail
tool.
The AI Agent can use this tool to send an email when appropriate.
🔐 Security
Do not publish API keys, bot tokens, OAuth secrets, or other
credentials in GitHub.
Before publishing an exported n8n workflow:
- Remove or replace personal email addresses where appropriate.
- Check Telegram configuration.
- Check Gmail configuration.
- Never commit .env files containing secrets.
- Use n8n Credentials instead of hard-coding API keys.
⚠️ Before publishing this workflow
The exported workflow contains a fixed Telegram Chat ID and a fixed
Gmail recipient in its configuration. Replace these with
dynamic/user-specific values or placeholders before publishing a public
repository.
🧪 Testing
1. Activate the n8n workflow.
2. Open your Telegram bot.
3. Send:
Hello
4. The Telegram Trigger receives the message.
5. The AI Agent processes it.
6. OpenAI generates the response.
7. Simple Memory stores conversation context.
8. The Telegram node sends the response back.
Example:
User:
What is AI?

Bot:
AI stands for Artificial Intelligence...
📁 Import the Workflow
The repository can contain the exported n8n workflow:
Telegram_AI_Chatbot.json
In n8n:
Workflows
   ↓
Import from File
   ↓
Telegram_AI_Chatbot.json
After importing, reconnect/configure the required credentials.
📌 Project Structure
telegram-ai-chatbot-n8n/
│
├── Telegram_AI_Chatbot.json
├── README.md
└── screenshots/
    └── workflow.png
👨‍💻 Author
Praveen Kumar N
AI Automation | Full Stack Development | n8n | AI Agents
⭐ Future Improvements
- User email collection
- Dynamic email recipient
- Gmail response history
- Supabase/PostgreSQL user database
- WhatsApp integration
- Voice messages
- Telegram commands
- AI-generated documents
- Admin dashboard
- Production persistent memory with Redis/PostgreSQL
📄 License
This project is provided for learning and development purposes.

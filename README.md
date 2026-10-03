# 🧠 AI Flashcard Generator

An AI-powered study flashcard generator that turns notes or PDF/TXT study material into concise, structured flashcards using **Hugging Face Inference Providers**.

Built with **Python + Streamlit + Hugging Face + PyPDF + Pandas**.

## ✨ Features

- 📄 Upload **PDF** or **TXT** study material
- 📝 Paste notes directly into the app
- 🤖 Generate AI-powered flashcards from the supplied material
- 🎯 Choose the number of cards and difficulty
- 🧩 Supports Easy, Medium, Hard, or Mixed difficulty
- 📚 Review cards in an interactive Streamlit interface
- 📥 Export flashcards as **CSV** or **JSON**
- 🔐 Keep API credentials in `.env` instead of source code
- 🔄 Easily switch between supported Hugging Face chat-completion models

## 🏗️ How It Works

```text
Study Notes / PDF / TXT
          │
          ▼
   Text Extraction
          │
          ▼
 Prompt Construction
          │
          ▼
Hugging Face Inference
          │
          ▼
 Structured JSON Output
          │
          ▼
 Flashcard Validation
          │
          ▼
 Streamlit Flashcards
       │       │
       ▼       ▼
      CSV     JSON
```

## 🛠️ Tech Stack

| Technology | Purpose |
|---|---|
| Python | Application logic |
| Streamlit | Web interface |
| Hugging Face Inference Providers | AI generation |
| `huggingface_hub` | Hugging Face API client |
| PyPDF | PDF text extraction |
| Pandas | CSV export/data handling |
| python-dotenv | Environment variable management |

## 📁 Project Structure

```text
flashcard-generator-huggingface/
├── app.py                 # Main Streamlit application
├── requirements.txt       # Python dependencies
├── .env.example           # Environment-variable template
├── .gitignore             # Files excluded from Git
├── run_windows.bat        # Windows quick-start script
├── LICENSE                # MIT License
└── README.md              # Project documentation
```

## 🚀 Getting Started

### 1. Clone the repository

```bash
git clone https://github.com/YOUR_USERNAME/flashcard-generator-huggingface.git
cd flashcard-generator-huggingface
```

### 2. Create a virtual environment

**Windows**

```bash
python -m venv venv
venv\Scripts\activate
```

**macOS / Linux**

```bash
python3 -m venv venv
source venv/bin/activate
```

### 3. Install dependencies

```bash
python -m pip install --upgrade pip
pip install -r requirements.txt
```

### 4. Configure Hugging Face

Create a Hugging Face access token with permission to use the required Inference Providers functionality.

Copy `.env.example` to `.env`:

```bash
# Windows
copy .env.example .env

# macOS / Linux
cp .env.example .env
```

Then edit `.env`:

```env
HF_TOKEN=hf_your_token_here
HF_MODEL=openai/gpt-oss-120b:fastest
```

> **Security:** Never commit `.env`, API keys, or access tokens to GitHub. The repository `.gitignore` already excludes `.env`.

### 5. Run the application

```bash
streamlit run app.py
```

Or on Windows:

```bash
run_windows.bat
```

Streamlit will display a local URL in the terminal, normally:

```text
http://localhost:8501
```

## 📖 Usage

1. Start the application.
2. Upload a `.pdf` or `.txt` file, **or** paste notes into the text box.
3. Select the AI model, number of cards, and difficulty.
4. Click **Generate Flashcards**.
5. Review the generated questions and answers.
6. Download the deck as CSV or JSON.

## 🤖 Model Configuration

The default model is configured through:

```env
HF_MODEL=openai/gpt-oss-120b:fastest
```

You can replace it with another compatible chat-completion model available through your Hugging Face Inference Providers setup.

If a model/provider becomes unavailable, update `HF_MODEL` or select another supported model from the application's sidebar.

## 🔐 Environment Variables

| Variable | Required | Description |
|---|---|---|
| `HF_TOKEN` | Yes | Hugging Face access token |
| `HF_MODEL` | No | Default Hugging Face model |

Example:

```env
HF_TOKEN=hf_xxxxxxxxxxxxxxxxx
HF_MODEL=openai/gpt-oss-120b:fastest
```

## ⚠️ Limitations

- PDF extraction works with PDFs containing machine-readable text.
- Scanned/image-only PDFs may require OCR and may not produce usable text.
- Generated flashcards depend on the quality and coverage of the supplied study material.
- Hugging Face model/provider availability can change over time.
- An internet connection is required for AI generation.

## 🧪 Troubleshooting

### `HF_TOKEN is missing`

Make sure:

- A `.env` file exists in the project root.
- It contains `HF_TOKEN=...`.
- The token is valid.
- The token has the required Inference Providers permission.

### Model/provider error

Try another currently supported chat-completion model and verify your Hugging Face account/token permissions.

### PDF produces no text

The PDF may be scanned or image-only. Use a text-based PDF or add an OCR pipeline in a future version.

### Dependency/import errors

Recreate the virtual environment and reinstall:

```bash
python -m pip install --upgrade pip
pip install -r requirements.txt
```

## 🛡️ Security Notes

- Never hard-code API tokens in `app.py`.
- Never upload `.env` to GitHub.
- Never paste private access tokens into public issues, commits, screenshots, or README files.
- If a token is accidentally exposed, revoke/rotate it immediately.

## 🔮 Future Improvements

Potential extensions include:

- OCR for scanned PDFs
- Spaced-repetition learning
- User accounts and saved decks
- More export formats
- Quiz mode
- Flashcard search/filtering
- Database-backed deck history
- Additional AI providers
- Deployment with Streamlit Community Cloud or another hosting platform

## 📄 License

This project is released under the MIT License. See [`LICENSE`](LICENSE).

---

### ⭐ If this project helps you

Consider giving the repository a star and sharing improvements through a pull request.

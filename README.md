```mermaid
flowchart TD

    %% ===== INPUT LAYER =====
    A[📄 Input PDF<br/>ocean.pdf] --> B[pdf2image<br/>Convert PDF → Images]
    B --> C[pytesseract OCR<br/>Extract Raw Text]
    C --> D[Full Text Buffer]

    %% ===== INTELLIGENCE LAYER =====
    D --> E[get_dynamic_headings()<br/>Regex Heading Detection]
    D --> F[clean_text()<br/>OCR Noise Cleanup]

    E --> G[Sequential Section Engine<br/>("Finger Logic")]
    F --> G

    G --> H[summarize_block()<br/>Chunking (600 words)]
    H --> I[DistilBART Model<br/>sshleifer/distilbart-cnn-12-6]

    %% ===== OUTPUT STRUCTURING =====
    I --> J[Structured Markdown Notes<br/>### Heading + Summary]
    J --> K[handwritten_ready_notes.txt]

    %% ===== RENDERING LAYER =====
    J --> L[HandwrittenNoteRenderer<br/>FPDF2 + Custom Font]
    L --> M[Professional_Handwritten_Notes.pdf<br/>Notebook Styled Output]
```

# pdf-to-structured-notes
An OCR and summarization pipeline that transforms long academic PDFs into readable, structured notes, designed to reduce revision time and cognitive load during exam prep.

📚 Smart Notes Processor (Colab Prototype)

A Colab-based prototype that processes student notes. Students can upload PDFs or images, and the notebook extracts, analyzes, and structures the content for easy study.

Key Contributions: I designed the system architecture, problem workflows, and solution approach, ensuring the notebook produces accurate and structured outputs.

🛠 Features (Prototype)

Upload PDFs or images of notes.

OCR-based text extraction (Tesseract).

Summarization and structured output for easier reading.

Modular workflow, ready for future web deployment and potential freemium features.

💻 Tech Stack

Notebook Environment: Google Colab

Programming Language: Python

Libraries: pytesseract, OpenCV, pandas, numpy, OpenAI APIs (optional)

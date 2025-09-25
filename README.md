graph TD
    subgraph "Phase 1: User Input & Pre-processing"
        A(Start) --> B{Choose Input Method};
        B --> B1[Paste Text Directly];
        B --> B2["Upload a File (.pdf, .txt, .docx)"];
        B --> B3[Enter a Web URL];

        B1 --> C[Extract Text];
        B2 --> C;
        B3 --> C;

        C --> D{Is Text Extracted Successfully?};
        D -- No --> E["Display Error Message to User<br/>'Invalid file or URL'"];
        E --> Z(End);
    end

    subgraph "Phase 2: Core Summarization Logic"
        D -- Yes --> F[Clean and Prepare Text];
        F --> G["User Selects Summarization Options<br/>- Length (Short, Medium, Long)<br/>- Style (Paragraph, Bullet Points)"];
        G --> H["Construct Final Prompt for LLM API<br/>(Includes cleaned text + user options)"];
        H --> I["Send API Request to Chosen LLM<br/>(e.g., Claude, GPT, Gemini, Llama 3)"];
    end

    subgraph "Phase 3: Output & User Interaction"
        I --> J{Receive Response from LLM};
        J -- API Error --> K["Handle Error<br/>(e.g., timeout, content filter) and Notify User"];
        K --> Z;

        J -- Success --> L[Parse the Response to Get Summary];
        L --> M[Display Generated Summary on UI];
        M --> N{User Action};

        N --> N1[Copy Summary to Clipboard];
        N --> N2["Download Summary as .txt file"];
        N --> N3[Start a New Summary];
        N3 --> B;
    end

    Z(End);

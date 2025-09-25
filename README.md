
following is the flowchart:


graph TD
    A(Start) --> B{Choose Input Method};
    B --> B1[Paste Text Directly];
    B --> B2["Upload a File (e.g., .pdf, .txt, .docx)"];
    B --> B3[Enter a Web URL];

    B1 --> C[Extract Text];
    B2 --> C;
    B3 --> C;

    C --> D{Is Text Extracted Successfully?};
    D -- No --> E[Display Error: Invalid Input];
    E --> Z(End);

    D -- Yes --> F[Clean and Prepare Text];
    F --> G[User Selects Summarization Options];
    G --> H[Construct Final Prompt for LLM API];
    H --> I[Send API Request to Chosen LLM];

    I --> J{Receive Response from LLM};
    J -- API Error --> K[Handle Error and Notify User];
    K --> Z;

    J -- Success --> L[Parse the Response to Get Summary];
    L --> M[Display Generated Summary on UI];
    M --> N{User Action};

    N --> N1[Copy Summary to Clipboard];
    N --> N2[Download Summary as .txt file];
    N --> N3[Start a New Summary];
    N3 --> B;
    Z(End);

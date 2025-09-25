graph TD
    A(Start) --> B{Choose Input Method};
    B --> B1[Paste Text Directly];
    B --> B2["Upload File (.pdf, .txt)"];
    B --> B3[Enter Web URL];

    B1 --> C[Extract Text];
    B2 --> C;
    B3 --> C;

    C --> D{Is Text Valid?};
    D -- No --> E["Display Invalid Input Error"];
    E --> Z(End);

    D -- Yes --> F[Clean Text];
    F --> G["User Selects Summary Options"];
    G --> H["Construct LLM Prompt"];
    H --> I["Send Request to LLM API"];

    I --> J{Receive Response};
    J -- Error --> K["Handle API Error"];
    K --> Z;

    J -- Success --> L[Parse Summary];
    L --> M[Display Summary on UI];
    M --> N{User Action};

    N --> N1[Copy Summary];
    N --> N2[Download Summary];
    N --> N3[Start New Summary];

    N3 --> B;
    Z(End);

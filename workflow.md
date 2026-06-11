
flowchart TD
    classDef data stroke:#2dd4bf,fill:#f0fdfa
    classDef process stroke:#a78bfa,fill:#f5f3ff
    classDef output stroke:#fb923c,fill:#fff7ed
    classDef app stroke:#4ade80,fill:#f0fdf4
    classDef dashboard stroke:#38bdf8,fill:#f0f9ff

    subgraph Inputs
        A[Google Sheet: Exercise Database]:::data
        B[SQL DB: Workout Log]:::data
        C[SQL DB: Wearable Data]:::data
        D[Static Config: Goals & Resources]:::data
    end

    E["Decision Engine (Generates personalized workout plan)"]:::process
    F[Personalized Workout Plan]:::output
    G["Android JavaScript App (User input: weights, notes, issues)"]:::app
    H["Dashboard (Plotly Dash / R Shiny)"]:::dashboard

    %% Main flow
    A --> E
    B --> E
    C --> E
    D --> E
    E --> F
    F --> G
    G --> B

    %% Data visualization
    B --> H
    C --> H

    %% Feedback loops
    B -. updated logs .-> E
    C -. updated metrics .-> E
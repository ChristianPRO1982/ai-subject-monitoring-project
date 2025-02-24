# ai-subject-monitoring-project
AI Subject Monitoring Project with mermaid

## Global workflow

``````mermaid
graph LR
    subgraph start[Linux machin]
        a((b))
    end
``````

## watch-podcast-download

### Overview diagram

```mermaid
graph TB
    subgraph start[Linux machin]
        subgraph chrontab[Chrontab]
            A((Chrontab))

            style chrontab fill:#556
        end

        style start fill:#444
    end

    subgraph step1[topics by podcasts]
        subgraph watch-podcast-download
            A ==>|main.py| B[01: parse feeds RSS]:::python
            B -.-> C[(podcastdb.sqlite)]:::sqlite
            B ==> D[02: download mp3]:::python
            C <-.-> D
            D -->|create 📝| E[\🎧 XX_podcast.mp3\]:::file
            D ==> F[03: transcribe]:::python
            C <-.-> F
            F -->|create 📝| G[/📄 XX_podcast.txt/]:::file
            F -->|delete 🗑️| E
            F ==> H[04: summarize]:::python
            C <-.-> H

            style watch-podcast-download fill:#556
        end
        
        subgraph transcription-API
            F <--> N[main.py: transcribe]:::fastapi

            style transcription-API fill:#556
        end
        
        H <-->|role: str + prompt: str| O[OpenAI API]:::openai

        style step1 fill:#444
        style E fill:#A00,color:#F99
    end

    H ==> I((END))

    subgraph Legend [Legend]
        subgraph package[Developed package]
            example((example))

            style package fill:#556
        end

        L1[python scripts]:::python
        L2[FastAPI]:::fastapi
        L3[OpenAI]:::openai
        L4[SQLite]:::sqlite
        Lf1[/files/]:::file
        Lf2[\temporary file\]:::file

        style Legend fill:#999, color:#000
    end

    classDef python fill:#FFDC52, color:#000;
    classDef fastapi fill:#059286, color:#45D2C6
    classDef openai fill:#FFF, color:#000;
    classDef sqlite fill:#0F80CC, color:#4FC0FC
    classDef file fill:#BBB,color:#333
``````

### I/O API: transcription-API

``````mermaid
sequenceDiagram
    participant watch-podcast-download
    participant transcription-API
    watch-podcast-download->>transcription-API: API Request [POST]: file_path: str
    transcription-API-->>watch-podcast-download: JSON: {"file_name", "date_time", "processing_time", "transcription_text": text, "error"}
``````

### I/O API: OpenAI API

``````mermaid
sequenceDiagram
    participant watch-podcast-download
    participant OpenAI
    watch-podcast-download->>OpenAI: Request API: role / prompt [= pre-prompt + transcribe]
    OpenAI-->>watch-podcast-download: message
``````
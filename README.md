# AI SUBJECT MONITORING PROJECT
AI Subject Monitoring Project with mermaid

## Legend

``````mermaid
graph LR
    subgraph Legend [Legend]
        subgraph package[Developed package]
            example1((example))

            style package fill:#556, color:#FFF
        end

        subgraph not-package[Not developed package]
            example2((example))

            style not-package fill:#444, color:#FFF
        end

        L1[python scripts]:::python
        L2[Linux shell]:::shell
        L3[FastAPI]:::fastapi
        L4[OpenAI]:::openai
        L5[(MySQL)]:::mysql
        L6[(SQLite)]:::sqlite
        Lf1[/files/]:::file
        Lf2[\temporary file\]:::file

        style Legend fill:#999, color:#000
    end
    

    classDef python fill:#FFDC52, color:#000;
    classDef fastapi fill:#059286, color:#45D2C6
    classDef openai fill:#FFF, color:#000;
    classDef mysql fill:#00618B, color:#40A1CB
    classDef sqlite fill:#0F80CC, color:#4FC0FC
    classDef shell fill:#000, color:#49F75C
    classDef file fill:#BBB, color:#333
``````

## Global workflow

``````mermaid
graph LR
    subgraph start[Linux machin]
        subgraph chrontab[Chrontab]
            A((Chrontab: weekly))
            
            style chrontab fill:#556, color:#FFF
        end

        subgraph scripts[Shell scripts]
            A --> B[watch-podcast-download]:::shell
            A --> C[Scraping-latest-posts-from-news-sites]:::shell
            A --> D[ChrisAI-research]:::shell
            A --> E[veille-IA-CR-auto]:::shell
            A --> F[newsletter]:::shell
            
            style scripts fill:#556, color:#FFF
        end

        style start fill:#444, color:#FFF

        subgraph subg-b[topics by podcasts]
            B --> subg-b-A[main.py]:::python

            style subg-b fill:#556, color:#FFF
        end

        subgraph subg-c[Scraping news sites]
            C --> subg-c-A[main.py]:::python

            style subg-c fill:#556, color:#FFF
        end

        subgraph subg-d[Manage newsletters]
            D --> subg-d-A[main.py]:::python

            style subg-d fill:#556, color:#FFF
        end

        subgraph subg-e[Veille outils IA]
            E --> subg-e-A[main.py]:::python

            style subg-e fill:#556, color:#FFF
        end

        subgraph transcription-API
            subg-b-A <--> subg-APIs-A[main.py: transcribe]:::fastapi

            style transcription-API fill:#556, color:#FFF
        end

        subgraph subg-mysql[Global DB]
            subg-b-A --> subg-mysql-A[(ai-subject-monitoring)]:::mysql
            subg-c-A --> subg-mysql-A
            subg-d-A --> subg-mysql-A
            subg-e-A --> subg-mysql-A

            style subg-mysql fill:#556, color:#FFF
        end

        subgraph subg-f[Newsletter]
            F --> subg-f-A[main.py]:::python
            subg-mysql-A --> subg-f-A
            subg-f-A --> subg-f-B((Send newsletter))

            style subg-f fill:#556, color:#FFF
        end
    end

    subgraph APIs
        subgraph OpenAI-API
            subg-b-A <--> subg-APIs-B[main.py: summarize]:::openai

            style OpenAI-API fill:#444, color:#FFF
        end

        style APIs fill:#444, color:#FFF
    end


    classDef python fill:#FFDC52, color:#000;
    classDef fastapi fill:#059286, color:#45D2C6
    classDef openai fill:#FFF, color:#000;
    classDef mysql fill:#00618B, color:#40A1CB
    classDef sqlite fill:#0F80CC, color:#4FC0FC
    classDef shell fill:#000, color:#49F75C
    classDef file fill:#BBB, color:#333
``````

## watch-podcast-download

### Overview diagram

```mermaid
graph TB
    subgraph chrontab[Chrontab]
        A((Chrontab))

        style chrontab fill:#556, color:#FFF
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
            H ==> I[05: Global DB]:::python
            I ==> J((END))

            style watch-podcast-download fill:#556, color:#FFF
        end
        
        subgraph transcription-API
            F <--> N[main.py: transcribe]:::fastapi

            style transcription-API fill:#556, color:#FFF
        end
        
        H <--> O[OpenAI API]:::openai

        subgraph subg-mysql[Global DB]
            I -.-> subg-mysql-A[(ai-subject-monitoring)]:::mysql

            style subg-mysql fill:#556, color:#FFF
        end

        style step1 fill:#444, color:#FFF
        style E fill:#A00,color:#F99
    end


    classDef python fill:#FFDC52, color:#000;
    classDef fastapi fill:#059286, color:#45D2C6
    classDef openai fill:#FFF, color:#000;
    classDef mysql fill:#00618B, color:#40A1CB
    classDef sqlite fill:#0F80CC, color:#4FC0FC
    classDef file fill:#BBB, color:#333
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
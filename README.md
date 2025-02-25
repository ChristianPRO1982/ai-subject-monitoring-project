# AI SUBJECT MONITORING PROJECT
AI Subject Monitoring Project with mermaid

## Legend

``````mermaid
graph LR
    subgraph Legend [Legend]
        style Legend fill:#DDD, color:#000

        subgraph package[Developed package]
            style package fill:#88A, color:#FFF
            example1((example))
        end

        subgraph not-package[Not developed package]
            style not-package fill:#555, color:#FFF
            example2((example))
        end

        L1[python scripts]:::python
        L2[Linux shell]:::shell
        L3[FastAPI]:::fastapi
        L4[OpenAI]:::openai
        L5[(MySQL)]:::mysql
        L6[(SQLite)]:::sqlite
        Lf1[/files/]:::file
        Lf2[\temporary file\]:::file
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
    subgraph machine[Linux machine]
        style machine fill:#777, color:#FFF

        subgraph crontab[Crontab]
            style crontab fill:#88A, color:#FFF
            A((Crontab: weekly))
        end

        subgraph scripts[Shell scripts]
            style scripts fill:#88A, color:#FFF
            
            A --> B[watch-podcast-downloader]:::shell
            A --> C[Scrape-latest-posts-from-news-sites]:::shell
            A --> D[ChrisAI-research]:::shell
            A --> E[veille-IA-CR-auto]:::shell
            A --> F[newsletter]:::shell
        end


        subgraph subg-b[Podcast Watchdog]
            style subg-b fill:#88A, color:#FFF
            B --> subg-b-A[main.py]:::python
        end

        subgraph subg-c[Scraping news sites]
            style subg-c fill:#88A, color:#FFF
            C --> subg-c-A[main.py]:::python
        end

        subgraph subg-d[Manage newsletters]
            style subg-d fill:#88A, color:#FFF
            D --> subg-d-A[main.py]:::python
        end

        subgraph subg-e[Veille outils IA]
            style subg-e fill:#88A, color:#FFF
            E --> subg-e-A[main.py]:::python
        end

        subgraph transcription-API
            style transcription-API fill:#88A, color:#FFF
            subg-b-A <--> subg-APIs-A[main.py: transcribe]:::fastapi
        end

        subgraph subg-mysql[Global DB]
            style subg-mysql fill:#88A, color:#FFF

            subg-b-A --> subg-mysql-A[(ai-subject-monitoring)]:::mysql
            subg-c-A --> subg-mysql-A
            subg-d-A --> subg-mysql-A
            subg-e-A --> subg-mysql-A
        end

        subgraph subg-f[Newsletter]
            style subg-f fill:#88A, color:#FFF

            F --> subg-f-A[main.py]:::python
            subg-mysql-A --> subg-f-A
            subg-f-A --> subg-f-B((Send newsletter))
        end
    end

    subgraph APIs
        style APIs fill:#777, color:#FFF
        subgraph OpenAI-API
            style OpenAI-API fill:#555, color:#FFF
            subg-b-A <--> subg-APIs-B[main.py: summarize]:::openai
        end
    end


    classDef python fill:#FFDC52, color:#000;
    classDef fastapi fill:#059286, color:#45D2C6
    classDef openai fill:#FFF, color:#000;
    classDef mysql fill:#00618B, color:#40A1CB
    classDef sqlite fill:#0F80CC, color:#4FC0FC
    classDef shell fill:#000, color:#49F75C
    classDef file fill:#BBB, color:#333
``````

## Podcast Watchdog

### Overview diagram

```mermaid
graph TB
    subgraph machine[Linux machine]
        style machine fill:#777, color:#FFF
        
        subgraph chrontab[Chrontab]
            style chrontab fill:#88A, color:#FFF
            A((Chrontab))
        end

        subgraph pw[Podcast Watchdog]
            style pw fill:#88A, color:#FFF

            ai-json[/ai_rss_feeds.json/]:::file
            prompt-json[/ai_rss_prompts.json/]:::file

            A ==>|main.py| B[01: parse feeds RSS - utils_parse_rss.py ParseRSS]:::python
            B ==> C[02: download mp3 - utils_podcast.py Podcasts.download_podcasts]:::python
            C ==> D[03: transcribe - utils_podcast.py Podcasts.transcribe_podcasts]:::python
            D ==> E[04: summarize - utils_podcast.py Podcasts.summarize_podcasts]:::python
            E ==> F[05: Global DB]:::python
            F ==> G((END))
            B <--> ai-json
            D <--> prompt-json
            B -.-> H[(podcastdb.sqlite)]:::sqlite
            C <-.-> H
            D <-.-> H
            E <-.-> H
            C -->|📝 create| I[\🎧 XX_podcast.mp3\]:::file
            D -->|📝 create| J[/📄 XX_podcast.txt/]:::file
            D -->|🗑️ delete| I
        end
        
        subgraph transcription-API
            style transcription-API fill:#88A, color:#FFF
            C <--> N[main.py: transcribe]:::fastapi
        end
        
        subgraph subg-mysql[Global DB]
            F -.-> subg-mysql-A[(ai-subject-monitoring)]:::mysql
            style subg-mysql fill:#88A, color:#FFF
        end
    end

    subgraph openai[OpenAI]
        style openai fill:#555, color:#FFF
        D <--> O[API]:::openai
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
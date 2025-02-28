# AI SUBJECT MONITORING PROJECT
AI Subject Monitoring Project with mermaid

[![Latest Release](https://img.shields.io/github/release/ChristianPRO1982/ai-subject-monitoring-project.svg)](https://github.com/ChristianPRO1982/ai-subject-monitoring-project/releases/latest)
[![Python](https://img.shields.io/badge/python-3.10%2B-blue.svg)](https://www.python.org/)
[![License](https://img.shields.io/github/license/ChristianPRO1982/ai-subject-monitoring-project.svg)](https://github.com/ChristianPRO1982/ai-subject-monitoring-project/blob/main/LICENSE)

<details>

  <summary><strong>📌 Table of Contents</strong></summary>

  * [Legend](#legend)
  * [Global workflow](#global-workflow)

| Linux machine | Podcast Watchdog | Transcrib API | News sites | Manage newsletters | ChrisAI-research | Monitoring AI tools | newsletter | Global DB |
|---------------|------------------|---------------|------------|--------------------|------------------|---------------------|------------|-----------|
| [Linux machine](#linux-machine) | [Podcast Watchdog](#podcast-watchdog) | [Transcribe API](#transcribe-api) | [Scraping news sites](#scraping-news-sites) | [Manage newsletters](#manage-newsletters) | [ChrisAI-research](#chrisai-research) | [Monitoring AI tools](#monitoring-ai-tools) | [Global DB](#global-db) | [Newsletter](#newsletter) |
| [Linux crontab](#linux-crontab) | [Flowchart](#flowchart) |
| [Shell scripts](#shell-scripts) | [I/O API: transcription-API](#io-api-transcription-api) |
|| [I/O API: OpenAI API](#io-api-openai-api) |
</details>

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

        subgraph dev[🚧 under construction 🚧]
            style dev fill:#363, color:#FFF
            example3((example))
        end

        L1[python scripts]:::python
        L2[Linux shell]:::shell
        L3[FastAPI]:::fastapi
        L4[OpenAI]:::openai
        L5[(MySQL)]:::mysql
        L6[(SQLite)]:::sqlite
        Lf1[/📃 files/]:::file
        Lf2[\📃 temporary file\]:::tfile
    end
    

    classDef python fill:#FFDC52, color:#000;
    classDef fastapi fill:#059286, color:#45D2C6
    classDef openai fill:#FFF, color:#000;
    classDef mysql fill:#00618B, color:#40A1CB
    classDef sqlite fill:#4FC0FC, color:#0F80CC
    classDef shell fill:#000, color:#49F75C
    classDef file fill:#BBB, color:#333
    classDef tfile fill:#888, color:#333
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
            
            A --> B[Podcast Watchdog]:::shell
            A --> C[Scrape-latest-posts-from-news-sites]:::shell
            A --> D[manage-newsletters]:::shell
            A --> E[ChrisAI-research]:::shell
            A --> F[newsletter]:::shell
        end


        subgraph subg-b[Podcast Watchdog]
            style subg-b fill:#88A, color:#FFF

            B -->|main.py| subg-b-A[python POO]:::python

            subg-b-A <-.-> dbpodcast[(podcast.db)]:::sqlite
            subg-b-A <--> transcribe[/📂 podcast_transcribed.txt/]:::file
        end

        subgraph subg-c[Scraping news sites]
            style subg-c fill:#363, color:#FFF
            C -->|main.py| subg-c-A[🚧 under construction 🚧]:::python
        end

        subgraph subg-d[Manage newsletters]
            style subg-d fill:#363, color:#FFF
            D -->|main.py| subg-d-A[🚧 under construction 🚧]:::python
        end

        subgraph subg-e[ChrisAI-research]
            style subg-e fill:#363, color:#FFF
            E -->|main.py| subg-e-A[🚧 under construction 🚧]:::python
        end

        subgraph subg-g[Monitoring AI tools]
            style subg-g fill:#88A, color:#FFF
            G((manual launch)) --> subg-g-A[python]:::python
        end

        subgraph transcription-API
            style transcription-API fill:#88A, color:#FFF
            subg-b-A <-->|EndPoint:transcribe| subg-APIs-A[main.py: transcribe]:::fastapi
        end

        subgraph subg-mysql[Global DB]
            style subg-mysql fill:#363, color:#FFF
            info1[🚧 under construction 🚧]
            subg-b-A -.-> subg-mysql-A[(ai-subject-monitoring)]:::mysql
            subg-c-A -.-> subg-mysql-A
            subg-d-A -.-> subg-mysql-A
            subg-e-A -.-> subg-mysql-A
            subg-g-A -.-> subg-mysql-A
        end

        subgraph subg-f[Newsletter]
            style subg-f fill:#363, color:#FFF
            
            F -->|main.py| subg-f-A[🚧 under construction 🚧]:::python
            subg-mysql-A -.-> subg-f-A
            subg-f-A --> subg-f-B((Send newsletter))
        end
    end

    subgraph APIs[external APIs]
        style APIs fill:#777, color:#FFF
        
        subgraph OpenAI-API
            style OpenAI-API fill:#555, color:#FFF
            subg-b-A <-->|role + prompt > txt| subg-APIs-B(openai):::openai
        end
    end


    classDef python fill:#FFDC52, color:#000;
    classDef fastapi fill:#059286, color:#45D2C6
    classDef openai fill:#FFF, color:#000;
    classDef mysql fill:#00618B, color:#40A1CB
    classDef sqlite fill:#4FC0FC, color:#0F80CC
    classDef shell fill:#000, color:#49F75C
    classDef file fill:#BBB, color:#333
    classDef tfile fill:#888, color:#333
``````

## Linux machine

### Linux crontab



### Shell scripts



## Podcast Watchdog

### Flowchart

```mermaid
graph LR
    goto-project
    click goto-project "https://github.com/ChristianPRO1982/podcast-watchdog"
    style goto-project fill:#000, color:#00F
    
    subgraph openai[OpenAI]
        style openai fill:#555, color:#FFF
        O[API]:::openai
    end
    
    subgraph machine[Linux machine]
        style machine fill:#777, color:#FFF
        
        subgraph linux[Linux]
            style linux fill:#555, color:#FFF
            A((Chrontab))
        end

        subgraph pw[Podcast Watchdog]
            style pw fill:#88A, color:#FFF
            
            ai-json[/⚙️ ai_rss_feeds.json/]:::file
            prompt-json[/⚙️ ai_rss_prompts.json/]:::file

            subgraph SQLite
                style SQLite fill:#88A, color:#FFF
                H[(podcast.db)]:::sqlite
            end

            subgraph of[output folder]
                style of fill:#88A, color:#FFF
                J[/📄 XX_podcast.txt/]:::file
                I[\🎧 XX_podcast.mp3\]:::tfile
            end

            A ==> main[main.py]:::python
            main ==> B[01: parse feeds RSS - utils_parse_rss.py ParseRSS]:::python
            main ==> C[02: download mp3 - utils_podcast.py Podcasts.download_podcasts]:::python
            main ==> D[03: transcribe - utils_podcast.py Podcasts.transcribe_podcasts]:::python
            main ==> E[04: summarize - utils_podcast.py Podcasts.summarize_podcasts]:::python
            main ==> F[05: Global DB]:::python
            ai-json --> B
            prompt-json --> E
            B -.->|INSERT| H
            C <-.->|SELECT + UPDATE| H
            D <-.->|SELECT + UPDATE| H
            E <-.->|SELECT + UPDATE| H
            E <-->|role + prompt > txt| O[API]:::openai
            C -->|📝 create| I
            D -->|📝 create| J
            D -->|🗑️ delete| I
        end
        
        subgraph transcription-API
            style transcription-API fill:#555, color:#FFF
            D <-->|EndPoint:transcribe| N[main.py: transcribe]:::fastapi
            N -->|👁️‍🗨️ read| I
        end
        
        subgraph subg-mysql[Global DB]
            style subg-mysql fill:#363, color:#FFF

            F -.->|INSERT| subg-mysql-A[(🚧ai-subject-monitoring🚧)]:::mysql
            F -.->|SELECT| H
        end
    end


    classDef python fill:#FFDC52, color:#000;
    classDef fastapi fill:#059286, color:#45D2C6
    classDef openai fill:#FFF, color:#000;
    classDef mysql fill:#00618B, color:#40A1CB
    classDef sqlite fill:#4FC0FC, color:#0F80CC
    classDef file fill:#BBB, color:#333
    classDef tfile fill:#888, color:#333
``````

### I/O API: transcription-API

``````mermaid
sequenceDiagram
    participant podcast-watchdog
    participant transcription-API
    podcast-watchdog->>transcription-API: API Request [POST]: file_path: str
    transcription-API-->>podcast-watchdog: JSON: {"file_name", "date_time", "processing_time", "transcription_text": text, "error"}
``````

### I/O API: OpenAI API

``````mermaid
sequenceDiagram
    participant podcast-watchdog
    participant OpenAI
    podcast-watchdog->>OpenAI: Request API: role / prompt [= pre-prompt + transcribe]
    OpenAI-->>podcast-watchdog: message
``````

## Transcribe API

### Flowchart

```mermaid
graph LR
    goto-project
    click goto-project "https://github.com/ChristianPRO1982/transcription-API"
    style goto-project fill:#000, color:#00F

    subgraph machine[Linux machine]
        style machine fill:#777, color:#FFF
        
        subgraph app
            style app fill:#555, color:#FFF
            A((call))
        end

        subgraph ta[Transcribe API]
            style ta fill:#88A, color:#FFF

            A ==>|file_path: str| EP-TRANSCRIBE["ENDPOINT Transcribe [POST]"]:::python
            EP-TRANSCRIBE -.->|"json:file_name / file_name / date_time / processing_time / transcription_text / error"| A

            EP-TRANSCRIBE -->|"file_path: str"| UTILS["utils.py transcription_text()"]:::python
            UTILS -->|"(text, error)"| EP-TRANSCRIBE

            UTILS <--> WHISPER["model = whisper.load_model('base')"]
        end
    end


    classDef python fill:#FFDC52, color:#000;
    classDef fastapi fill:#059286, color:#45D2C6
    classDef openai fill:#FFF, color:#000;
    classDef mysql fill:#00618B, color:#40A1CB
    classDef sqlite fill:#4FC0FC, color:#0F80CC
    classDef file fill:#BBB, color:#333
    classDef tfile fill:#888, color:#333
``````

## Scraping news sites

### Flowchart

```mermaid
graph LR
    goto-project
    click goto-project "https://github.com/ChristianPRO1982/scraping-news-sites"
    style goto-project fill:#000, color:#00F

    subgraph machine[Linux machine]
        style machine fill:#777, color:#FFF
        
        init
    end


    classDef python fill:#FFDC52, color:#000;
    classDef fastapi fill:#059286, color:#45D2C6
    classDef openai fill:#FFF, color:#000;
    classDef mysql fill:#00618B, color:#40A1CB
    classDef sqlite fill:#4FC0FC, color:#0F80CC
    classDef file fill:#BBB, color:#333
    classDef tfile fill:#888, color:#333
``````

## Manage newsletters

### Flowchart

```mermaid
graph LR
    goto-project
    click goto-project "https://github.com/ChristianPRO1982/watch-podcast-download"
    style goto-project fill:#000, color:#00F

    subgraph machine[Linux machine]
        style machine fill:#777, color:#FFF
        
        init
    end


    classDef python fill:#FFDC52, color:#000;
    classDef fastapi fill:#059286, color:#45D2C6
    classDef openai fill:#FFF, color:#000;
    classDef mysql fill:#00618B, color:#40A1CB
    classDef sqlite fill:#4FC0FC, color:#0F80CC
    classDef file fill:#BBB, color:#333
    classDef tfile fill:#888, color:#333
``````

## ChrisAI-research

### Flowchart

```mermaid
graph LR
    goto-project
    click goto-project "https://github.com/ChristianPRO1982/ChrisAI-research"
    style goto-project fill:#000, color:#00F

    subgraph machine[Linux machine]
        style machine fill:#777, color:#FFF
        
        init
    end


    classDef python fill:#FFDC52, color:#000;
    classDef fastapi fill:#059286, color:#45D2C6
    classDef openai fill:#FFF, color:#000;
    classDef mysql fill:#00618B, color:#40A1CB
    classDef sqlite fill:#4FC0FC, color:#0F80CC
    classDef file fill:#BBB, color:#333
    classDef tfile fill:#888, color:#333
``````

## Monitoring AI tools

### Flowchart

```mermaid
graph LR
    goto-project
    click goto-project "https://github.com/ChristianPRO1982/monitoring-ai-tools"
    style goto-project fill:#000, color:#00F

    subgraph machine[Linux machine]
        style machine fill:#777, color:#FFF
        
        init
    end


    classDef python fill:#FFDC52, color:#000;
    classDef fastapi fill:#059286, color:#45D2C6
    classDef openai fill:#FFF, color:#000;
    classDef mysql fill:#00618B, color:#40A1CB
    classDef sqlite fill:#4FC0FC, color:#0F80CC
    classDef file fill:#BBB, color:#333
    classDef tfile fill:#888, color:#333
``````

## Global DB

### Flowchart

```mermaid
graph LR
    goto-project
    click goto-project "https://github.com/ChristianPRO1982/watch-podcast-download"
    style goto-project fill:#000, color:#00F

    subgraph machine[Linux machine]
        style machine fill:#777, color:#FFF
        
        init
    end


    classDef python fill:#FFDC52, color:#000;
    classDef fastapi fill:#059286, color:#45D2C6
    classDef openai fill:#FFF, color:#000;
    classDef mysql fill:#00618B, color:#40A1CB
    classDef sqlite fill:#4FC0FC, color:#0F80CC
    classDef file fill:#BBB, color:#333
    classDef tfile fill:#888, color:#333
``````

## Newsletter

### Flowchart

```mermaid
graph LR
    goto-project
    click goto-project "https://github.com/ChristianPRO1982/watch-podcast-download"
    style goto-project fill:#000, color:#00F

    subgraph machine[Linux machine]
        style machine fill:#777, color:#FFF
        
        init
    end


    classDef python fill:#FFDC52, color:#000;
    classDef fastapi fill:#059286, color:#45D2C6
    classDef openai fill:#FFF, color:#000;
    classDef mysql fill:#00618B, color:#40A1CB
    classDef sqlite fill:#4FC0FC, color:#0F80CC
    classDef file fill:#BBB, color:#333
    classDef tfile fill:#888, color:#333
``````
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
            A --> D[ChrisAI-research]:::shell
            A --> E[veille-IA-CR-auto]:::shell
            A --> F[Monitoring AI tools]:::shell
            A --> G[newsletter]:::shell
        end


        subgraph subg-b[Podcast Watchdog]
            style subg-b fill:#88A, color:#FFF

            B -->|main.py| subg-b-A[python POO]:::python

            dbpodcast[(podcast.db)]:::sqlite
            transcribe[/📂 podcast_transcribed.txt/]:::file
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

        subgraph subg-f[Monitoring AI tools]
            style subg-f fill:#363, color:#FFF
            F -->|main.py| subg-f-A[🚧 under construction 🚧]:::python
        end

        subgraph transcription-API
            style transcription-API fill:#88A, color:#FFF
            subg-b-A <--> subg-APIs-A[main.py: transcribe]:::fastapi
        end

        subgraph subg-mysql[Global DB]
            style subg-mysql fill:#363, color:#FFF
            info1[🚧 under construction 🚧]
            subg-b-A --> subg-mysql-A[(ai-subject-monitoring)]:::mysql
            subg-c-A --> subg-mysql-A
            subg-d-A --> subg-mysql-A
            subg-e-A --> subg-mysql-A
            subg-f-A --> subg-mysql-A
        end

        subgraph subg-g[Newsletter]
            style subg-g fill:#363, color:#FFF
            
            G -->|main.py| subg-g-A[🚧 under construction 🚧]:::python
            subg-mysql-A --> subg-g-A
            subg-g-A --> subg-g-B((Send newsletter))
        end
    end

    subgraph APIs[external APIs]
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
    classDef sqlite fill:#4FC0FC, color:#0F80CC
    classDef shell fill:#000, color:#49F75C
    classDef file fill:#BBB, color:#333
    classDef tfile fill:#888, color:#333
``````

## Podcast Watchdog

### Flowchart

```mermaid
graph LR
    goto-project
    click goto-project "https://github.com/ChristianPRO1982/podcast-watchdog"
    style goto-project fill:#000, color:#00F

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

            A ==> main[main.py]:::python
            main ==> B[01: parse feeds RSS - utils_parse_rss.py ParseRSS]:::python
            main ==> C[02: download mp3 - utils_podcast.py Podcasts.download_podcasts]:::python
            main ==> D[03: transcribe - utils_podcast.py Podcasts.transcribe_podcasts]:::python
            main ==> E[04: summarize - utils_podcast.py Podcasts.summarize_podcasts]:::python
            main ==> F[05: Global DB]:::python
            ai-json --> B
            prompt-json --> D
            B -.->|INSERT| H[(podcast.db)]:::sqlite
            C <-.->|SELECT + UPDATE| H
            D <-.->|SELECT + UPDATE| H
            E <-.->|SELECT + UPDATE| H
            C -->|📝 create| I[\🎧 XX_podcast.mp3\]:::tfile
            D -->|📝 create| J[/📄 XX_podcast.txt/]:::file
            D <-->|👁️‍🗨️ read & 🗑️ delete| I
        end
        
        subgraph transcription-API
            style transcription-API fill:#555, color:#FFF
            D <--> N[main.py: transcribe]:::fastapi
        end
        
        subgraph subg-mysql[Global DB]
            style subg-mysql fill:#363, color:#FFF

            F -.->|INSERT| subg-mysql-A[(ai-subject-monitoring)]:::mysql
            H -.->|SELECT| F
        end
    end

    subgraph openai[OpenAI]
        style openai fill:#555, color:#FFF
        E <--> O[API]:::openai
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
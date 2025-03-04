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

```mermaid
graph LR
    subgraph Legend [Legend]
        style Legend fill:#777, color:#000

        subgraph machine
            style machine fill:#777, color:#FFF
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
        end

        subgraph code
            style code fill:#777, color:#000
            
            L1[python scripts]:::python
            L2[Linux shell]:::shell
            L3[FastAPI]:::fastapi
            L4[OpenAI]:::openai
        end

        subgraph DBMS
            style DBMS fill:#777, color:#000

            L5[(MySQL)]:::mysql
            L6[(SQLite)]:::sqlite
        end

        subgraph files
            style files fill:#777, color:#000

            Lf1@{ shape: doc, label: "📄 File" }
            Lf1:::file
            Lf2@{ shape: docs, label: "📃 files" }
            Lf2:::file
            Lf3@{ shape: docs, label: "📃 temporary files" }
            Lf3:::tfile
        end

        subgraph actions[Actions emoji]
            style actions fill:#777, color:#000

            a1(SQL SELECT) -->|👁️‍🗨️| a2(Database)
            a3(SQL INSERT) -->|🆕| a4(Database)
            a5(SQL UPDATE) -->|🔄| a6(Database)
            a7(SQL DELETE) -->|🗑️| a8(Database)
        end

        subgraph sql[SQL emoji : SIUD]
            style sql fill:#777, color:#000

            s1(SQL SELECT) -.->|🎯| s2[(Database)]:::mysql
            s3(SQL INSERT) -.->|🌱| s4[(Database)]:::sqlite
            s5(SQL UPDATE) -.->|🚀| s6[(Database)]:::mysql
            s7(SQL DELETE) -.->|⚰️| s8[(Database)]:::sqlite
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
```

## Global workflow

```mermaid
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
            subg-b-A <--> transcribe@{ shape: docs, label: "📃 XX_podcast.txt" }
            transcribe:::file
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
            info1[/🚧 under construction 🚧/]
            subg-b-A -.->|🌱| subg-mysql-A[(ai-subject-monitoring)]:::mysql
            subg-c-A -.->|🌱| subg-mysql-A
            subg-d-A -.->|🌱| subg-mysql-A
            subg-e-A -.->|🌱| subg-mysql-A
            subg-g-A -.->|🌱| subg-mysql-A
        end

        subgraph subg-f[Newsletter]
            style subg-f fill:#363, color:#FFF
            
            F -->|main.py| subg-f-A[🚧 under construction 🚧]:::python
            subg-f-A -.->|🎯🚀| subg-mysql-A
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
```

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

    subgraph APIs[external APIs]
        style APIs fill:#777, color:#FFF
        
        subgraph OpenAI-API
            style OpenAI-API fill:#555, color:#FFF
            o-api[API]:::openai
        end
    end
    
    subgraph machine[Linux machine]
        style machine fill:#777, color:#FFF
        
        subgraph linux[Linux]
            style linux fill:#555, color:#FFF
            ct((Crontab))
        end

        subgraph pw[Podcast Watchdog]
            style pw fill:#88A, color:#FFF

            pw00[main.py]:::python
            pw01[01: parse feeds RSS - utils_parse_rss.py ParseRSS]:::python
            pw02[02: download mp3 - utils_podcast.py Podcasts.download_podcasts]:::python
            pw03[03: transcribe - utils_podcast.py Podcasts.transcribe_podcasts]:::python
            pw04[04: summarize - utils_podcast.py Podcasts.summarize_podcasts]:::python
            pw05[05: Global DB]:::python

            subgraph SQLite
                style SQLite fill:#88A, color:#FFF
                pcdb[(podcast.db)]:::sqlite
            end
            
            subgraph in-f[input folder]
                style in-f fill:#88A, color:#FFF
                ai-json@{ shape: doc, label: "⚙️ ai_rss_feeds.json" }
                ai-json:::file
                prompt-json@{ shape: doc, label: "⚙️ ai_rss_prompts.json" }
                prompt-json:::file
            end

            subgraph out-f[output folder]
                style out-f fill:#88A, color:#FFF
                pcmp3@{ shape: docs, label: "🎧 XX_podcast.mp3" }
                pcmp3:::tfile
                pctxt@{ shape: docs, label: "📃 XX_podcast.txt" }
                pctxt:::file
            end
        end
        
        subgraph transcription-API
            style transcription-API fill:#555, color:#FFF
            t-api[main.py: transcribe]:::fastapi
        end
        
        subgraph mysql[Global DB]
            style mysql fill:#363, color:#FFF
            mon-mysql[(🚧ai-subject-monitoring🚧)]:::mysql
        end
    end


    ct ==> pw00
    pcdb o-.-o|🌱| pw01
    pcdb o-.-o|🎯🚀| pw02
    pcdb o-.-o|🎯🚀| pw03
    pcdb o-.-o|🎯🚀| pw04
    pcdb o-.-o|🎯🚀| pw05
    pw00 ==> pw01
    pw01 -->|👁️‍🗨️| ai-json
    pw00 ==> pw02
    pw02 -->|🆕| pcmp3
    pw00 ==> pw03
    pw03 <--> t-api
    t-api -->|👁️‍🗨️| pcmp3
    pw03 -->|🆕| pctxt
    pw03 -->|🗑️| pcmp3
    pw00 ==> pw04
    pw04 <--> o-api
    pw04 -->|👁️‍🗨️| prompt-json
    pw00 ==> pw05
    pw05 -...->|🌱| mon-mysql


    classDef python fill:#FFDC52, color:#000;
    classDef fastapi fill:#059286, color:#45D2C6
    classDef openai fill:#FFF, color:#000;
    classDef mysql fill:#00618B, color:#40A1CB
    classDef sqlite fill:#4FC0FC, color:#0F80CC
    classDef file fill:#BBB, color:#333
    classDef tfile fill:#888, color:#333
```

### I/O API: transcription-API

```mermaid
sequenceDiagram
    participant podcast-watchdog
    participant transcription-API
    podcast-watchdog->>transcription-API: API Request [POST]: file_path: str
    transcription-API-->>podcast-watchdog: JSON: {"file_name", "date_time", "processing_time", "transcription_text": text, "error"}
```

### I/O API: OpenAI API

```mermaid
sequenceDiagram
    participant podcast-watchdog
    participant OpenAI
    podcast-watchdog->>OpenAI: Request API: role / prompt [= pre-prompt + transcribe]
    OpenAI-->>podcast-watchdog: message
```

## Transcribe API

### Flowchart

```mermaid
graph TB
    goto-project
    click goto-project "https://github.com/ChristianPRO1982/transcription-API"
    style goto-project fill:#000, color:#00F

    subgraph app
        style app fill:#555, color:#FFF
        A((call))
    end

    subgraph machine[Linux machine]
        style machine fill:#777, color:#FFF

        subgraph ta[Transcribe API]
            style ta fill:#88A, color:#FFF

            A ==>|file_path: str| EP-TRANSCRIBE["ENDPOINT Transcribe [POST]"]:::python
            EP-TRANSCRIBE -.->|"json:file_name / file_name / date_time / processing_time / transcription_text / error"| A

            EP-TRANSCRIBE -->|"file_path: str"| UTILS["utils.py transcription_text()"]:::python
            UTILS -->|"(text, error)"| EP-TRANSCRIBE

            UTILS <--> WHISPER("model = whisper.load_model('base')")
        end
    end


    classDef python fill:#FFDC52, color:#000;
    classDef fastapi fill:#059286, color:#45D2C6
    classDef openai fill:#FFF, color:#000;
    classDef mysql fill:#00618B, color:#40A1CB
    classDef sqlite fill:#4FC0FC, color:#0F80CC
    classDef file fill:#BBB, color:#333
    classDef tfile fill:#888, color:#333
```

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
```

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
```

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
```

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
```

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
```

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
```

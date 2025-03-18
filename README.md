# AI SUBJECT MONITORING PROJECT
AI Subject Monitoring Project with mermaid

[![Latest Release](https://img.shields.io/github/release/ChristianPRO1982/ai-subject-monitoring-project.svg)](https://github.com/ChristianPRO1982/ai-subject-monitoring-project/releases/latest)
[![Python](https://img.shields.io/badge/python-3.10%2B-blue.svg)](https://www.python.org/)
[![License](https://img.shields.io/github/license/ChristianPRO1982/ai-subject-monitoring-project.svg)](https://github.com/ChristianPRO1982/ai-subject-monitoring-project/blob/main/LICENSE)

<details>
  <summary><strong>📌 Table of Contents</strong></summary>

  * [Legend](#legend)
  * [Global workflow - Flowchart](#flowchart)

| Developement            | Link 1                                  | Link 2                                                  | Link 3                                    |
|-------------------------|-----------------------------------------|---------------------------------------------------------|-------------------------------------------|
| **Linux machine**       | [Linux machine](#linux-machine)         | [Linux crontab](#linux-crontab)                         | [Shell scripts](#shell-scripts)           |
| **Podcast Watchdog**    | [Flowchart](#PW-flowchart)              |                                                         |                                           |
| **News sites**          | [Flowchart](#NS-flowchart)              |                                                         |                                           |
| **Manage newsletters**  | [Flowchart](#MN-flowchart)              |                                                         |                                           |
| **ChrisAI-research**    | [Flowchart](#CAIR-flowchart)            |                                                         |                                           |
| **Monitoring AI tools** | [Flowchart](#MAIT-flowchart)            |                                                         |                                           |
| **Newsletter**          | [Flowchart](#N-flowchart)               |                                                         |                                           |
| **Global DB**           | [Flowchart](#GDB-flowchart)             |                                                         |                                           |
| **APIs**                | [Transcribe Flowchart](#Tapi-flowchart) | [I/O API: transcription-API](#io-api-transcription-api) | [I/O API: OpenAI API](#io-api-openai-api) |

</details>

# Global workflow

## Legend

```mermaid
graph LR
    subgraph Legend [Legend]
        style Legend fill:#777, color:#000

        subgraph machine
            style machine fill:#777, color:#FFF
            subgraph package[Developed package]
                style package fill:#88A, color:#FFF
                example1[example]
            end
    
            subgraph not-package[Not developed package]
                style not-package fill:#555, color:#FFF
                example2[example]
            end

            subgraph dev[🚧 under construction 🚧]
                style dev fill:#363, color:#FFF
                example3[/🚧 example 🚧\]
            end
        end

        subgraph code
            style code fill:#777, color:#000
            
            L1[python scripts]:::python
            L2[Linux shell]:::shell
            L3[/FastAPI/]:::fastapi
            L4[/OpenAI/]:::openai
            L5[Other]
        end

        subgraph DBMS
            style DBMS fill:#777, color:#000

            L6[(MySQL)]:::mysql
            L7[(SQLite)]:::sqlite
        end

        subgraph files
            style files fill:#777, color:#000

            Lf1@{ shape: doc, label: "📄 File" }
            Lf1:::file
            Lf2@{ shape: docs, label: "📄 files" }
            Lf2:::file
            Lf3@{ shape: docs, label: "📄 temporary files" }
            Lf3:::tfile
        end

        subgraph actions[Actions emoji]
            style actions fill:#777, color:#000

            Lf4@{ shape: doc, label: "📄 File" }
            Lf5@{ shape: doc, label: "📄 File" }
            Lf6@{ shape: doc, label: "📄 File" }
            Lf7@{ shape: doc, label: "📄 File" }

            a1(read file) -->|👁️‍🗨️| Lf4:::file
            a3(create file) -->|✚| Lf5:::file
            a5(update file) -->|🔄| Lf6:::file
            a7(delete file) -->|🗑️| Lf7:::file
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

## Flowchart

```mermaid
graph LR
    subgraph APIs1[external APIs]
        style APIs1 fill:#777, color:#FFF
        
        subgraph OpenAI
            style OpenAI fill:#555, color:#FFF
            subg-APIs-B[/API/]:::openai
        end
    end

    subgraph machine[Linux machine]
        style machine fill:#777, color:#FFF

        subgraph crontab[Linux Crontab]
            style crontab fill:#363, color:#FFF
            A(⏱️ Crontab: weekly)
        end

        subgraph scripts[Shell scripts]
            style scripts fill:#363, color:#FFF
            
            A --> B[Podcast Watchdog]:::shell
            A --> C[Scrape-latest-posts-from-news-sites]:::shell
            A --> D[manage-newsletters]:::shell
            A --> E[ChrisAI-research]:::shell
            A ==> F[newsletter]:::shell
        end


        subgraph subg-b[Podcast Watchdog]
            style subg-b fill:#88A, color:#FFF

            B -->|main.py| subg-b-A[python POO]:::python
            subg-b-A -.->|🎯🌱🚀| dbpodcast[(podcast.db)]:::sqlite
            subg-b-A -->|✚| transcribe@{ shape: docs, label: "📄 XX_podcast.txt" }
            transcribe:::file

            subg-b-A <-->|role + prompt > txt| subg-APIs-B
        end

        subgraph subg-c[Scraping news sites]
            style subg-c fill:#363, color:#FFF
            C -->|main.py| subg-c-A[/🚧 under construction 🚧\]:::python
        end

        subgraph subg-d[Manage newsletters]
            style subg-d fill:#88A, color:#FFF

            D -->|main.py| subg-d-A[python POO]:::python
        end

        subgraph subg-e[ChrisAI-research]
            style subg-e fill:#363, color:#FFF
            E -->|main.py| subg-e-A[/🚧 under construction 🚧\]:::python
        end

        subgraph transcription-API
            style transcription-API fill:#88A, color:#FFF
            subg-b-A <-->|EndPoint:transcribe| subg-APIs-A[/main.py: transcribe/]:::fastapi
        end

        subgraph subg-g[Monitoring AI tools]
            style subg-g fill:#88A, color:#FFF

            G(🫳⌨️ manual launch) --> subg-g-A[python POO]:::python
            subg-g-A -.->|🌱| subg-g-B[(ai_tools.db)]:::sqlite
        end

        subgraph subg-mysql[Global DB]
            style subg-mysql fill:#363, color:#FFF
            info1[/🚧 under construction 🚧\]
            subg-b-A -.->|🌱| subg-mysql-A[(ai-subject-monitoring)]:::mysql
            subg-c-A -.->|🌱| subg-mysql-A
            subg-e-A -.->|🌱| subg-mysql-A
            subg-d-A -.->|🌱| subg-mysql-A
            subg-g-A -.->|🌱| subg-mysql-A
        end

        subgraph subg-f[Newsletter]
            style subg-f fill:#363, color:#FFF
            
            F ==>|main.py| subg-f-A[/🚧 under construction 🚧\]:::python
            subg-f-A -.->|🎯🚀| subg-mysql-A
        end
    end

    subgraph APIs2[external APIs]
        style APIs2 fill:#777, color:#FFF

        subgraph Outlook
            style Outlook fill:#555, color:#FFF

            subg-d-A --> |📬🔀📨🧨| subg-APIs-C[/📧 API/]
            subg-f-A ==>|📨| subg-APIs-C
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

[Table of content](#ai-subject-monitoring-project)

# Developments

## Linux machine

### Linux crontab

[...]

[Table of content](#ai-subject-monitoring-project)

### Shell scripts

[...]

[Table of content](#ai-subject-monitoring-project)

## Podcast Watchdog

### PW-Flowchart

```mermaid
graph LR
    goto-project
    click goto-project "https://github.com/ChristianPRO1982/podcast-watchdog"
    style goto-project fill:#000, color:#00F

    subgraph APIs[external APIs]
        style APIs fill:#777, color:#FFF
        
        subgraph OpenAI
            style OpenAI fill:#555, color:#FFF
            o-api[/API/]:::openai
        end
    end
    
    subgraph machine[Linux machine]
        style machine fill:#777, color:#FFF
        
        subgraph linux[Linux]
            style linux fill:#555, color:#FFF
            ct(⏱️ Crontab)
        end

        subgraph pw[Podcast Watchdog]
            style pw fill:#88A, color:#FFF

            pw00[main.py]:::python
            pw01[[01: parse feeds RSS - utils_parse_rss.py ParseRSS]]:::python
            pw02[[02: download mp3 - utils_podcast.py Podcasts.download_podcasts]]:::python
            pw03[[03: transcribe - utils_podcast.py Podcasts.transcribe_podcasts]]:::python
            pw04[[04: summarize - utils_podcast.py Podcasts.summarize_podcasts]]:::python
            pw05[[05: Global DB]]:::python

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
                pctxt@{ shape: docs, label: "📄 XX_podcast.txt" }
                pctxt:::file
            end
        end
        
        subgraph transcription-API
            style transcription-API fill:#555, color:#FFF
            t-api[/main.py: transcribe/]:::fastapi
        end
        
        subgraph mysql[Global DB]
            style mysql fill:#363, color:#FFF
            mon-mysql[(🚧ai-subject-monitoring🚧)]:::mysql
        end
    end


    ct ==> pw00
    pw00 ==> pw01
    pw01 -.->|🌱| pcdb
    pw01 -->|👁️‍🗨️| ai-json
    pw00 ==> pw02
    pw01 ~~~ pw02
    pw02 -.->|🎯🚀| pcdb
    pw02 -->|✚| pcmp3
    pw00 ==> pw03
    pw02 ~~~ pw03
    pw03 <--> t-api
    t-api -->|👁️‍🗨️| pcmp3
    pw03 -->|🗑️| pcmp3
    pw03 -->|✚| pctxt
    pw03 -.->|🎯🚀| pcdb
    pw00 ==> pw04
    pw03 ~~~ pw04
    pw04 -->|👁️‍🗨️| pctxt
    pw04 -->|👁️‍🗨️| prompt-json
    pw04 -.->|🎯🚀| pcdb
    pw00 ==> pw05
    pw04 ~~~ pw05
    pw04 <--> o-api
    pw05 -.->|🎯🚀| pcdb
    pw05 -...->|🌱| mon-mysql


    classDef python fill:#FFDC52, color:#000;
    classDef fastapi fill:#059286, color:#45D2C6
    classDef openai fill:#FFF, color:#000;
    classDef mysql fill:#00618B, color:#40A1CB
    classDef sqlite fill:#4FC0FC, color:#0F80CC
    classDef file fill:#BBB, color:#333
    classDef tfile fill:#888, color:#333
```

[Table of content](#ai-subject-monitoring-project)

## Scraping news sites

### NS-Flowchart

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

[Table of content](#ai-subject-monitoring-project)

## Manage newsletters

### MN-Flowchart

```mermaid
graph LR
    goto-project
    click goto-project "https://github.com/ChristianPRO1982/manage-newsletters"
    style goto-project fill:#000, color:#00F

    subgraph APIs[external APIs]
        style APIs fill:#777, color:#FFF
        
        subgraph Outlook
            style Outlook fill:#555, color:#FFF
            out-api[/📧 API/]
        end
    end

    subgraph machine[Linux machine]
        style machine fill:#777, color:#FFF
        
        subgraph linux[Linux]
            style linux fill:#555, color:#FFF
            ct(⏱️ Crontab)
        end

        subgraph mn[Manage newsletters]
            style mn fill:#88A, color:#FFF

            subgraph out-f[output folder]
                style out-f fill:#88A, color:#FFF
                
                NLtxt@{ shape: doc, label: "📄 NL_YYYY-MM-DD.txt" }
                NLtxt:::file
            end

            mn00[main.py]:::python

            mn01[[01: search new NL - utils_email.py OutlookEmails.new]]:::python
            mn02[[02: concact newsletters - utils_email.py AllEmails.concact]]:::python
            mn03[[03: send newsletter - utils_email.py AllEmails.send]]:::python
            mn04[[04: move newsletters - utils_email.py OutlookEmails.move]]:::python
            mn05[[05: delete old newsletters - utils_email.py OutlookEmails.delete]]:::python
        end
        
        subgraph mysql[Global DB]
            style mysql fill:#363, color:#FFF
            mon-mysql[(🚧ai-subject-monitoring🚧)]:::mysql
        end
    end


    ct ==> mn00
    mn00 ==> mn01
    mn01 <-->|📬| out-api
    mn00 ==> mn02
    mn01 ~~~ mn02
    mn02 -.->|🌱| mon-mysql
    mn02 --> NLtxt
    mn00 ==> mn03
    mn02 ~~~ mn03
    mn03 -->|📨| out-api
    mn00 ==> mn04
    mn03 ~~~ mn04
    mn04 -->|🔀| out-api
    mn00 ==> mn05
    mn04 ~~~ mn05
    mn05 -->|🧨| out-api


    classDef python fill:#FFDC52, color:#000;
    classDef fastapi fill:#059286, color:#45D2C6
    classDef openai fill:#FFF, color:#000;
    classDef mysql fill:#00618B, color:#40A1CB
    classDef sqlite fill:#4FC0FC, color:#0F80CC
    classDef file fill:#BBB, color:#333
    classDef tfile fill:#888, color:#333
```

[Table of content](#ai-subject-monitoring-project)

## ChrisAI-research

### CAIR-Flowchart

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

[Table of content](#ai-subject-monitoring-project)

## Monitoring AI tools

### MAIT-Flowchart

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

[Table of content](#ai-subject-monitoring-project)

## Newsletter

### N-Flowchart

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

[Table of content](#ai-subject-monitoring-project)

## Global DB

### GDB-Flowchart

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

[Table of content](#ai-subject-monitoring-project)

# APIs

## Transcribe API

### Tapi-Flowchart

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

            A ==>|file_path: str| EP-TRANSCRIBE[/"ENDPOINT Transcribe [POST]"/]:::python
            EP-TRANSCRIBE -.->|"json: file_name / file_name / date_time / processing_time / transcription_text / error"| A

            EP-TRANSCRIBE -->|"file_path: str"| UTILS["utils.py transcription_text()"]:::python
            UTILS -->|"(text, error)"| EP-TRANSCRIBE

            UTILS <--> WHISPER[["model = whisper.load_model('base')"]]
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

[Table of content](#ai-subject-monitoring-project)

### I/O API: transcription-API

```mermaid
sequenceDiagram
    participant Calling APP
    participant transcription-API
    Calling APP->>transcription-API: API Request [POST]: file_path: str
    transcription-API-->>Calling APP: JSON: {"file_name", "date_time", "processing_time", "transcription_text": text, "error"}
```

[Table of content](#ai-subject-monitoring-project)

## OpenAI API

### I/O API: OpenAI API

```mermaid
sequenceDiagram
    participant Calling APP
    participant OpenAI
    Calling APP->>OpenAI: Request API: role / prompt [= pre-prompt + transcribe]
    OpenAI-->>Calling APP: message
```

[Table of content](#ai-subject-monitoring-project)

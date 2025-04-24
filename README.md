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

            a1(read file) -->|👁️| Lf4:::file
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
            subg-b-A -->|✚| transcribe@{ shape: docs, label: "📄 XX_podcast.txt" }
            transcribe:::file
        end

        subgraph subg-c[Scraping news sites]
            style subg-c fill:#363, color:#FFF
            C -->|main.py| subg-c-A[/🚧 under construction 🚧\]:::python
        end

        subgraph subg-d[Manage newsletters]
            style subg-d fill:#88A, color:#FFF
            
            nl-txt@{ shape: docs, label: "📄 NL_YYYY-MM-DD.txt" }

            D -->|main.py| subg-d-A[python POO]:::python
            subg-d-A -->|✚| nl-txt:::file
        end

        subgraph subg-e[ChrisAI-research]
            style subg-e fill:#363, color:#FFF
            E -->|main.py| subg-e-A[/🚧 under construction 🚧\]:::python
        end

        subgraph subg-g[Monitoring AI tools]
            style subg-g fill:#88A, color:#FFF

            G(🫳⌨️ manual launch) --> subg-g-A[python POO]:::python
            subg-g-A -.->|🌱| subg-g-B[(ai_tools.db)]:::sqlite
        end

        subgraph subg-mysql[Global DB]
            style subg-mysql fill:#363, color:#FFF
            info1[/🚧 under construction 🚧\]
            subg-g-B ~~~ subg-mysql-A
            subg-b-A -.->|🌱| subg-mysql-A[(ai-subject-monitoring)]:::mysql
            subg-g-A -.->|🌱| subg-mysql-A
            subg-c-A -.->|🌱| subg-mysql-A
            subg-d-A -.->|🌱| subg-mysql-A
            subg-e-A -.->|🌱| subg-mysql-A
            nl-txt ~~~ subg-mysql-A
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
flowchart TB
    goto-project
    click goto-project "https://github.com/ChristianPRO1982/podcast-watchdog"
    style goto-project fill:#000, color:#0FF

    subgraph exDB[External DB]
        style exDB fill:#555, color:#FFF

        gDB[(Global DB)]:::mysql
    end

    subgraph machine[Linux machine]
        style machine fill:#777, color:#FFF

        subgraph inDB[internal DB]
            style inDB fill:#88A, color:#FFF

            sqlite[(podcast.db)]:::sqlite
        end

        subgraph inputoutput["Input / Output files"]
            style inputoutput fill:#777, color:#FFF

            ai-json@{ shape: doc, label: "⚙️ ai_rss_feeds.json" }
            ai-json:::file
            prompt-json@{ shape: doc, label: "⚙️ ai_rss_prompts.json" }
            prompt-json:::file

            p-mp3@{ shape: docs, label: "🎧 XX_podcast.mp3" }
            p-mp3:::tfile
            p-txt@{ shape: docs, label: "📄 XX_podcast.txt" }
            p-txt:::file
        end
            
        subgraph transcription-API
            style transcription-API fill:#555, color:#FFF
            
            t-api[/main.py: transcribe/]:::fastapi
        end

        subgraph pw[Podcast Watchdog]
            style pw fill:#88A, color:#FFF
            
            pw00[main.py]:::python
            pw00 ==> pw01[[#01: parse feeds RSS - utils_parse_rss.py ParseRSS]]:::python
            pw01 ==> pw02[[#02: download mp3 - utils_podcast.py Podcasts.download_podcasts]]:::python
            pw02 ==> pw03[[#03: transcribe - utils_podcast.py Podcasts.transcribe_podcasts]]:::python
            pw03 ==> pw04[[#04: summarize - utils_podcast.py Podcasts.summarize_podcasts]]:::python
            pw04 ==> pw05[[#05: Global DB]]:::python
        end


        go((START)) --> ct(⏱️ Crontab)
        ct ==> pw00
        pw01 -->|👁️| ai-json
        pw04 -->|👁️| prompt-json
        pw03 -->|✚| p-txt
        pw03 -->|🗑️| p-mp3
        pw02 -->|✚| p-mp3
        pw04 --> p-txt
        sqlite ~~~ gDB

        pw01 -.->|🌱| sqlite
        pw02 -.->|🎯🚀| sqlite
        pw03 -.->|🎯🚀| sqlite
        pw04 -.->|🎯🚀| sqlite
        pw05 -.->|🎯🚀| sqlite

        pw05 -.->|🌱| gDB

        pw03 <==> t-api
        t-api ~~~ pw03
        t-api -->|👁️| p-mp3

        pw05 ==> stop([END])

    end

    subgraph openAI[OpenAI]
        style openAI fill:#555, color:#FFF
        style openAI fill:#555, color:#FFF

        prompt-json ~~~ o-api[/API/]:::openai
        pw04 <==> o-api
    end

    ai-json ~~~ prompt-json
    prompt-json ~~~ p-mp3
    p-mp3 ~~~ p-txt


    classDef python fill:#FFDC52, color:#000;
    classDef fastapi fill:#059286, color:#45D2C6
    classDef openai fill:#FFF, color:#000;
    classDef mysql fill:#00618B, color:#40A1CB
    classDef sqlite fill:#4FC0FC, color:#0F80CC
    classDef file fill:#BBB, color:#333
    classDef tfile fill:#888, color:#333
```

[Table of content](#ai-subject-monitoring-project)

## Scraping latest posts from news sites

### NS-Flowchart

```mermaid
graph TB
    goto-project
    click goto-project "https://github.com/ChristianPRO1982/scraping-latest-posts-from-news-sites"
    style goto-project fill:#000, color:#0FF

    subgraph exDB[External DB]
        style exDB fill:#555, color:#FFF

        gDB[(Global DB)]:::mysql
    end

    subgraph output[Output files]
        style output fill:#88A, color:#FFF

        scrap-json@{ shape: docs, label: "{} scraped_sites.mp3" }
        scrap-json:::tfile
        article-txt@{ shape: docs, label: "📜 articles.md" }
        article-txt:::file

        scrap-json ~~~ article-txt
    end

    subgraph machine[Linux machine]
        style machine fill:#88A, color:#FFF
        
        ns00[main.py]:::python
        ns00 ==> ns01[[#01: scraping]]:::python
        ns01 ==> ns02[[#02: transform HTML to markdown and clean data]]:::python
        ns02 ==> ns03[[#03: save in txt file]]:::python
        ns03 ==> ns04[[#04: Global DB]]:::python
    end

    ct(⏱️ Crontab) ==> ns00
    ns01 -->|🔄| scrap-json
    ns02 -->|👁️| scrap-json
    ns03 -->|✚| article-txt

    ns04 -.->|🌱| gDB

    ns04 ==> stop([END])


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
graph TB
    goto-project
    click goto-project "https://github.com/ChristianPRO1982/manage-newsletters"
    style goto-project fill:#000, color:#0FF

    subgraph Outlook
        style Outlook fill:#555, color:#FFF
        out-api[/📧 API/]
    end

    subgraph exDB[External DB]
        style exDB fill:#555, color:#FFF

        gDB[(Global DB)]:::mysql
    end

    subgraph machine[Linux machine]
        style machine fill:#88A, color:#FFF
        
        mn00[main.py]:::python
        mn00 ==> mn01[[#01: search new NL - utils_email.py OutlookEmails.new]]:::python
        mn01 ==> mn02[[#02: concact newsletters - utils_email.py AllEmails.concact]]:::python
        mn02 ==> mn03[[#03: send newsletter - utils_email.py AllEmails.send]]:::python
        mn03 ==> mn04[[#04: move newsletters - utils_email.py OutlookEmails.move]]:::python
        mn04 ==> mn05[[#05: delete old newsletters - utils_email.py OutlookEmails.delete]]:::python
    end

    subgraph output[Output files]
        style output fill:#88A, color:#FFF

        nl-txt@{ shape: docs, label: "📄 NL_YYYY-MM-DD.txt" }
        nl-txt:::file
    end

    ct(⏱️ Crontab) ==> mn00
    mn01 -->|📬| out-api
    mn02 -->|✚| nl-txt
    mn02 -.->|🌱| gDB
    mn03 -->|📨| out-api
    mn04 -->|🔀| out-api
    mn05 -->|🧨| out-api

    mn05 ==> stop([END])


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
    style goto-project fill:#000, color:#0FF

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
    style goto-project fill:#000, color:#0FF

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
    style goto-project fill:#000, color:#0FF

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
    click goto-project "https://github.com/ChristianPRO1982/global-db"
    style goto-project fill:#000, color:#0FF

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
    style goto-project fill:#000, color:#0FF

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



```mermaid
graph RL

    subgraph autre
    A[👁️✚🔄🗑️]
    B[🎯🌱🚀⚰️]
        style autre fill:#777, color:#FFF
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


    classDef python fill:#FFDC52, color:#000;
    classDef fastapi fill:#059286, color:#45D2C6
    classDef openai fill:#FFF, color:#000;
    classDef mysql fill:#00618B, color:#40A1CB
    classDef sqlite fill:#4FC0FC, color:#0F80CC
    classDef file fill:#BBB, color:#333
    classDef tfile fill:#888, color:#333
```

```mermaid
graph TB
    subgraph PotC
        style PotC fill:#842, color:#F84
        
        start((début du jeu))
        QO1([.....])
        QOend([fin de la grande quête principale officielle])

        subgraph QG3[QG3 : RPG PotC]
            style QG3 fill:#88A, color:#FFF
            

        end

        subgraph QG2[QG2 : Traites et trahisons]
            style QG2 fill:#88A, color:#FFF
            

        end

        subgraph QG1[QG1 : Le Cachet de São Vicente ~ Saint George]
            style QG1 fill:#88A, color:#FFF
            

        end

        subgraph QM3[QM3 : Le trésor inca]
            style QM3 fill:#88A, color:#FFF
            
            
        end

        subgraph QM2[QM2 : A la poursuite de Carmen Sandiego]
            style QM2 fill:#88A, color:#FFF
            
            
        end

        subgraph QM1[QM1 : Le titre de ''Pirates des Caraïbes'']
            style QM1 fill:#88A, color:#FFF
            
            
        end

        subgraph QP3[QP3 : assassins]
            style QP3 fill:#88A, color:#FFF
            
            QP3-e1[lancement] --> QP3-e2[recherche d'informations]
            QP3-e2 --o QP3-e3@{ shape: docs, label: "informations sur les autres quêtes" }
            QP3-e2 --o QP3-e4@{ shape: docs, label: "informations sur la cible" }
            QP3-e1 --> QP3-e5[cible trouvée]
            QP3-e5 --> QP3-e6{Tuer la cible ?}
            QP3-e4 -.-> QP3-e6
            QP3-e6 -->|dans tous les cas| QP3-e7[retour au commanditaire]
            QP3-e7 -->|cible tuée| QP3-e8{{la cible a été assassinée ?}}
            QP3-e8 -->|oui| QP3-e9{{la cible est innocente ?}}
            QP3-e9 -->|oui| QP3-e10[[récompense + mauvaise réputation]]
            QP3-e9 -->|non| QP3-e11[[récompense + bonne réputation]]
            QP3-e8 -->|non| QP3-e12{{la cible est innocente ?}}
            QP3-e12 -->|oui| QP3-e13[[combat]]
            QP3-e13 -.->|oui| QP3-e14[[récompense + bonne réputation]]
            QP3-e12 -->|non| QP3-e15[[pas de récompense + ~mauvaise réputation]]
            QP3-e10 --> QP3-e16([FIN])
            QP3-e11 --> QP3-e16([FIN])
            QP3-e14 --> QP3-e16([FIN])
            QP3-e15 --> QP3-e16([FIN])
            QP3-e16 -.-> QP3-e1
        end

        subgraph QP2[QP2 : les amoureux]
            style QP2 fill:#88A, color:#FFF
            
            QP2-e1[lancement] --> QP2-e2[recherche de la bague]
            QP2-e2 --> QP2-e5[la bague est remise]
            QP2-e5 --> QP2-e6>quête terminée]
            QP2-e6 -.-> QP2-e7{{Toutes les quêtes sont faites ?}}
            QP2-e7 -.->|non| QP2-e1
            QP2-e7 ==>|oui| QP2-e8[[apparition de la guilde]]
            QP2-e8 ==> QP2-e9([FIN de toutes les quêtes])
            QP2-e2 -.-> QP2-e3(((timeout)))
            QP2-e3 --> QP2-e4[fin de la quête]
            QP2-e4 -.-> QP2-e1
        end

        subgraph QP1[QP1 : cartes aux trésor]
            style QP1 fill:#88A, color:#FFF

            QP1-e1[lancement] --> QP1-e2[recherche du trésor]
            QP1-e2 --> QP1-e3[recherche du trésor]
            QP1-e3 --> QP1-e4{partage du trésor ?}
            QP1-e4 -->|non| QP1-e5[[combat]]
            QP1-e5 --> QP1-e6([FIN de toutes les quêtes])
            QP1-e4 -->|oui| QP1-e7>partage du trésor]
            QP1-e7 -.-> QP1-e8{{Toutes les quêtes sont faites ?}}
            QP1-e8 -.->|non| QP1-e1
            QP1-e8 ==>|oui| QP1-e9[[lancement de la dernière quête]]
            QP1-e9 ==> QP1-e10([FIN de toutes les quêtes])
        end
    end

    start o--o QO1
    QO1 o--o QOend
    start ==> QP1
    start ==> QP2
    QOend ==> QP3
    QOend ==> QM1
    QOend ==> QM2
    QOend ==> QM3
    QM3 --> QG1
    QG1 --> QG2
    QG2 --> QG3

    classDef python fill:#FFDC52, color:#000;
```
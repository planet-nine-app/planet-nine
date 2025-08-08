# Planet Nine Ecosystem Architecture

## Complete Ecosystem Overview

```mermaid
graph TB
    subgraph "Client Layer - the-nullary"
        subgraph "Social Apps"
            blogary[blogary<br/>Text Blogging]
            eventary[eventary<br/>Event Management]
            postary[postary<br/>General Posting]
            screenary[screenary<br/>Multi-Purpose Social]
            viewaris[viewaris<br/>Short Videos]
            wikiary[wikiary<br/>Wiki/Knowledge]
            rhapsold[rhapsold<br/>Minimalist Blog]
            lexary[lexary<br/>Text Feeds]
            photary[photary<br/>Photo Sharing]
        end
        
        subgraph "Commerce Apps"
            ninefy[ninefy<br/>Digital Marketplace]
        end
        
        subgraph "Communication Apps"
            stackchat[StackChat<br/>P2P Messaging]
        end
        
        subgraph "Aggregation Apps"
            mybase[MyBase<br/>Multi-Base Content]
        end
        
        subgraph "Web Portal"
            nexus[Nexus<br/>Ecosystem Portal]
        end
    end
    
    subgraph "Protocol Layer - The Stack"
        sessionless[sessionless<br/>Cryptographic Auth<br/>secp256k1 Keys]
        magic[MAGIC<br/>Payment Protocol<br/>MP/Nineum Currency]
        teleportation[teleportation<br/>Content Discovery]
        advancement[the-advancement<br/>Browser Extensions<br/>Privacy Protection]
    end
    
    subgraph "Backend Layer - allyabase"
        subgraph "Core Services"
            bdo[bdo<br/>Big Dumb Object<br/>Storage]
            continuebee[continuebee<br/>State Verification]
            pref[pref<br/>Key/Value Prefs]
        end
        
        subgraph "Content Services"
            sanora[sanora<br/>Product Hosting<br/>Marketplace]
            dolores[dolores<br/>Video Storage<br/>Tagging]
        end
        
        subgraph "Commerce Services"
            addie[addie<br/>Payment Processing<br/>Split Transactions]
            aretha[aretha<br/>Limited Products<br/>Tickets/Rentals]
            fount[fount<br/>MAGIC Integration<br/>Rewards]
        end
        
        subgraph "Communication Services"
            julia[julia<br/>P2P Messaging<br/>Associations]
            minnie[minnie<br/>Email Handling]
        end
        
        subgraph "Account Services"
            joan[joan<br/>Account Recovery]
        end
    end
    
    subgraph "Infrastructure"
        subgraph "Multi-Base Architecture"
            base1[Base 1<br/>Port 1000-1122]
            base2[Base 2<br/>Port 2000-2122]
            base3[Base 3<br/>Port 3000-3122]
        end
        
        docker[Docker<br/>Containerization]
        pm2[PM2<br/>Process Management]
        testing[Test Suite<br/>6-Phase Validation]
    end
    
    %% Client to Protocol connections
    blogary --> sessionless
    eventary --> sessionless
    postary --> sessionless
    screenary --> sessionless
    viewaris --> sessionless
    wikiary --> sessionless
    rhapsold --> sessionless
    ninefy --> sessionless
    lexary --> sessionless
    photary --> sessionless
    stackchat --> sessionless
    mybase --> sessionless
    nexus --> sessionless
    
    ninefy --> magic
    screenary --> magic
    
    %% Protocol to Backend connections
    sessionless --> continuebee
    sessionless --> joan
    
    magic --> addie
    magic --> fount
    
    teleportation --> bdo
    teleportation --> sanora
    
    %% App to Service connections
    blogary --> sanora
    rhapsold --> sanora
    rhapsold --> bdo
    
    ninefy --> sanora
    ninefy --> bdo
    ninefy --> addie
    ninefy --> aretha
    
    viewaris --> dolores
    viewaris --> bdo
    
    screenary --> bdo
    screenary --> sanora
    screenary --> dolores
    screenary --> pref
    
    stackchat --> julia
    stackchat --> bdo
    
    lexary --> bdo
    photary --> bdo
    mybase --> bdo
    
    nexus --> bdo
    nexus --> sanora
    nexus --> dolores
    
    %% Infrastructure connections
    base1 --> docker
    base2 --> docker
    base3 --> docker
    docker --> pm2
    docker --> testing
    
    %% Browser Extension
    advancement -.-> |"Protects"| blogary
    advancement -.-> |"Protects"| eventary
    advancement -.-> |"Protects"| postary
    advancement -.-> |"Protects"| screenary
    advancement -.-> |"Protects"| viewaris
    advancement -.-> |"Protects"| wikiary
    advancement -.-> |"Protects"| rhapsold
    advancement -.-> |"Protects"| ninefy
    advancement -.-> |"Protects"| nexus
    
    classDef client fill:#e1f5fe,stroke:#01579b,stroke-width:2px
    classDef protocol fill:#f3e5f5,stroke:#4a148c,stroke-width:2px
    classDef backend fill:#e8f5e9,stroke:#1b5e20,stroke-width:2px
    classDef infra fill:#fff3e0,stroke:#e65100,stroke-width:2px
    
    class blogary,eventary,postary,screenary,viewaris,wikiary,rhapsold,ninefy,lexary,photary,stackchat,mybase,nexus client
    class sessionless,magic,teleportation,advancement protocol
    class bdo,continuebee,pref,sanora,dolores,addie,aretha,fount,julia,minnie,joan backend
    class base1,base2,base3,docker,pm2,testing infra
```

## Shared Component Architecture

```mermaid
graph LR
    subgraph "Shared SVG Components"
        text[text.js<br/>Typography]
        forms[forms.js<br/>Input Forms]
        layout[layout.js<br/>Containers]
        buttons[buttons.js<br/>Interactive]
        media[media.js<br/>Images/Video]
        feed[feed.js<br/>Scrollable Feeds]
        hud[hud.js<br/>Overlay System]
        base_screen[base-screen.js<br/>Base Management]
    end
    
    subgraph "Utilities"
        svg_utils[svg-utils.js<br/>SVG Helpers]
        form_utils[form-utils.js<br/>Form Creation]
        post_creator[post-creator.js<br/>Post Generation]
        layered_ui[layered-ui.js<br/>Layer Manager]
        env_config[environment-config.js<br/>Env Switching]
    end
    
    subgraph "Theme System"
        default_theme[default.js]
        dark_theme[dark.js]
        light_theme[light.js]
    end
    
    text --> svg_utils
    forms --> form_utils
    feed --> layered_ui
    hud --> layered_ui
    base_screen --> feed
    
    post_creator --> forms
    post_creator --> text
    
    default_theme --> text
    dark_theme --> text
    light_theme --> text
    
    classDef component fill:#e3f2fd,stroke:#1565c0,stroke-width:2px
    classDef util fill:#fce4ec,stroke:#880e4f,stroke-width:2px
    classDef theme fill:#f9fbe7,stroke:#558b2f,stroke-width:2px
    
    class text,forms,layout,buttons,media,feed,hud,base_screen component
    class svg_utils,form_utils,post_creator,layered_ui,env_config util
    class default_theme,dark_theme,light_theme theme
```

## Data Flow Architecture

```mermaid
sequenceDiagram
    participant User
    participant App as Nullary App
    participant Auth as sessionless
    participant Service as allyabase Service
    participant Storage as File System/BDO
    
    User->>App: Interact with UI
    App->>Auth: Generate signature
    Auth-->>App: Cryptographic proof
    App->>Service: API Request + Signature
    Service->>Auth: Verify signature
    Auth-->>Service: Valid/Invalid
    Service->>Storage: Read/Write data
    Storage-->>Service: Data response
    Service-->>App: JSON response
    App-->>User: Update UI (SVG)
    
    Note over App,Service: No sessions, cookies, or passwords
    Note over Storage: Self-hostable, privacy-focused
```

## Testing Infrastructure

```mermaid
graph LR
    subgraph "6-Phase Testing System"
        phase1[Phase 1<br/>Infrastructure<br/>3 Bases]
        phase2[Phase 2<br/>Services<br/>12+ APIs]
        phase3[Phase 3<br/>Applications<br/>All Nullary]
        phase4[Phase 4<br/>Cross-Base<br/>P2P Testing]
        phase5[Phase 5<br/>Nexus Portal<br/>Browser Tests]
        phase6[Phase 6<br/>Integration<br/>Reports]
    end
    
    phase1 --> phase2
    phase2 --> phase3
    phase3 --> phase4
    phase4 --> phase5
    phase5 --> phase6
    
    classDef test fill:#fff9c4,stroke:#f57f17,stroke-width:2px
    class phase1,phase2,phase3,phase4,phase5,phase6 test
```

This diagram shows the complete Planet Nine ecosystem with all its layers, connections, and architectural patterns!
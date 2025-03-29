```mermaid
graph TB
    subgraph "Client Browser"
        UI[User Interface]
    end

    subgraph "Next.js Application"
        NEXT[Next.js App]
        ROUTER[Next.js Router]
        
        subgraph "Server Components"
            SSR[Server-Side Rendering]
            ACTIONS[Server Actions]
        end
        
        subgraph "Client Components"
            CSR[Client-Side React]
            RQ[React Query]
            CACHE[Query Cache]
        end
        
        subgraph "API Layer"
            HONO[Hono.js API Routes]
        end
    end
    
    subgraph "External Services"
        SB[Supabase]
        SANITY[Sanity.io]
        
        subgraph "Supabase Services"
            AUTH[Authentication]
            DB[PostgreSQL Database]
            STORAGE[File Storage]
        end
        
        subgraph "Sanity Services"
            CMS[Content Management]
            CDN[Content Delivery]
            ASSETS[Asset Management]
        end
    end
    
    %% Client-side flow
    UI <--> ROUTER
    UI <--> CSR
    CSR <--> RQ
    RQ <--> CACHE
    
    %% Server-side flow
    ROUTER <--> SSR
    ROUTER <--> ACTIONS
    
    %% API Connections
    RQ <--> HONO
    SSR <--> HONO
    ACTIONS <--> SB
    
    %% External connections
    HONO <--> SB
    HONO <--> SANITY
    SSR <--> SB
    SSR <--> SANITY
    
    %% Supabase internals
    SB <--> AUTH
    SB <--> DB
    SB <--> STORAGE
    
    %% Sanity internals
    SANITY <--> CMS
    SANITY <--> CDN
    SANITY <--> ASSETS
    
    %% Data flow annotations
    classDef highlight fill:#f9f,stroke:#333,stroke-width:2px;
    class HONO,SB,SANITY,RQ highlight;

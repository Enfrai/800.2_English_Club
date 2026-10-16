# Architecture

## 1. Client - Service - Permanent Storage

```mermaid
graph TD
    %% Styling and layout
    Client([Web Application / Mobile Application]) -->|HTTPS| LoadBalancer[Load Balancer]
    
    subgraph Cloud Infrastructure
        LoadBalancer --> CDN[CDN]

        LoadBalancer --> APIGateway[API Gateway]
        APIGateway --> ApplicationService[Application Services]
        
        ApplicationService --> Model[Model]


        ApplicationService --> AsyncProcessing[Async Processing]

        AsyncProcessing --> Model
    end

    subgraph Sotrage
        Model --> DB[(Primary Database)]
        Model --> Cache[(Redis Cache)]
    end

    classDef database fill:#f9f,stroke:#333,stroke-width:2px;
    class DB,Cache database;
```

## 2. Tech-Stack

### Frontend 

- React + Next.js (~55% - 60%)

### Backend 

- Python + FastAPI

### Database

- PostgreSQL

### API

- RESTful API

## 3. Backend 

### Services

- Application Services + Domain + Repository / DAO

### Database

- PostgreSQL
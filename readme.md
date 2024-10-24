```bash
src/
├── application/           # Casos de Uso, DTOs, Exceções, e Gateways
│   ├── dto/               # Data Transfer Objects (DTOs)
│   ├── exceptions/        # Exceções específicas da aplicação
│   ├── gateways/          # Interfaces para interações externas (e.g., APIs externas)
│   └── use-cases/         # Casos de Uso (Aplicação)
├── domain/                # Entidades, Regras de Negócio, Repositórios e Serviços
│   ├── entities/          # Entidades do domínio
│   ├── exceptions/        # Exceções de domínio (opcional)
│   ├── repositories/      # Interfaces dos repositórios (Interface Adapters)
│   └── services/          # Interfaces para serviços de domínio
├── infrastructure/        # Implementações de Infraestrutura
│   ├── config/            # Configurações (banco de dados, serviços, etc.)
│   ├── database/          # Conexões e mapeamentos do banco de dados
│   ├── orm/               # Mapeamento de Entidades (ORM)
│   ├── repositories/      # Implementações dos Repositórios
│   ├── services/          # Implementações de Serviços Externos (e.g., Hashing, APIs)
│   └── logging/           # Sistema de logging centralizado
├── interface/             # Interface (Controllers e APIs)
│   ├── controllers/       # Controladores para APIs
│   └── presenters/        # Transformadores de saída (opcional)
├── shared/                # Recursos compartilhados entre camadas
│   ├── utils/             # Utilitários, helpers
│   ├── constants/         # Constantes globais
│   ├── middleware/        # Middlewares globais
│   └── interceptors/      # Interceptores globais
└── test/                  # Testes (unitários, integração, etc.)
    ├── unit/              # Testes Unitários
    └── integration/       # Testes de Integração

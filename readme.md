# Estrutura do Projeto com Clean Architecture

Este projeto segue os princípios da Clean Architecture, separando as responsabilidades entre camadas distintas. Abaixo, você encontra uma explicação detalhada de cada camada e seus respectivos diretórios.

## Estrutura de Pastas

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
```

Camada de Domínio (domain/)
Essa camada contém a lógica central do negócio, isolada de detalhes de infraestrutura e interfaces.

Entidades (entities/): Define as entidades principais do domínio, como User, Order, etc.
Regras de Negócio (services/): Serviços que implementam regras de negócios mais complexas que podem ser usadas por múltiplos casos de uso.
Exceções (exceptions/): Exceções relacionadas às regras de negócio. Exemplo: InvalidUserEmailException.
Repositórios (repositories/): Interfaces que definem como acessar e persistir os dados. Exemplo: UserRepository.
Camada de Aplicação (application/)
Responsável por orquestrar o fluxo de dados entre o domínio e as interfaces, sem expor detalhes de infraestrutura.

DTOs (dto/): Objetos de Transferência de Dados usados para entrada/saída de dados entre camadas.
Exceções (exceptions/): Exceções específicas da aplicação, como falhas ao logar um usuário.
Gateways (gateways/): Interfaces para comunicação com serviços externos, como APIs de pagamento.
Use Cases (use-cases/): Casos de uso que orquestram as operações da aplicação, interagindo com o domínio.
Camada de Infraestrutura (infrastructure/)
Esta camada contém as implementações concretas de bancos de dados, serviços externos e ferramentas auxiliares.

Configurações (config/): Arquivos de configuração para banco de dados, autenticação, etc.
Banco de Dados (database/): Configurações específicas de conexão com bancos de dados.
ORM (orm/): Mapeamento de entidades e suas interações com o banco de dados (e.g., TypeORM, Prisma).
Repositórios (repositories/): Implementações concretas dos repositórios definidos no domínio.
Serviços (services/): Implementações de serviços de infraestrutura, como hashing, envio de e-mails, etc.
Logging (logging/): Sistema de logging centralizado, para separar a lógica de registro de eventos dos serviços principais.
Camada de Interface (interface/)
Esta camada lida com a interação do usuário ou de sistemas externos com a aplicação.

Controllers (controllers/): Exposição das rotas e endpoints de API, geralmente no formato REST.
Presenters (presenters/): Transformadores que formatam os dados de saída para diferentes interfaces (e.g., API REST, GraphQL).
Recursos Compartilhados (shared/)
Arquivos e funcionalidades que podem ser reutilizados por diferentes camadas do projeto.

Utilitários (utils/): Funções auxiliares e helpers que podem ser usados em várias partes do código.
Constantes (constants/): Variáveis constantes que são compartilhadas entre múltiplas camadas.
Middleware (middleware/): Middlewares globais que interceptam as requisições, como autenticação e autorização.
Interceptores (interceptors/): Interceptores para manipulação de requisições e respostas (e.g., tratamento de erros).
Testes (test/)
A estrutura de testes é organizada para garantir a cobertura completa da aplicação.

Testes Unitários (unit/): Testes focados em componentes específicos da aplicação (e.g., casos de uso, serviços).
Testes de Integração (integration/): Testes que validam a interação entre diferentes módulos e camadas.
Melhorias e Refinamentos
Camada de Exceções
Exceções de Domínio: Exceções que surgem quando as regras de negócio são violadas (e.g., InvalidOrderException).
Exceções de Aplicação: Geradas ao interagir com infraestrutura ou APIs externas (e.g., falha ao conectar ao banco de dados).
Gateways e Adapters
Gateways: Interfaces que abstraem a interação com serviços externos (e.g., APIs de pagamento).
Adapters: Implementações específicas dessas interações (e.g., StripePaymentAdapter).
Middleware e Interceptores
Middlewares: Úteis para centralizar a lógica de autenticação e autorização.
Interceptores: Manipulam requisições e respostas, ajudando no tratamento de erros e logging.
Testabilidade
Seguindo a Clean Architecture, cada parte do sistema é modular e mais fácil de testar, seja com testes unitários ou de integração.


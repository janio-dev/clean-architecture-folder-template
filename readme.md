# Estrutura do Projeto com Clean Architecture

Este projeto segue os princípios da **Clean Architecture**, separando as responsabilidades entre camadas distintas. Abaixo, você encontrará uma explicação detalhada de cada camada e seus respectivos diretórios.

## Índice

- [Estrutura de Pastas](#estrutura-de-pastas)
- [Camada de Domínio (domain/)](#camada-de-domínio-domain)
- [Camada de Aplicação (application/)](#camada-de-aplicação-application)
- [Camada de Infraestrutura (infrastructure/)](#camada-de-infraestrutura-infrastructure)
- [Camada de Interface (interface/)](#camada-de-interface-interface)
- [Recursos Compartilhados (shared/)](#recursos-compartilhados-shared)
- [Testes (test/)](#testes-test)
- [Melhorias e Refinamentos](#melhorias-e-refinamentos)

## Estrutura de Pastas

```bash
src/
├── application/           # Casos de Uso, DTOs, Exceções, e Gateways
├── domain/                # Entidades, Regras de Negócio, Repositórios e Serviços
├── infrastructure/        # Configurações, Repositórios, Serviços de Infraestrutura
├── interface/             # Controladores e Apresentadores para API
├── shared/                # Utilitários, Constantes, Middleware e Interceptores
└── test/                  # Testes unitários e de integração
```

## Camada de Domínio (domain/)

A camada de domínio contém a lógica central do negócio, totalmente desacoplada de detalhes de
infraestrutura ou interfaces. Seus principais componentes são:

- **Entidades (entities/):** Definem as principais entidades do domínio, como User, Order, etc.
- **Regras de Negócio (services/):** Contêm regras de negócio complexas, que podem ser reutilizadas
 em vários casos de uso.
- **Exceções (exceptions/):** Exceções específicas do domínio, como InvalidUserEmailException,
 que tratam violações de regras de negócio.
- **Repositórios (repositories/):** Interfaces que definem como os dados serão acessados
 e persistidos.

## Camada de Aplicação (application/)

A camada de aplicação é responsável por orquestrar o fluxo de dados entre
o domínio e as interfaces. Ela contém:

- **DTOs (dto/):** Objetos de Transferência de Dados usados para entrada e saída de dados entre camadas.
- **Exceções (exceptions/):** Exceções específicas de lógica de aplicação, como falhas ao logar um usuário.
- **Gateways (gateways/):** Interfaces para comunicação com serviços externos, como APIs de pagamento.
- **Use Cases (use-cases/):** Casos de uso que contêm a lógica de aplicação, organizando a interação entre domínio e infraestrutura.

## Camada de Infraestrutura (infrastructure/)

A camada de infraestrutura contém implementações concretas e detalhes técnicos da aplicação. Seus componentes incluem:

**Configurações (config/):** Arquivos de configuração para banco de dados, provedores de autenticação, etc.
**Banco de Dados (database/):** Configurações de conexão com o banco de dados.
**RM (orm/):** Mapeamento das entidades e suas interações com o banco de dados (e.g., usando TypeORM, Prisma).
**Repositórios (repositories/):** Implementações concretas das interfaces de repositórios definidas no domínio.
**Serviços (services/):** Implementações de serviços externos, como hashing de senhas, envio de e-mails, etc.
**Logging (logging/):** Sistema centralizado de logging, para registros e monitoramento.

## Camada de Interface (interface/)

A camada de interface lida com a interação do usuário ou de sistemas externos com a aplicação. Ela contém:

**Controllers (controllers/):** Controladores que expõem as rotas e endpoints da API.
**Presenters (presenters/):** Transformadores que formatam os dados de saída para diferentes interfaces, como APIs REST e GraphQL.

## Recursos Compartilhados (shared/)

Essa seção contém utilitários e outros componentes que são amplamente reutilizados em várias partes da aplicação:

**Utilitários (utils/):** Funções auxiliares usadas em várias partes do código.
**Constantes (constants/):** Valores constantes que são utilizados em múltiplas camadas.
**Middleware (middleware/):** Middlewares que interceptam as requisições para realizar tarefas como autenticação e autorização.
**Interceptores (interceptors/):** Manipulam requisições e respostas, oferecendo suporte para logging e tratamento de erros.

## Testes (test/)

A estrutura de testes é dividida em duas principais categorias:

**Testes Unitários (unit/):** Testes que verificam componentes individuais, como casos de uso e serviços.
**Testes de Integração (integration/):** Testes que validam a interação entre múltiplas camadas e componentes do sistema.

## Melhorias e Refinamentos

### Camada de Exceções
- **Exceções de Domínio:** Tratam violações das regras de negócio no domínio.
- **Exceções de Aplicação:** Lidam com erros gerados por interações com infraestrutura ou APIs externas.

### Gateways e Adapters
- **Gateways:** Interfaces que abstraem a comunicação com serviços externos.
- **Adapters:** Implementações concretas dessas interfaces, como um StripePaymentAdapter para interagir com a API de pagamentos do Stripe.

### Middleware e Interceptores
- **Middlewares:** Centralizam tarefas como autenticação e autorização.
- **Interceptores:** Manipulam requisições e respostas, lidando com erros e logging.

### Testabilidade
A modularização da aplicação baseada em camadas torna o sistema altamente testável, tanto com testes unitários quanto com testes de integração.
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

## Camada de Domínio (domain/)

A camada de domínio contém a lógica central do negócio, totalmente desacoplada de detalhes de infraestrutura ou interfaces. Seus principais componentes são:

- Entidades (entities/): Definem as principais entidades do domínio, como User, Order, etc.
- Regras de Negócio (services/): Contêm regras de negócio complexas, que podem ser reutilizadas em vários casos de uso.
- Exceções (exceptions/): Exceções específicas do domínio, como InvalidUserEmailException, que tratam violações de regras de negócio.
- Repositórios (repositories/): Interfaces que definem como os dados serão acessados e persistidos.
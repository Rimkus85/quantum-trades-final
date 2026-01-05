# Quantum Trades

**Plataforma de Trading Automatizado com Inteligência Artificial**

---

## Sobre o Projeto

A Quantum Trades é uma plataforma de trading automatizado que utiliza inteligência artificial para analisar o mercado, identificar oportunidades e executar operações 24/7. O sistema funciona como uma camada de inteligência entre o investidor e o mercado, oferecendo um agente de IA financeiro autônomo.

### Propósito

Democratizar o acesso a estratégias de investimento sofisticadas por meio da inteligência artificial, capacitando investidores de todos os níveis a operar com a mesma disciplina e análise de dados de grandes instituições financeiras.

---

## Documentação

| Documento | Descrição |
| :--- | :--- |
| [Plano de Desenvolvimento MVP](./PLANO_DESENVOLVIMENTO_MVP.md) | Plano completo com sprints e histórias de usuário |
| [Manual Mestre v3.0](./docs/Manual_Mestre_Quantum_Trades_v3.md) | Documento central de referência do projeto |
| [Requisitos Consolidados](./docs/requisitos_consolidados.md) | Requisitos funcionais e não-funcionais do MVP |
| [Sprints e Histórias](./docs/sprints_e_historias.md) | Detalhamento das histórias de usuário por sprint |
| [Mapa Mental Extraído](./docs/mapa_mental_extraido.md) | Informações extraídas do mapa mental do projeto |

---

## Stack Tecnológica

### Backend
- **Python 3.11+** - Linguagem principal
- **FastAPI** - Framework de API REST
- **Pydantic v2** - Validação de dados
- **PostgreSQL** - Banco de dados
- **Redis/Kafka** - Mensageria

### Frontend
- **React + TypeScript** - Aplicação Web
- **React Native + TypeScript** - Aplicação Mobile (iOS e Android)

### Integrações
- **Cedro OMS** - Conexão com corretoras via FIX ou API institucional
- **APIs de Mercado** - B3, S&P, Criptomoedas
- **Telegram** - Alertas e notificações

---

## Arquitetura

O projeto segue o padrão **Clean Architecture / Hexagonal Architecture**:

```
├── domain/          # Lógica de negócio central
├── application/     # Casos de uso
├── adapters/        # Conexão com serviços externos
├── infrastructure/  # Persistência, mensageria, logs
├── api/             # FastAPI endpoints
└── ui/              # Frontend (Web e Mobile)
```

---

## Sprints do MVP

| Sprint | Objetivo |
| :--- | :--- |
| **Sprint 1** | Fundação e Autenticação |
| **Sprint 2** | Onboarding e Gestão de Planos |
| **Sprint 3** | Dashboard e Visualização de Dados |
| **Sprint 4** | Motor de IA (v1) e Bots |
| **Sprint 5** | Integrações e Alertas |
| **Sprint 6** | Refinamento e Preparação para o Beta |

---

## Segurança e Compliance

- **2FA Obrigatório** - Google Authenticator
- **Audit Trail** - Logs imutáveis de todas as ações
- **Circuit Breakers** - Proteção automática contra perdas
- **Conformidade** - CVM, B3, LGPD

---

## Licença

Este projeto é proprietário da Quantum Trades. Todos os direitos reservados.

---

**Quantum Trades** - *Automatize suas estratégias com nossa IA*

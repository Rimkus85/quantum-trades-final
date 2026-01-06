# Quantum Trades

**Plataforma de Trading Automatizado com Inteligência Artificial**

![Quantum Trades Logo](./landing-page/assets/logo.png)

---

## Sobre o Projeto

A Quantum Trades é uma plataforma de trading automatizado que utiliza inteligência artificial para analisar o mercado, identificar oportunidades e executar operações 24/7. O sistema funciona como uma camada de inteligência entre o investidor e o mercado, oferecendo um agente de IA financeiro autônomo.

### Propósito

Democratizar o acesso a estratégias de investimento sofisticadas por meio da inteligência artificial, capacitando investidores de todos os níveis a operar com a mesma disciplina e análise de dados de grandes instituições financeiras.

---

## Status do Desenvolvimento

| Sprint | Objetivo | Status |
| :--- | :--- | :---: |
| **Sprint 0** | Landing Page e Marketing | ✅ Concluída |
| **Sprint 1** | Fundação e Autenticação | 🔜 Próxima |
| **Sprint 2** | Onboarding e Gestão de Planos | ⏳ Pendente |
| **Sprint 3** | Dashboard e Visualização de Dados | ⏳ Pendente |
| **Sprint 4** | Motor de IA (v1) e Bots | ⏳ Pendente |
| **Sprint 5** | Integrações e Alertas | ⏳ Pendente |
| **Sprint 6** | Refinamento e Preparação para o Beta | ⏳ Pendente |

---

## Sprint 0 - Landing Page e Marketing ✅

A Landing Page foi desenvolvida seguindo as diretrizes de design e UX definidas na documentação, com foco em conversão e captura de leads.

### Funcionalidades Implementadas

| História | Descrição | Status |
| :--- | :--- | :---: |
| QT-LP-01 | Hero Section com navegação responsiva | ✅ |
| QT-LP-02 | Seção "Como Funciona" com 4 etapas | ✅ |
| QT-LP-03 | Resultados e ganhos potenciais com disclaimers | ✅ |
| QT-LP-04 | Tabela comparativa dos 3 planos | ✅ |
| QT-LP-05 | Formulário de cadastro com CPF e corretoras | ✅ |
| QT-LP-06 | FAQ com perguntas frequentes | ✅ |
| QT-LP-07 | SEO, meta tags e responsividade | ✅ |

### Planos Disponíveis

| Plano | Preço | Destaques |
| :--- | :--- | :--- |
| **Entrada** | R$ 97/mês | 1 corretora, 5 ativos, estratégias básicas |
| **Profissional** | R$ 197/mês | 3 corretoras, 20 ativos, relatórios detalhados |
| **Enterprise** | R$ 497/mês | Ilimitado, API, gamificação com prêmios em dinheiro |

### Identidade Visual

A Landing Page segue rigorosamente a identidade visual definida:

- **Cor de Fundo**: #0A192F (Azul Noturno)
- **Cor de Destaque**: #FFD700 (Dourado Quantum)
- **Cor de Texto**: #FFFFFF (Branco)
- **Fonte**: Montserrat (pesos 400, 500, 600, 700, 800)
- **Design**: Moderno, futurista, com elementos neon

### Arquivos da Sprint 0

```
landing-page/
├── index.html              # Landing Page completa
├── assets/
│   └── logo.png            # Logo oficial
└── SPRINT0_CHECKLIST.md    # Checklist de verificação
```

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
- **TailwindCSS** - Estilização

### Integrações
- **Cedro OMS** - Conexão com corretoras via FIX ou API institucional
- **APIs de Mercado** - B3, S&P, Criptomoedas
- **Telegram** - Alertas e notificações
- **Google Authenticator** - 2FA obrigatório

---

## Arquitetura

O projeto segue o padrão **Clean Architecture / Hexagonal Architecture**:

```
├── domain/          # Lógica de negócio central
├── application/     # Casos de uso
├── adapters/        # Conexão com serviços externos
├── infrastructure/  # Persistência, mensageria, logs
├── api/             # FastAPI endpoints
├── landing-page/    # Landing Page (Sprint 0)
└── ui/              # Frontend (Web e Mobile)
```

---

## Segurança e Compliance

- **2FA Obrigatório** - Google Authenticator
- **Audit Trail** - Logs imutáveis de todas as ações
- **Circuit Breakers** - Proteção automática contra perdas
- **Stop Loss Inteligente** - Gestão de risco automatizada
- **Conformidade** - CVM, B3, LGPD

---

## Corretoras Compatíveis

- XP Investimentos
- Clear
- Inter
- Rico
- Genial
- Toro
- Nu Invest
- BTG Pactual

---

## Licença

Este projeto é proprietário da **RimkusSoftware ME**. Todos os direitos reservados.

---

**Quantum Trades** - *Automatize suas estratégias com nossa IA*

© 2026 Quantum Trades - RimkusSoftware ME

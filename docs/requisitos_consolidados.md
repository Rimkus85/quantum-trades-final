# Requisitos Consolidados - Quantum Trades MVP

**Versão:** 1.0  
**Data:** 05 de Janeiro de 2026  
**Fonte:** Manual Mestre v3.0 + Mapa Mental

---

## 1. Visão Geral do Produto

A Quantum Trades é uma plataforma de trading automatizado que utiliza inteligência artificial para analisar o mercado, identificar oportunidades e executar operações 24/7. O sistema funciona como uma camada de inteligência entre o investidor e o mercado, oferecendo um agente de IA financeiro autônomo.

### 1.1 Objetivos Estratégicos do MVP

| Fase | Objetivo | Entregáveis |
|------|----------|-------------|
| Fase 0 | Fundação e Planejamento | Stack tecnológica, validação regulatória, ICP definido |
| Fase 1 | Desenvolvimento do MVP | Plataforma funcional com onboarding, dashboard e motor de IA em modo DEMO |
| Fase 2 | Beta Fechado | Validação com usuários reais e execução em ambiente real |
| Fase 3 | Lançamento Público | Escala de operações e otimização de infraestrutura |

---

## 2. Stack Tecnológica Obrigatória

### 2.1 Backend / Core

| Tecnologia | Versão | Propósito |
|------------|--------|-----------|
| Python | 3.11+ | Linguagem principal do backend |
| FastAPI | Latest | Framework de API REST |
| Pydantic | v2 | Validação de dados e schemas |
| Pytest | Latest | Framework de testes |
| Asyncio | Built-in | Programação assíncrona |

### 2.2 Frontend

| Tecnologia | Propósito |
|------------|-----------|
| React + TypeScript | Aplicação Web |
| React Native + TypeScript | Aplicação Mobile (iOS e Android) |

### 2.3 Infraestrutura

| Componente | Tecnologia |
|------------|------------|
| Banco de Dados | PostgreSQL |
| Mensageria | Redis ou Kafka |
| OMS | Cedro OMS (via FIX ou API institucional) |

---

## 3. Arquitetura Obrigatória

A arquitetura segue o padrão **Clean Architecture / Hexagonal Architecture** com separação explícita entre camadas:

| Camada | Responsabilidade |
|--------|------------------|
| Domain | Ordens, contas, corretoras, risco |
| Application | Casos de uso |
| Adapters | OMS, FIX, corretoras |
| Infrastructure | DB, filas, logs |
| API | FastAPI |
| UI | Web / Mobile |

**Regra Crítica:** Nenhum código de integração externa pode vazar para a camada de domínio.

---

## 4. Funcionalidades do MVP

### 4.1 Módulo de Autenticação e Segurança

| Funcionalidade | Prioridade | Descrição |
|----------------|------------|-----------|
| Cadastro de usuário | P0 | Nome, CPF, e-mail, corretora(s) |
| Login seguro | P0 | Usuário + senha criptografada |
| 2FA obrigatório | P0 | Google Authenticator |
| Recuperação de senha | P0 | Via código por e-mail |
| Validação de dados | P0 | CPF no padrão xxx.xxx.xxx-xx |

### 4.2 Módulo de Onboarding

| Funcionalidade | Prioridade | Descrição |
|----------------|------------|-----------|
| Questionário de perfil | P0 | Perfil de risco, objetivos, tempo, aportes |
| Termos de aceite | P0 | Termos de Uso, Política de Privacidade, Política de Risco |
| Autorização de execução | P0 | Opt-in para execução automática |
| Cadastro Telegram | P1 | Para autorização remota |

### 4.3 Módulo de Planos e Pagamento

| Plano | Funcionalidades |
|-------|-----------------|
| **Entrada** | Carteira de investimentos, Cedro OMS, Dashboard, Alertas Telegram (3 ações), Gamificação |
| **Médio** | Entrada + Cripto futuros automatizado, Alertas diários cripto, Alertas (5 ações), Opções automatizadas |
| **Top** | Médio + Administração total da carteira, Customização de estratégia, Research com IA |

| Funcionalidade | Prioridade | Descrição |
|----------------|------------|-----------|
| Seleção de plano | P0 | 3 níveis de plano |
| Trial com timer | P1 | Período de teste com contador |
| Pagamento cartão | P0 | Integração com operadora |
| Validação de pagamento | P0 | Feedback de sucesso/erro |

### 4.4 Módulo Dashboard

| Componente | Prioridade | Descrição |
|------------|------------|-----------|
| Total da Carteira | P0 | Valor total administrado |
| Retorno Mensal | P0 | Média de retorno com seleção de período |
| Comparativos | P1 | S&P, CDI, Dólar, B3, BTC |
| Quantidade de Trades | P0 | Soma de operações realizadas |
| Portfólio por classe | P0 | Ações B3, Internacionais, Opções, Cripto |
| Taxa de Acerto | P0 | % de operações lucrativas |
| Operações Recentes | P0 | Top 10 operações |
| Gráfico de Performance | P1 | Evolução temporal |

### 4.5 Módulo de Inteligência Artificial

| Funcionalidade | Prioridade | Descrição |
|----------------|------------|-----------|
| Motor de Decisão v1 | P0 | 2-3 setups básicos |
| Sistema de predileção | P1 | Recomendação quando score > 70 |
| Análise técnica | P0 | HiLo Activator, Fibonacci, Gann |
| Orquestrador de ordens | P0 | Modo DEMO inicialmente |
| Explicabilidade | P0 | Motivo textual para cada decisão |

### 4.6 Módulo de Bots

| Funcionalidade | Prioridade | Descrição |
|----------------|------------|-----------|
| Lista de Bots | P0 | Listar bots e status |
| Criar/Editar Bot | P0 | Configurar estratégia básica |
| Monitoramento | P0 | Status em tempo real |

### 4.7 Integrações

| Integração | Prioridade | Descrição |
|------------|------------|-----------|
| Cedro OMS | P0 | Conexão com corretoras |
| API B3 | P0 | Dados de mercado brasileiro |
| API S&P | P1 | Dados de mercado americano |
| API Criptos | P0 | Dados de criptomoedas |
| Telegram | P1 | Alertas e notificações |

---

## 5. Requisitos de Interface

### 5.1 Identidade Visual

| Elemento | Especificação |
|----------|---------------|
| Cor de Fundo | #0A192F (Azul Noturno) |
| Cor de Destaque | #FFD700 (Dourado Quantum) |
| Cor Positiva | #28A745 (Verde) |
| Cor Negativa | #DC3545 (Vermelho) |
| Tipografia | Montserrat (700, 600, 400) |
| Cards | border-radius: 8px-12px |

### 5.2 Layout Padrão

| Elemento | Especificação |
|----------|---------------|
| Header | Fixo, máximo 1,5cm de altura |
| Menu Sanduíche | Canto superior esquerdo, abre ao hover |
| Logo | 1x1 cm com nome "Quantum Trade" |
| Centro do Header | Status B3, S&P500, Cripto |
| Direita do Header | Notificações, cadastro de alertas, conta |

### 5.3 Mapa de Telas MVP

| Tela | Prioridade | Persona Foco |
|------|------------|--------------|
| Landing Page | P0 | Todas |
| Cadastro / Login | P0 | Todas |
| Onboarding Inicial | P0 | Jogador em Transição / Cauteloso |
| Dashboard Geral | P0 | Todas |
| Tela Portfólio | P0 | Trader Ocupado / Cauteloso |
| Tela Performance | P1 | Trader Ocupado |
| Lista de Bots | P0 | Todas |
| Criar / Editar Bot | P0 | Trader Ocupado / Jogador |
| Operações Recentes | P0 | Todas |
| Tela de Planos / Trial | P0 | Todas |
| Ajuda / FAQ / Riscos | P1 | Cauteloso / Reguladores |

---

## 6. Requisitos de Segurança e Compliance

### 6.1 Segurança

| Requisito | Descrição |
|-----------|-----------|
| Secrets | Nunca armazenar em código, usar variáveis de ambiente |
| Audit Trail | Todas as ações devem gerar log imutável |
| Logs | Timestamp, usuário, ordem, corretora, status |
| 2FA | Obrigatório para todos os usuários |
| Criptografia | Senhas e dados sensíveis criptografados |

### 6.2 Regras de Risco (Soberanas - Não Flexíveis)

| Regra | Descrição |
|-------|-----------|
| Stop Loss | Limites de perda não podem ser desabilitados |
| Circuit Breakers | Gatilhos automáticos de proteção |
| Drawdown Global | STOP TRADING se > 8% em 24h |
| Drawdown por Modelo | PAUSAR MODELO se > 15% |

### 6.3 Compliance

| Área | Requisito |
|------|-----------|
| CVM | Conformidade com regulamentação |
| B3 | Conformidade com regras da bolsa |
| LGPD | Proteção de dados pessoais |
| Termos | Aceite explícito obrigatório |

---

## 7. Requisitos Não-Funcionais

### 7.1 Performance

| Métrica | Requisito |
|---------|-----------|
| Latência API | < 200ms para operações críticas |
| Disponibilidade | 99.9% uptime |
| Concorrência | Suportar 1.000 usuários (Fase 3) |

### 7.2 Qualidade de Código

| Requisito | Descrição |
|-----------|-----------|
| Tipagem | Código 100% tipado |
| Testes | Unitários e de integração |
| Idempotência | Ordens devem ser idempotentes |
| Retry | Controlado com backoff exponencial |
| Tratamento de Falhas | Explícito e documentado |

### 7.3 Observabilidade

| Componente | Requisito |
|------------|-----------|
| Logs | Estruturados e centralizados |
| Métricas | Dashboard de monitoramento |
| Traces | Distribuídos para debugging |
| Alertas | Automáticos para incidentes |

---

## 8. KPIs do MVP

### 8.1 Produto

| KPI | Meta |
|-----|------|
| Usuários cadastrados | A definir |
| MAU (Usuários ativos mensais) | A definir |
| Bots por usuário | A definir |
| Taxa de ativação | A definir |

### 8.2 Retenção

| KPI | Meta |
|-----|------|
| Retenção D30 | A definir |
| Sessões semanais por usuário | A definir |

### 8.3 Percepção

| KPI | Meta |
|-----|------|
| NPS/CSAT | A definir |
| Tickets de suporte por 100 usuários | A definir |

---

## 9. Personas

| Persona | Perfil | Necessidades | Como Atendemos |
|---------|--------|--------------|----------------|
| Jogador em Transição | 22-34 anos, acostumado a bets | Transformar "sorte" em algo inteligente | Interface gamificada, termos simples, risco controlado |
| Trader Ocupado | 28-45 anos, já investe, trabalha em horário comercial | Automatizar estratégias | Bots prontos, dashboards claros, alertas 24/7 |
| Investidor Cauteloso | 30-55 anos, foco em preservação | Testar com risco controlado | Simulações, backtests, modos conservadores |

---

## 10. Restrições do Sistema

O sistema **NÃO DEVE**:

| Restrição | Justificativa |
|-----------|---------------|
| Fazer HFT | Fora do escopo e regulamentação |
| Executar estratégias sem autorização humana | Compliance e segurança |
| Assumir acesso direto à B3 | Deve usar intermediários autorizados |
| Simular market making | Fora do escopo regulatório |
| Prometer ganhos garantidos | Compliance e ética |

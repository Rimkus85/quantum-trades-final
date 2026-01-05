# Plano de Desenvolvimento do MVP - Sprints e Histórias de Usuário

**Versão:** 1.0  
**Data:** 05 de Janeiro de 2026  
**Fonte:** Requisitos Consolidados v1.0

---

## Introdução

Este documento detalha o plano de desenvolvimento para o MVP da Quantum Trades, quebrando o projeto em **seis sprints de desenvolvimento**. Cada sprint tem um objetivo claro e um conjunto de histórias de usuário a serem implementadas, garantindo um progresso iterativo e incremental em direção à plataforma final.

## Estrutura dos Sprints

| Sprint | Título | Objetivo Principal |
|--------|--------|--------------------|
| 1 | Fundação e Autenticação | Configurar a base do projeto e implementar o fluxo completo de autenticação e segurança. |
| 2 | Onboarding e Gestão de Planos | Implementar o fluxo de onboarding do usuário e a gestão de planos e assinaturas. |
| 3 | Dashboard e Visualização de Dados | Desenvolver o dashboard principal com a visualização dos dados da carteira do usuário. |
| 4 | Motor de IA (v1) e Bots | Implementar a primeira versão do motor de IA e o gerenciamento de bots. |
| 5 | Integrações e Alertas | Integrar com o Cedro OMS e implementar o sistema de alertas via Telegram. |
| 6 | Refinamento e Preparação para o Beta | Refinar a interface, corrigir bugs e preparar a plataforma para o lançamento em beta fechado. |

---

## Sprint 1: Fundação e Autenticação

**Objetivo:** Configurar a base do projeto e implementar o fluxo completo de autenticação e segurança.

| ID | História de Usuário | Critérios de Aceite |
|----|---------------------|----------------------|
| **QT-01** | **Como Desenvolvedor,** quero ter o ambiente de desenvolvimento (backend, frontend, DB) configurado para iniciar o projeto. | 1. Repositório Git inicializado com a estrutura de pastas da Clean Architecture. <br> 2. Backend FastAPI com conexão ao PostgreSQL. <br> 3. Frontend React/React Native com setup inicial. |
| **QT-02** | **Como Usuário,** quero poder me cadastrar na plataforma informando meus dados básicos (nome, CPF, e-mail, corretora). | 1. Formulário de cadastro implementado. <br> 2. Validação de CPF no formato correto. <br> 3. Dados do usuário salvos no banco de dados. |
| **QT-03** | **Como Usuário,** quero poder fazer login de forma segura utilizando meu e-mail, senha e um código 2FA. | 1. Tela de login com campos para e-mail, senha e 2FA. <br> 2. Senha armazenada de forma criptografada. <br> 3. Integração com Google Authenticator para geração de código 2FA. |
| **QT-04** | **Como Usuário,** quero poder recuperar minha senha caso a esqueça. | 1. Fluxo de "Esqueci a senha" implementado. <br> 2. Envio de código de recuperação para o e-mail do usuário. <br> 3. Tela para redefinição de senha. |

---

## Sprint 2: Onboarding e Gestão de Planos

**Objetivo:** Implementar o fluxo de onboarding do usuário e a gestão de planos e assinaturas.

| ID | História de Usuário | Critérios de Aceite |
|----|---------------------|----------------------|
| **QT-05** | **Como Novo Usuário,** quero responder a um questionário para que a plataforma entenda meu perfil de risco e objetivos. | 1. Questionário de perfil de risco implementado. <br> 2. Perfil do usuário (Conservador, Moderado, Agressivo) salvo no banco de dados. |
| **QT-06** | **Como Novo Usuário,** quero ler e aceitar os Termos de Uso, Política de Privacidade e Política de Risco. | 1. Telas com os termos legais implementadas. <br> 2. Aceite do usuário registrado no banco de dados. |
| **QT-07** | **Como Usuário,** quero poder escolher entre os diferentes planos de assinatura (Entrada, Médio, Top). | 1. Tela de seleção de planos com descrição de cada um. <br> 2. Integração com a API de pagamento (cartão de crédito). |
| **QT-08** | **Como Novo Usuário,** quero poder experimentar a plataforma em um modo de teste (Trial) por um tempo limitado. | 1. Implementação do modo Trial com timer. <br> 2. Banner ou modal para incentivar a contratação do plano. |

---

## Sprint 3: Dashboard e Visualização de Dados

**Objetivo:** Desenvolver o dashboard principal com a visualização dos dados da carteira do usuário.

| ID | História de Usuário | Critérios de Aceite |
|----|---------------------|----------------------|
| **QT-09** | **Como Usuário,** quero ver um resumo da minha carteira no dashboard, incluindo valor total, retorno e número de trades. | 1. Cards de resumo implementados no dashboard. <br> 2. Dados populados a partir do banco de dados (inicialmente com dados mockados). |
| **QT-10** | **Como Usuário,** quero ver a distribuição do meu portfólio por classe de ativo (Ações, Opções, Cripto). | 1. Componente de portfólio com cards para cada classe de ativo. <br> 2. Funcionalidade de expandir para ver detalhes dos ativos. |
| **QT-11** | **Como Usuário,** quero ver uma lista das minhas 10 operações mais recentes. | 1. Tabela de operações recentes implementada. <br> 2. Dados da tabela atualizados em tempo real (ou com alta frequência). |
| **QT-12** | **Como Usuário,** quero ver um gráfico da performance da minha carteira ao longo do tempo. | 1. Gráfico de performance implementado. <br> 2. Integração com APIs de mercado (B3, Cripto) para obter dados de cotação. |

---

## Sprint 4: Motor de IA (v1) e Bots

**Objetivo:** Implementar a primeira versão do motor de IA e o gerenciamento de bots.

| ID | História de Usuário | Critérios de Aceite |
|----|---------------------|----------------------|
| **QT-13** | **Como Sistema,** quero ter um motor de decisão que analise o mercado e gere recomendações de trade com base em 2-3 setups básicos. | 1. Motor de IA v1 implementado em Python. <br> 2. Lógica para os setups iniciais (ex: Cruzamento de Médias, IFR2) implementada. |
| **QT-14** | **Como Sistema,** quero ter um orquestrador que receba as decisões da IA e as prepare para envio (em modo DEMO). | 1. Orquestrador de ordens implementado. <br> 2. Ordens salvas no banco de dados com status "DEMO". |
| **QT-15** | **Como Usuário,** quero poder ver uma lista dos meus bots de automação e seu status (ativo, pausado). | 1. Tela de listagem de bots implementada. <br> 2. Status dos bots atualizado em tempo real. |
| **QT-16** | **Como Usuário,** quero poder criar um novo bot, selecionando uma das estratégias disponíveis. | 1. Tela de criação/edição de bots. <br> 2. Formulário para configurar os parâmetros do bot. |

---

## Sprint 5: Integrações e Alertas

**Objetivo:** Integrar com o Cedro OMS e implementar o sistema de alertas via Telegram.

| ID | História de Usuário | Critérios de Aceite |
|----|---------------------|----------------------|
| **QT-17** | **Como Sistema,** quero me conectar à API do Cedro OMS para enviar e consultar o status das ordens. | 1. Adapter para o Cedro OMS implementado. <br> 2. Conexão com o ambiente de sandbox do Cedro OMS estabelecida. |
| **QT-18** | **Como Usuário,** quero receber alertas no Telegram sobre as operações realizadas e oportunidades identificadas. | 1. Integração com a API do Telegram. <br> 2. Serviço de notificação que envia mensagens para o usuário. |
| **QT-19** | **Como Usuário,** quero poder cadastrar alertas de preço para ações e criptomoedas. | 1. Funcionalidade de cadastro de alertas no frontend. <br> 2. Serviço de backend que monitora os preços e dispara os alertas. |

---

## Sprint 6: Refinamento e Preparação para o Beta

**Objetivo:** Refinar a interface, corrigir bugs e preparar a plataforma para o lançamento em beta fechado.

| ID | História de Usuário | Critérios de Aceite |
|----|---------------------|----------------------|
| **QT-20** | **Como Usuário,** quero ter uma experiência de uso fluida e intuitiva em todas as telas da plataforma. | 1. Revisão completa da UI/UX com base no Manual Mestre. <br> 2. Ajustes de layout, cores e tipografia. |
| **QT-21** | **Como Equipe,** quero ter um conjunto de testes de ponta a ponta que valide os principais fluxos do usuário. | 1. Suíte de testes e2e implementada com Pytest ou similar. <br> 2. Testes cobrindo cadastro, login, criação de bot e visualização do dashboard. |
| **QT-22** | **Como Product Manager,** quero ter um dashboard com as principais métricas de performance e engajamento do sistema. | 1. Dashboard de métricas implementado (ex: com Grafana ou similar). <br> 2. Métricas como MAU, retenção e número de trades sendo coletadas. |
| **QT-23** | **Como Beta Tester,** quero ter uma documentação clara sobre como usar a plataforma e reportar bugs. | 1. Guia do beta tester criado. <br> 2. Canal de comunicação para feedback estabelecido. |

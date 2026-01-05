# Plano de Desenvolvimento do MVP - Sprints e Histórias de Usuário

**Versão:** 1.1  
**Data:** 05 de Janeiro de 2026  
**Fonte:** Requisitos Consolidados v1.0 + Mapa Mental

---

## Introdução

Este documento detalha o plano de desenvolvimento para o MVP da Quantum Trades, quebrando o projeto em **sete sprints de desenvolvimento**. Cada sprint tem um objetivo claro e um conjunto de histórias de usuário a serem implementadas, garantindo um progresso iterativo e incremental em direção à plataforma final.

## Estrutura dos Sprints

| Sprint | Título | Objetivo Principal |
|--------|--------|--------------------|
| 0 | Landing Page e Marketing | Desenvolver a página de entrada (Fan Page) para captura de leads e comunicação da proposta de valor. |
| 1 | Fundação e Autenticação | Configurar a base do projeto e implementar o fluxo completo de autenticação e segurança. |
| 2 | Onboarding e Gestão de Planos | Implementar o fluxo de onboarding do usuário e a gestão de planos e assinaturas. |
| 3 | Dashboard e Visualização de Dados | Desenvolver o dashboard principal com a visualização dos dados da carteira do usuário. |
| 4 | Motor de IA (v1) e Bots | Implementar a primeira versão do motor de IA e o gerenciamento de bots. |
| 5 | Integrações e Alertas | Integrar com o Cedro OMS e implementar o sistema de alertas via Telegram. |
| 6 | Refinamento e Preparação para o Beta | Refinar a interface, corrigir bugs e preparar a plataforma para o lançamento em beta fechado. |

---

## Sprint 0: Landing Page e Marketing

**Objetivo:** Desenvolver a Landing Page (Fan Page) como porta de entrada da plataforma, capturando leads e comunicando a proposta de valor.

**Diretrizes de Design (do Mapa Mental):**
- Design moderno utilizando imagens futuristas neon que remetam a abundância e riqueza
- Precisa ser calmo e impactante
- Descrever as vantagens
- Apresentar os ganhos

| ID | História de Usuário | Critérios de Aceite |
|----|---------------------|----------------------|
| **QT-LP-01** | **Como Visitante,** quero acessar uma página inicial atraente que explique o que é a Quantum Trades e suas vantagens. | 1. Hero section com headline impactante e imagem futurista neon. <br> 2. Seção de vantagens com cards/ícones. <br> 3. Design responsivo (desktop, tablet, mobile). <br> 4. Paleta de cores: Fundo #0A192F, Destaque #FFD700. |
| **QT-LP-02** | **Como Visitante,** quero ver como a plataforma funciona em passos simples para entender se é para mim. | 1. Seção "Como Funciona" com 3-4 etapas ilustradas. <br> 2. Linguagem simples e acessível. <br> 3. Ícones ou animações para cada etapa. |
| **QT-LP-03** | **Como Visitante,** quero ver os resultados e ganhos potenciais da plataforma de forma transparente. | 1. Seção de resultados com dados reais ou simulados. <br> 2. Disclaimers legais visíveis (ex: "Resultados passados não garantem resultados futuros"). <br> 3. Gráficos de performance ilustrativos. |
| **QT-LP-04** | **Como Visitante,** quero comparar os planos disponíveis para escolher o mais adequado. | 1. Tabela comparativa dos 3 planos (Entrada, Médio, Top). <br> 2. Preços e features claramente listados. <br> 3. CTA para cada plano. <br> 4. Destaque visual para o plano recomendado. |
| **QT-LP-05** | **Como Visitante,** quero me cadastrar na plataforma através de um formulário simples. | 1. Formulário com campos: Nome Completo, CPF (xxx.xxx.xxx-xx), E-mail, Corretora(s). <br> 2. Validação de CPF no formato correto. <br> 3. Checkbox de corretoras: XP, Clear, Inter, Rico, Genial, Toro, Nu Invest, BTG, "Ainda não tenho conta". <br> 4. "Ainda não tenho conta" anula todas as outras opções quando selecionada. <br> 5. Botão de enviar. <br> 6. Após envio: QR Code para Google Authenticator + Botão "Seguir". |
| **QT-LP-06** | **Como Visitante,** quero ter minhas dúvidas respondidas antes de me cadastrar. | 1. Seção de FAQ com pelo menos 8-10 perguntas frequentes. <br> 2. Accordion ou tabs para organização. <br> 3. Perguntas sobre segurança, riscos, planos e funcionamento. |
| **QT-LP-07** | **Como Marketing,** quero que a página seja otimizada para SEO e conversão. | 1. Meta tags configuradas (title, description, keywords). <br> 2. Open Graph para redes sociais. <br> 3. Lighthouse score > 90. <br> 4. Integração com Google Analytics. <br> 5. Tempo de carregamento < 3s em 3G. |

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
| **QT-08** | **Como Novo Usuário,** quero poder experimentar a plataforma em um modo de teste (Trial) por um tempo limitado. | 1. Implementação do modo Trial com timer (30 segundos na tela informativa). <br> 2. Banner ou modal para incentivar a contratação do plano. <br> 3. Botões "Deseja contratar agora?" (Sim/Não). |

---

## Sprint 3: Dashboard e Visualização de Dados

**Objetivo:** Desenvolver o dashboard principal com a visualização dos dados da carteira do usuário.

| ID | História de Usuário | Critérios de Aceite |
|----|---------------------|----------------------|
| **QT-09** | **Como Usuário,** quero ver um resumo da minha carteira no dashboard, incluindo valor total, retorno e número de trades. | 1. Cards de resumo implementados no dashboard. <br> 2. Dados populados a partir do banco de dados (inicialmente com dados mockados). |
| **QT-10** | **Como Usuário,** quero ver a distribuição do meu portfólio por classe de ativo (Ações, Opções, Cripto). | 1. Componente de portfólio com cards para cada classe de ativo. <br> 2. Funcionalidade de expandir para ver detalhes dos ativos. <br> 3. Itens: Ações B3, Ações Internacionais, Opções, Futuro Cripto. |
| **QT-11** | **Como Usuário,** quero ver uma lista das minhas 10 operações mais recentes. | 1. Tabela de operações recentes implementada. <br> 2. Colunas: Ativo, Volume, Valor Entrada, Valor Atual, Resultado, Status (Ativo/Inativo). <br> 3. Dados atualizados em tempo real (ou com alta frequência). |
| **QT-12** | **Como Usuário,** quero ver um gráfico da performance da minha carteira ao longo do tempo. | 1. Gráfico de performance implementado. <br> 2. Seleção de período: desde o início, no mês, no ano, últimos 6 meses, últimos 90 dias. <br> 3. Comparativos: S&P, CDI, Dólar, B3, BTC. |

---

## Sprint 4: Motor de IA (v1) e Bots

**Objetivo:** Implementar a primeira versão do motor de IA e o gerenciamento de bots.

| ID | História de Usuário | Critérios de Aceite |
|----|---------------------|----------------------|
| **QT-13** | **Como Sistema,** quero ter um motor de decisão que analise o mercado e gere recomendações de trade com base em 2-3 setups básicos. | 1. Motor de IA v1 implementado em Python. <br> 2. Lógica para os setups iniciais (ex: Cruzamento de Médias, HiLo Activator) implementada. <br> 3. Só recomenda quando pontuação > 70. |
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

---

## Resumo de Histórias por Sprint

| Sprint | Título | Histórias | Total |
| :--- | :--- | :--- | :--- |
| **Sprint 0** | Landing Page e Marketing | QT-LP-01 a QT-LP-07 | 7 |
| **Sprint 1** | Fundação e Autenticação | QT-01 a QT-04 | 4 |
| **Sprint 2** | Onboarding e Gestão de Planos | QT-05 a QT-08 | 4 |
| **Sprint 3** | Dashboard e Visualização de Dados | QT-09 a QT-12 | 4 |
| **Sprint 4** | Motor de IA (v1) e Bots | QT-13 a QT-16 | 4 |
| **Sprint 5** | Integrações e Alertas | QT-17 a QT-19 | 3 |
| **Sprint 6** | Refinamento e Preparação para o Beta | QT-20 a QT-23 | 4 |
| **TOTAL** | | | **30** |

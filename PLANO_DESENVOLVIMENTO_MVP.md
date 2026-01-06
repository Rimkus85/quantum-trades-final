# Plano de Desenvolvimento e Documentação Técnica - Quantum Trades MVP

**Versão:** 1.1  
**Data:** 05 de Janeiro de 2026  
**Autor:** Manus AI

---

## 1. Introdução

Este documento consolida o plano de desenvolvimento e a documentação técnica para o **MVP (Minimum Viable Product)** da plataforma Quantum Trades. Ele foi elaborado com base no **Manual Mestre v3.0** e no **Mapa Mental** do projeto, servindo como um guia central para a equipe de desenvolvimento, produto e governança.

O objetivo é garantir que o desenvolvimento siga as diretrizes estratégicas, arquiteturais e de negócio, resultando em uma plataforma robusta, segura e alinhada com a visão da empresa: **democratizar o acesso a estratégias de investimento sofisticadas por meio da inteligência artificial**.

---

## 2. Visão Geral e Requisitos do MVP

Esta seção resume os requisitos funcionais e não-funcionais que definem o escopo do MVP, garantindo que a primeira versão do produto entregue valor real às nossas personas-alvo.

### 2.1. Arquitetura Obrigatória

A arquitetura segue o padrão **Clean Architecture / Hexagonal Architecture**, com uma separação explícita entre as camadas para garantir manutenibilidade e escalabilidade.

| Camada | Responsabilidade | Tecnologias Chave |
| :--- | :--- | :--- |
| **Domain** | Lógica de negócio central (Ordens, Contas, Risco) | Python, Pydantic |
| **Application** | Casos de uso e orquestração | Python, FastAPI |
| **Adapters** | Conexão com serviços externos (OMS, APIs) | Python, Requests |
| **Infrastructure** | Persistência, mensageria, logs | PostgreSQL, Redis/Kafka |
| **API** | Exposição dos serviços via REST | FastAPI |
| **UI** | Interface do usuário | React (Web), React Native (Mobile) |

> **Diretriz Crítica:** Nenhum código de integração com serviços externos (APIs de corretoras, OMS) deve vazar para a camada de Domínio. A lógica de negócio deve permanecer pura e agnóstica à infraestrutura.

### 2.2. Requisitos Funcionais Chave

O MVP se concentrará nas seguintes funcionalidades essenciais, priorizadas para entregar o ciclo de valor completo ao usuário.

| Módulo | Funcionalidades Essenciais do MVP |
| :--- | :--- |
| **Landing Page (Fan Page)** | Página de entrada com design futurista, apresentação das vantagens, exibição de ganhos potenciais e botão de cadastro. |
| **Autenticação e Segurança** | Cadastro de usuário, Login seguro com 2FA (Google Authenticator), e Recuperação de senha. |
| **Onboarding** | Questionário de perfil de risco, aceite dos termos legais e autorização para execução automática (opcional). |
| **Gestão de Planos** | Seleção entre 3 níveis de plano (Entrada, Médio, Top) e um modo de Trial com timer. |
| **Dashboard** | Visualização do valor total da carteira, retorno mensal, quantidade de trades, distribuição do portfólio e operações recentes. |
| **Motor de IA (v1)** | Sistema de decisão robusto e multidisciplinar com análise técnica, fundamentalista e de sentimento, ranking de predileção (>70), backtesting e aprendizado contínuo. Operação exclusiva com dados reais. Ver [SPRINT_4_MOTOR_IA.md](./docs/SPRINT_4_MOTOR_IA.md). |
| **Gestão de Bots** | Criação de bots com base nas estratégias disponíveis e visualização de seu status. |
| **Integrações** | Conexão com **Cedro OMS** para envio de ordens (em ambiente de sandbox) e APIs de mercado para cotações (B3, Cripto). |
| **Alertas** | Notificações via **Telegram** para operações e alertas de preço cadastrados pelo usuário. |

### 2.3. Requisitos de Segurança e Compliance (Não Negociáveis)

| Requisito | Descrição |
| :--- | :--- |
| **Armazenamento de Segredos** | Utilização exclusiva de variáveis de ambiente ou um serviço de Secret Manager. **NUNCA** armazenar segredos no código. |
| **Audit Trail** | Todas as ações críticas (criação de ordem, login, etc.) devem gerar um log imutável contendo timestamp, usuário, e detalhes da ação. |
| **Regras de Risco Soberanas** | Limites de Stop Loss e Circuit Breakers (ex: Drawdown global > 8%) são soberanos e não podem ser desabilitados pelo usuário. |
| **Conformidade Legal** | Aderência estrita às normativas da CVM, B3 e LGPD. O fluxo de aceite dos termos legais é obrigatório. |

---

## 3. Landing Page (Fan Page) - Especificação Detalhada

A Landing Page é a porta de entrada da plataforma e deve causar uma primeira impressão impactante, comunicando confiança, tecnologia e resultados. Esta seção detalha todos os requisitos extraídos do Mapa Mental e do Manual Mestre.

### 3.1. Diretrizes de Design

| Aspecto | Especificação |
| :--- | :--- |
| **Estilo Visual** | Design moderno utilizando imagens futuristas com elementos neon que remetam a abundância e riqueza. |
| **Tom** | Calmo e impactante simultaneamente. Transmitir confiança sem agressividade. |
| **Paleta de Cores** | Fundo: #0A192F (Azul Noturno), Destaques: #FFD700 (Dourado Quantum), Texto: #FFFFFF |
| **Tipografia** | Montserrat (700 para títulos, 600 para botões, 400 para texto) |
| **Responsividade** | Totalmente responsiva para desktop, tablet e mobile |

### 3.2. Estrutura da Página

A Landing Page deve conter as seguintes seções, na ordem apresentada:

| Seção | Conteúdo | Objetivo |
| :--- | :--- | :--- |
| **Hero Section** | Headline impactante, subheadline explicativa, imagem/vídeo futurista, CTA principal | Capturar atenção e comunicar proposta de valor |
| **Vantagens** | Cards ou ícones descrevendo as principais vantagens da plataforma | Educar sobre benefícios |
| **Como Funciona** | Passos simples explicando o funcionamento (3-4 etapas) | Reduzir fricção e dúvidas |
| **Resultados/Ganhos** | Apresentação transparente de ganhos potenciais (com disclaimers legais) | Gerar interesse e credibilidade |
| **Planos** | Resumo dos 3 planos (Entrada, Médio, Top) com preços e features | Facilitar decisão de compra |
| **Depoimentos** | Testemunhos de usuários (quando disponíveis) | Prova social |
| **FAQ** | Perguntas frequentes sobre a plataforma | Eliminar objeções |
| **CTA Final** | Botão de cadastro com urgência | Converter visitante em lead |
| **Footer** | Links legais, contato, redes sociais | Compliance e navegação |

### 3.3. Formulário de Cadastro

O formulário de cadastro deve ser acessível via botão na Landing Page e conter os seguintes campos:

| Campo | Tipo | Validação | Obrigatório |
| :--- | :--- | :--- | :--- |
| **Nome Completo** | Texto | Mínimo 3 caracteres | Sim |
| **CPF** | Texto com máscara | Formato xxx.xxx.xxx-xx, validação de dígitos | Sim |
| **E-mail** | E-mail | Formato válido de e-mail | Sim |
| **Corretora(s)** | Checkbox múltipla escolha | Pelo menos uma selecionada (ou "Ainda não tenho conta") | Sim |

**Opções de Corretora:**

| Corretora | Comportamento |
| :--- | :--- |
| XP | Seleção múltipla permitida |
| Clear | Seleção múltipla permitida |
| Inter | Seleção múltipla permitida |
| Rico | Seleção múltipla permitida |
| Genial | Seleção múltipla permitida |
| Toro | Seleção múltipla permitida |
| Nu Invest | Seleção múltipla permitida |
| BTG | Seleção múltipla permitida |
| **Ainda não tenho conta** | Anula todas as outras alternativas quando selecionada |

**Após o envio do formulário:**
1. Exibir QR Code para cadastro do Google Authenticator
2. Botão "Seguir" para continuar o fluxo de onboarding

### 3.4. Elementos de Conversão

| Elemento | Especificação |
| :--- | :--- |
| **CTA Principal** | Botão dourado (#FFD700) com texto "Começar Agora" ou "Criar Conta Grátis" |
| **CTA Secundário** | Link para "Saiba Mais" ou "Ver Planos" |
| **Urgência** | Contador de vagas limitadas ou oferta por tempo limitado (se aplicável) |
| **Trust Badges** | Selos de segurança, criptografia, conformidade |

### 3.5. SEO e Performance

| Requisito | Especificação |
| :--- | :--- |
| **Meta Tags** | Title, description e keywords otimizados para "trading automatizado", "robô de investimento", "IA financeira" |
| **Open Graph** | Tags para compartilhamento em redes sociais |
| **Performance** | Lighthouse score > 90 em todas as métricas |
| **Tempo de Carregamento** | < 3 segundos em conexão 3G |

---

## 4. Plano de Desenvolvimento em Sprints

O desenvolvimento do MVP será dividido em **sete sprints**, permitindo entregas incrementais e validação contínua. A Landing Page foi adicionada como **Sprint 0** por ser o primeiro ponto de contato com o usuário.

### Sprint 0: Landing Page e Marketing

**Objetivo:** Desenvolver a Landing Page (Fan Page) como porta de entrada da plataforma, capturando leads e comunicando a proposta de valor.

| ID | História de Usuário | Critérios de Aceite |
| :--- | :--- | :--- |
| **QT-LP-01** | **Como Visitante,** quero acessar uma página inicial atraente que explique o que é a Quantum Trades e suas vantagens. | 1. Hero section com headline impactante e imagem futurista. <br> 2. Seção de vantagens com cards/ícones. <br> 3. Design responsivo (desktop, tablet, mobile). |
| **QT-LP-02** | **Como Visitante,** quero ver como a plataforma funciona em passos simples para entender se é para mim. | 1. Seção "Como Funciona" com 3-4 etapas ilustradas. <br> 2. Linguagem simples e acessível. |
| **QT-LP-03** | **Como Visitante,** quero ver os resultados e ganhos potenciais da plataforma de forma transparente. | 1. Seção de resultados com dados reais ou simulados. <br> 2. Disclaimers legais visíveis. <br> 3. Gráficos de performance ilustrativos. |
| **QT-LP-04** | **Como Visitante,** quero comparar os planos disponíveis para escolher o mais adequado. | 1. Tabela comparativa dos 3 planos (Entrada, Médio, Top). <br> 2. Preços e features claramente listados. <br> 3. CTA para cada plano. |
| **QT-LP-05** | **Como Visitante,** quero me cadastrar na plataforma através de um formulário simples. | 1. Formulário com campos: Nome, CPF, E-mail, Corretora(s). <br> 2. Validação de CPF no formato correto. <br> 3. Checkbox de corretoras com lógica de exclusão mútua para "Ainda não tenho conta". |
| **QT-LP-06** | **Como Visitante,** quero ter minhas dúvidas respondidas antes de me cadastrar. | 1. Seção de FAQ com pelo menos 8-10 perguntas frequentes. <br> 2. Accordion ou tabs para organização. |
| **QT-LP-07** | **Como Marketing,** quero que a página seja otimizada para SEO e conversão. | 1. Meta tags configuradas. <br> 2. Open Graph para redes sociais. <br> 3. Lighthouse score > 90. <br> 4. Integração com Google Analytics. |

### Sprint 1: Fundação e Autenticação

**Objetivo:** Configurar a base do projeto e implementar o fluxo completo de autenticação e segurança.

| ID | História de Usuário | Critérios de Aceite |
| :--- | :--- | :--- |
| **QT-01** | **Como Desenvolvedor,** quero ter o ambiente de desenvolvimento (backend, frontend, DB) configurado. | 1. Repositório Git com estrutura da Clean Architecture. <br> 2. Backend FastAPI conectado ao PostgreSQL. <br> 3. Frontend React/React Native com setup inicial. |
| **QT-02** | **Como Usuário,** quero poder me cadastrar na plataforma informando meus dados básicos. | 1. Formulário de cadastro implementado. <br> 2. Validação de CPF. <br> 3. Dados salvos no banco de dados. |
| **QT-03** | **Como Usuário,** quero poder fazer login de forma segura utilizando e-mail, senha e código 2FA. | 1. Tela de login com campo para 2FA. <br> 2. Senha armazenada com hash. <br> 3. Integração com Google Authenticator. |
| **QT-04** | **Como Usuário,** quero poder recuperar minha senha caso a esqueça. | 1. Fluxo de "Esqueci a senha" via e-mail. <br> 2. Tela para redefinição de senha. |

### Sprint 2: Onboarding e Gestão de Planos

**Objetivo:** Implementar o fluxo de onboarding do usuário e a gestão de planos e assinaturas.

| ID | História de Usuário | Critérios de Aceite |
| :--- | :--- | :--- |
| **QT-05** | **Como Novo Usuário,** quero responder a um questionário para que a plataforma entenda meu perfil de risco. | 1. Questionário de perfil de risco implementado. <br> 2. Perfil do usuário salvo no banco de dados. |
| **QT-06** | **Como Novo Usuário,** quero ler e aceitar os Termos de Uso, Política de Privacidade e Política de Risco. | 1. Telas com os termos legais. <br> 2. Registro do aceite do usuário. |
| **QT-07** | **Como Usuário,** quero poder escolher entre os diferentes planos de assinatura. | 1. Tela de seleção de planos. <br> 2. Integração com API de pagamento (cartão de crédito). |
| **QT-08** | **Como Novo Usuário,** quero poder experimentar a plataforma em um modo de teste (Trial). | 1. Implementação do modo Trial com timer. <br> 2. Banner para incentivar a contratação. |

### Sprint 3: Dashboard e Visualização de Dados

**Objetivo:** Desenvolver o dashboard principal com a visualização dos dados da carteira do usuário.

| ID | História de Usuário | Critérios de Aceite |
| :--- | :--- | :--- |
| **QT-09** | **Como Usuário,** quero ver um resumo da minha carteira no dashboard. | 1. Cards de resumo (valor total, retorno, etc.). <br> 2. Dados populados a partir do banco de dados. |
| **QT-10** | **Como Usuário,** quero ver a distribuição do meu portfólio por classe de ativo. | 1. Componente de portfólio com cards para cada classe. <br> 2. Funcionalidade de expandir para ver detalhes. |
| **QT-11** | **Como Usuário,** quero ver uma lista das minhas 10 operações mais recentes. | 1. Tabela de operações recentes implementada. <br> 2. Dados atualizados com alta frequência. |
| **QT-12** | **Como Usuário,** quero ver um gráfico da performance da minha carteira. | 1. Gráfico de performance implementado. <br> 2. Integração com APIs de mercado (B3, Cripto). |

### Sprint 4: Motor de IA (Cérebro do Sistema)

**Objetivo:** Implementar o Motor de Decisão de IA robusto e multidisciplinar, o coração da Quantum Trades. Operação exclusiva com dados reais.

> **Documentação Completa:** Ver [SPRINT_4_MOTOR_IA.md](./docs/SPRINT_4_MOTOR_IA.md) para especificação detalhada.

| ID | História de Usuário | Critérios de Aceite |
| :--- | :--- | :--- |
| **QT-IA-01** | **Como Sistema,** quero rodar um processo diário (22:00 UTC-3) que combina análises (Fundamentalista, Gráfica, Sentimento, Sazonalidade) para rankear as estratégias mais rentáveis por papel. | 1. Implementação do algoritmo `Forrestthree`. <br> 2. Geração de um Ranking de Estratégias (RK) diário. <br> 3. O RK é usado para balizar o % de alocação de capital. |
| **QT-IA-02** | **Como Sistema,** quero usar o resultado do ranking para gerar uma lista de oportunidades para o dia seguinte, com % de acurácia e expectativa de acerto. | 1. O processo das 22:00 gera uma lista de trades potenciais. <br> 2. Cada oportunidade na lista contém as métricas de acurácia e expectativa. |
| **QT-IA-03** | **Como Sistema,** quero rodar uma análise gráfica a cada 5 minutos para identificar oportunidades e setups intraday. | 1. Implementação da análise de padrões (OCO, Engolfo, etc.). <br> 2. Geração de sinais de entrada/saída intraday. |
| **QT-IA-04** | **Como Sistema,** quero aprender com meus erros, capturando a causa raiz de cada `stoploss` para ajustar futuras análises. | 1. Implementação do módulo `Brainding+LLM`. <br> 2. Criação de um log de aprendizado (causa-raiz do erro -> ajuste). |
| **QT-IA-05** | **Como Sistema,** quero varrer fontes externas (YouTube, sites, Telegram) para aprender com canais reais e refinar minhas estratégias. | 1. Implementação de um scraper/parser para fontes externas. <br> 2. O conteúdo extraído alimenta o módulo `Brainding+LLM`. |
| **QT-IA-06** | **Como Sistema (Analista Senior),** quero definir estratégias de proteção (opções, aluguel) para cada papel, a fim de minimizar perdas e potencializar ganhos. | 1. Módulo de análise de risco que sugere operações de hedge. <br> 2. As sugestões de proteção são anexadas à `DecisaoTrade`. |
| **QT-IA-07** | **Como Sistema (Avaliações Ocultas),** quero calcular meu próprio impacto potencial no preço de um ativo e usar essa informação como um impulsionador de resultado. | 1. Implementação do módulo confidencial de análise de impacto. <br> 2. O resultado é usado na decisão final, mas **não é logado**. |
| **QT-IA-08** | **Como Sistema,** quero consolidar todas as análises em uma pontuação final e só gerar uma `DecisaoTrade` se a pontuação for > 70. | 1. Orquestrador de Decisão que agrega todos os scores. <br> 2. Geração do `DecisaoTrade` JSON completo, incluindo `motivo_textual` detalhado. |

### Sprint 5: Integrações e Alertas

**Objetivo:** Integrar com o Cedro OMS e implementar o sistema de alertas via Telegram.

| ID | História de Usuário | Critérios de Aceite |
| :--- | :--- | :--- |
| **QT-17** | **Como Sistema,** quero me conectar à API do Cedro OMS para enviar e consultar ordens. | 1. Adapter para o Cedro OMS implementado. <br> 2. Conexão com o ambiente de sandbox do Cedro OMS. |
| **QT-18** | **Como Usuário,** quero receber alertas no Telegram sobre operações e oportunidades. | 1. Integração com a API do Telegram. <br> 2. Serviço de notificação implementado. |
| **QT-19** | **Como Usuário,** quero poder cadastrar alertas de preço para ativos. | 1. Funcionalidade de cadastro de alertas no frontend. <br> 2. Serviço de backend que monitora e dispara os alertas. |

### Sprint 6: Refinamento e Preparação para o Beta

**Objetivo:** Refinar a interface, corrigir bugs e preparar a plataforma para o lançamento em beta fechado.

| ID | História de Usuário | Critérios de Aceite |
| :--- | :--- | :--- |
| **QT-20** | **Como Usuário,** quero ter uma experiência de uso fluida e intuitiva. | 1. Revisão completa da UI/UX com base no Manual Mestre. <br> 2. Ajustes de layout, cores e tipografia. |
| **QT-21** | **Como Equipe,** quero ter testes de ponta a ponta que validem os fluxos principais. | 1. Suíte de testes e2e implementada. <br> 2. Testes cobrindo cadastro, login, criação de bot e dashboard. |
| **QT-22** | **Como Product Manager,** quero ter um dashboard com as métricas de performance do sistema. | 1. Dashboard de métricas implementado (ex: Grafana). <br> 2. Coleta de métricas como MAU, retenção, etc. |
| **QT-23** | **Como Beta Tester,** quero ter uma documentação clara sobre como usar a plataforma. | 1. Guia do beta tester criado. <br> 2. Canal de comunicação para feedback estabelecido. |

---

## 5. Resumo dos Sprints e Histórias

| Sprint | Título | Histórias | Total |
| :--- | :--- | :--- | :--- |
| **Sprint 0** | Landing Page e Marketing | QT-LP-01 a QT-LP-07 | 7 |
| **Sprint 1** | Fundação e Autenticação | QT-01 a QT-04 | 4 |
| **Sprint 2** | Onboarding e Gestão de Planos | QT-05 a QT-08 | 4 |
| **Sprint 3** | Dashboard e Visualização de Dados | QT-09 a QT-12 | 4 |
| **Sprint 4** | Motor de IA (Cérebro do Sistema) | QT-IA-01 a QT-IA-08 | 8 |
| **Sprint 5** | Integrações e Alertas | QT-17 a QT-19 | 3 |
| **Sprint 6** | Refinamento e Preparação para o Beta | QT-20 a QT-23 | 4 |
| **TOTAL** | | | **34** |

---

## 6. Pontos de Risco e Mitigações

| Risco | Probabilidade | Impacto | Mitigação |
| :--- | :--- | :--- | :--- |
| **Risco de Modelo (IA)** | Média | Alto | Backtesting rigoroso, monitoramento contínuo da performance dos modelos, e implementação de circuit breakers automáticos. |
| **Risco de Execução (OMS)** | Baixa | Alto | Implementar o adapter com múltiplos retries controlados, reconciliação de ordens e monitoramento constante da conexão com o Cedro OMS. |
| **Risco Regulatório** | Média | Alto | Manter o escopo do MVP como ferramenta de automação (não consultoria), acompanhamento jurídico constante e roadmap regulatório faseado. |
| **Risco de Segurança** | Média | Alto | Pentests regulares, 2FA obrigatório, criptografia de dados em repouso e em trânsito, e política de segurança estrita. |
| **Risco de Conversão (Landing Page)** | Média | Médio | Testes A/B, otimização contínua baseada em métricas, e feedback de usuários. |

---

## 7. Próximos Passos

1.  **Kick-off do Sprint 0:** Iniciar o desenvolvimento da Landing Page com a equipe de frontend e design.
2.  **Definição de Wireframes:** Criar wireframes de baixa fidelidade para a Landing Page e validar com stakeholders.
3.  **Configuração do Ambiente:** Iniciar a configuração da infraestrutura base (repositório, CI/CD, banco de dados) em paralelo.
4.  **Revisão de Design:** Validar o design de alta fidelidade para a Landing Page com base no Manual Mestre.
5.  **Integração com Analytics:** Configurar Google Analytics e ferramentas de tracking para medir conversão desde o dia 1.

# Mapa Mental - Quantum Trades (Extraído)

## Estrutura Principal

### 1. Fan Page (Landing Page)
- Designer moderno utilizando imagens futuristas neon que remetam a abundância, riquezas
- Precisa ser calmo e impactante
- Descrever as vantagens
- Apresentar os ganhos
- **Botão de Cadastro**

### 2. Cadastro
- Nome Completo (obrigatório)
- CPF (preencher no padrão xxx.xxx.xxx-xx) (obrigatório)
- E-mail (obrigatório)
- Corretora (CheckBox de múltipla escolha):
  - XP
  - Clear
  - Inter
  - Rico
  - Genial
  - Toro
  - Nu Invest
  - BTG
  - "Ainda não tenho conta" (anula todas as outras alternativas)
- Botão de enviar
- QR Code para cadastro do Google Authenticator
- Botão seguir

### 3. Fluxo de Primeiro Acesso
- **Primeiro Acesso ou Não respondeu ao formulário?**
  - **Sim:** Abre formulário para conhecer perfil do usuário, objetivos para investimentos, tempo disponível, aportes mensais etc.
  - Passar os termos de aceite para uso da ferramenta
  
- **Autorizo a execução das ordens automaticamente de acordo com a estratégia definida?**
  - **Sim:** Verifica se já possui plano contratado
  - **Não:** Cadastro do Telegram para autorização remota

### 4. Fluxo de Planos
- **Já possui plano contratado?**
  - **Sim:** Vai para Dashboard
  - **Não:** Verifica Trial

- **Trial?**
  - **Sim:** Tela informativa do tempo restante com timer (30 segundos)
    - Botões: "Deseja contratar agora?" (Sim/Não)
  - **Não:** Tela para seleção do plano desejado

### 5. Planos Disponíveis

#### Plano Entrada
- Carteira de investimentos
- Conexão da corretora usando Cedro OMS
- Dashboard das corretoras
- Alertas no Telegram de ações cadastradas (limite de 3)
- Gamificação

#### Plano Médio
- Carteira de investimentos
- Conexão com a corretora
- Carteira automatizada de cripto futuros, com execuções automáticas
- Alertas no Telegram diário com a análise das criptos
- Alertas no Telegram de ações cadastradas (limite de 5)
- Carteira de opções automatizadas com execução automatizada
- Gamificação

#### Plano Top
- Tudo do médio
- Administração total da carteira, análise, envio de ordem e administração do gain e loss
- Customização de estratégia, com automação da análise e de envio de ordem
- Gamificação
- Research
- Análise de ações com uso da IA já treinada em mercado financeiro

### 6. Faturamento
- Apenas Cartão de crédito
- Executa ação → Envia para operadora de cartão → Valida
- Retorna validação do cartão
- Compra realizada com sucesso / Erro: Devolve o erro da operadora

### 7. Login
- Tela de login:
  - Usuário
  - Senha (Criptografada com opção de visualização)
  - Google Authenticator
  - Link: Esqueci a senha
  - Link: Não tenho cadastro

- **Esqueci a Senha:**
  - Envia código de recuperação no e-mail cadastrado
  - Frase: "Um código de recuperação foi enviado ao seu e-mail"
  - Tela de inserir código enviado por e-mail
  - Valida Login
    - Válido: Tela de redefinir senha
    - Não válido: Informativo "Código Inválido" → Volta para login

### 8. Padrões de Interface (Todas as Telas)

#### Header Fixo
- Faixa superior fixada (máximo 1,5cm de largura)
- Menu sanduíche no canto superior esquerdo
- Logo pequeno (1x1 cm) com nome "Quantum Trade" ao lado
- Centro: Status da B3, S&P500 e Cripto
- Canto superior direito: Sininho de notificações, sinal de mais para cadastro de alertas, botão discreto da conta

#### Menu Sanduíche (abre ao passar o mouse)

**DASHBOARD**
- Painel Principal
- Gráficos Avançados
- Portfólio
- Alerta

**INTELIGÊNCIA ARTIFICIAL**
- Painel de IA
- Predileções
- Análise de Sentimento
- Recomendações
- Definição de estratégias

**RESEARCH**
- Relatórios
- Quantum Call
- Giro de Mercado
- Radar FII's
- Radar de Opções

**CONFIGURAÇÕES**
- Configurações
- Conta
- Sair

#### Regras de UI
- No cabeçalho: % do cumprimento do objetivo (se objetivo cruzado: dinheiro + objetivo + tempo)
- Perfis limitados: experiência de ver opções sem dados habilitados (degustação)
- Ao tentar aplicar: aparecer tela de upgrade do plano
- Redundância de fonte de dados do mercado
- Logs detalhados de tudo

### 9. Dashboard - Painel Principal

**Contexto:** Panorama geral dos serviços contratados no perfil. Quando não habilitado, deixar cinza para mostrar disponibilidade com upgrade.

#### Componentes:
- **Total da Carteira:** Valor total administrado pelo Quantum Trade
- **Retorno Mensal:** Média de retorno mensal do valor total investido
  - Seleção de período: desde o início, no mês, no ano, últimos 6 meses, últimos 90 dias
  - Comparativos: S&P, CDI, Dólar, B3, BTC, Média Mês
- **Quantidade de Trades Realizados:** Soma de todas as operações
- **Portfólio:** Cards com resumo
  - Quantidade de ativos, valor investido, valor atual, % de ganho
  - Sinal de "+" para expandir tabela com ativos
  - Itens: Ações B3, Ações Internacionais, Opções, Futuro Cripto
- **Taxa de Acerto:** % de operações lucrativas
- **Operações Recentes:** Top 10 operações (ativo, volume, valor entrada, valor atual, resultado, status)
- **Gráfico de Performance Evolutivo**

#### APIs Necessárias:
- API para dados online da B3
- API para S&P (dados online das ações)
- API para dados online das criptos
- Conexão com banco de dados para históricos

### 10. Inteligência Artificial - Cérebro do Sistema

**Contexto:** Orquestra tudo - desde escolha da ação/cripto até recomendação de estratégia ao usuário.

#### Funcionalidades:
- Sistema de predileção com base em dados reais (mercados nacionais e internacionais, opções, criptomoedas)
- Análises customizadas de acordo com tempo de permanência do papel
- Só recomenda quando pontuação > 70
- Agente de IA financeiro autônomo (sistema híbrido de análise, recomendação e automação)
- Camada inteligente entre fontes de dados e usuários

#### Sistema de Conhecimento Unificado:
- Consolida informações de diversas fontes
- Aplica algoritmos de análise técnica (HiLo Activator, Fibonacci, Gann)
- Valida dados com sistema de expiração
- Aprende com feedback de operações
- Busca estratégias com maior probabilidade de sucesso

---

## Resumo de Funcionalidades MVP

1. **Autenticação e Segurança**
   - Cadastro com validação de dados
   - Login com 2FA (Google Authenticator)
   - Recuperação de senha

2. **Onboarding**
   - Questionário de perfil
   - Termos de aceite
   - Autorização de execução automática

3. **Gestão de Planos**
   - Trial com timer
   - 3 níveis de plano (Entrada, Médio, Top)
   - Pagamento via cartão de crédito

4. **Dashboard**
   - Painel principal com KPIs
   - Portfólio por classe de ativos
   - Operações recentes
   - Gráficos de performance

5. **Motor de IA**
   - Sistema de recomendações
   - Análise técnica automatizada
   - Execução de ordens (conforme plano)

6. **Integrações**
   - Cedro OMS
   - APIs de mercado (B3, S&P, Criptos)
   - Telegram para alertas

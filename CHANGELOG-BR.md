# Changelog — CBini OrquestrAI

🇺🇸 [English](CHANGELOG.md) · 🇧🇷 **Português** · 🇪🇸 [Español](CHANGELOG-ES.md)

Como o produto mudou, escrito para pessoas e não para máquinas. Cada entrada diz o que quem usa o OrquestrAI passou a conseguir fazer, ou
o que deixou de dar errado. Ferramentas internas, infraestrutura de testes e mecanismos de segurança aparecem resumidos, não listados.

O OrquestrAI foi idealizado e é conduzido por **Cristhian Bini, fundador da CBini Soluções em TI**. Ele define a visão do produto, toma as
decisões de produto e aprova cada versão. Agentes de IA atuam como colaboradores de engenharia: escrevem e testam código e propõem
mudanças. Uma pessoa aprova cada mudança antes de ela entrar no ar.

> **A IA acelera. O humano decide.**

**Estados.** **Publicada**: no ar na instalação em produção. **Em preparação**: construída e testada, ainda não lançada. **Planejado**:
ainda não é funcionalidade. Datas no formato AAAA-MM-DD.

---

## 0.45.0 — MVP · Em preparação

É a primeira versão pensada como produto mínimo completo. Ela só será lançada quando três construções reais passarem numa verificação
funcional pelo cockpit em produção, todas com modelos de IA gratuitos e custo zero. As três construções são um simulador de empréstimo, um
painel de dados e um site institucional. Tudo o que está listado abaixo já está no ar. O lançamento espera essas verificações e a decisão do
fundador.

**Entregue**
- **Telemetria restaurada e aprovada pelo fundador.** Mostra os últimos 30 dias e o histórico completo: investimento, tokens e economia
  estimada. Detalha o custo por tipo de cobrança, projeto, agente e modelo, e inclui o controle de gastos. Uma falha nos dados não apaga mais
  a tela inteira. Custo desconhecido aparece como "sem custo medido", nunca como gratuito.
- **Painel lateral da construção.** Mostra quais agentes não foram chamados e por quê, quanto tempo a construção levou de verdade e atalhos
  para o Preview e para o projeto.
- **Verificação funcional em cada construção.** Depois de uma construção, o app gerado é aberto e usado automaticamente. O projeto então
  mostra um de três vereditos: ACEITA, REPROVADA ou INCONCLUSIVA.
- **A Fábrica funciona com modelos gratuitos.** O raciocínio interno do modelo usa só uma parte do limite de saída, para o código gerado
  ainda caber. O modelo gratuito mais estável é tentado primeiro.
- **Gráficos nos apps gerados.** Barras, linha e pizza vêm de um componente da plataforma, em tamanho legível e sem biblioteca externa.
- **Filtros de dados nos painéis gerados.** Um filtro da plataforma permite escolher uma coluna e um valor, por exemplo *região = Sul*. Os
  totais e os gráficos acompanham o filtro. Quando o pedido fala em filtro e o código gerado não usa esse componente, a Fábrica manda
  aquela parte ser corrigida.
- **Menu que alcança todas as seções.** Em sites de uma página, o menu passa a listar as seções que existem. Um link que apontava para a
  própria página agora leva o visitante à primeira seção.
- **Liberação pelo operador.** Cada atualização do sistema em produção exige uma liberação digitada pelo operador. A liberação fica presa
  aos arquivos exatos que foram conferidos.

**Corrigido**
- A tela de Telemetria não carregava quando uma execução não tinha custo medido.
- A Fábrica tinha várias falhas que faziam a geração falhar ou sair quebrada:
  - um contrato dos módulos lido errado derrubava a geração;
  - um módulo chamava outro pelo nome errado e a página saía com "não definido";
  - um plano ilegível agora ganha mais uma tentativa;
  - um módulo recusado agora ganha mais uma tentativa;
  - erros de execução agora são pegos antes de o site ser publicado.
- O cabeçalho não mostra mais um número de versão provisório enquanto a página carrega.

## 0.44.2 — 2026-11-05 · Publicada
- **A Fábrica pode usar modelos pagos econômicos.** O custo máximo é mostrado e autorizado antes de qualquer gasto.
- **O Chat pago pergunta antes.** Cada mensagem paga espera a autorização do operador, com limite por mensagem. Clicar duas vezes não cobra
  duas vezes.
- **O Chat lê sozinho os arquivos do projeto,** somente leitura, em vez de pedir ao operador que rode comandos. Ele também sabe se o app
  está no ar, parado ou ainda não publicado.
- **Manual maior,** com busca e seções novas: o que funciona hoje, seu primeiro app e modelos pagos.
- **Correções:**
  - a lista de projetos podia esconder uma mensagem de erro;
  - uma construção interrompida por reinício continuava aparecendo como "gerando";
  - o cartão do site mostrava avisos vermelhos falsos;
  - uma falha ao registrar um custo agora trava novas chamadas pagas.

## 0.44.1 — 2026-11-04 · Publicada
- **O servidor recusa modelo pago sem uma janela de gasto aberta e autorizada,** mesmo escolhido à mão. Antes só a troca automática era
  barrada.
- **Mensagens mais claras:** o cartão de um app pronto não diz mais que os agentes estão trabalhando, e as recusas aparecem em português.

## 0.44.0 — 2026-11-04 · Publicada
- **Apps Full Stack novos podem ter até quatro cadastros relacionados,** por exemplo clientes e pedidos. Os apps existentes não mudam.
- **O operador escolhe o modelo de IA ao criar o app.** Um modelo gratuito confirmado vem marcado por padrão.
- **Um app interrompido pode ser retomado com modelo gratuito,** sem refazer o que já foi feito.
- **Mais provedores de IA:** MiniMax e DeepSeek podem ser configurados.
- **Correções:**
  - editar um registro num app gerado falhava dentro do Preview;
  - nomes internos apareciam na tela;
  - quando o modelo gratuito não responde, o cockpit agora diz isso e oferece outro.

## 0.43.0 — 2026-11-04 · Publicada
- **Uma construção de site interrompida se explica:** por que parou, o que foi feito, o que falta e como continuar. Não há troca automática
  para modelo pago.
- **O Chat grava o pedido antes de chamar a IA,** então uma falha do provedor nunca o perde.
- **Modelos favoritos,** gravados por usuário.
- **Painel de estado do primeiro produto,** montado a partir dos requisitos do produto.
- **Menos erros falsos:** uma alteração agora é conferida contra o que o pedido quis dizer.

## 0.42.0 – 0.42.5 — 2026-10-15 a 2026-10-16 · Publicadas
- **Apps gerados mais completos:**
  - campos de lista de opções, que aparecem como selos coloridos e podem ser filtrados;
  - campos de valor em reais, com totais;
  - gênero gramatical certo nos rótulos;
  - uma tela de **Detalhes** para cadastros com muitos campos.
- **Os sites gerados não inventam mais números de registro profissional nem CNPJ.** O que não foi informado aparece como "a informar".
- **Treinar um agente não corta mais parte do cartão dele.**
- **Verificação semanal sem itens vermelhos,** restauração do backup provada num container limpo e um guia de rotina do operador.

## 0.41.0 – 0.41.2 — 2026-10-14 a 2026-10-15 · Publicadas
- **Os apps gerados ganharam:**
  - edição, e exclusão com confirmação na própria tela;
  - busca e mensagem de sucesso depois de salvar;
  - números e datas no formato brasileiro;
  - layout em cartões no celular;
  - uma paleta de cores adequada ao negócio;
  - ordenação por coluna, e listas que carregam em lotes.
- **Revisão renderizada dos sites:** o contraste do texto é medido do jeito que o navegador pinta.
- **Um teste A/B pago mostrou** que um briefing de design faz sites claramente melhores. Ligá-lo é decisão do fundador.

## 0.40.0 – 0.40.6 — 2026-10-12 a 2026-10-14 · Publicadas
- **Uso de ponta a ponta testado num navegador real:** criar um projeto, construir, ver o Preview, conversar no Chat, depois preparar e
  confirmar uma alteração.
- **Toda execução termina num desfecho único e claro:** falhou sem alteração, parcial, aplicada, já aplicada, sem efeito ou indeterminado.
  Cada desfecho diz se é seguro rodar de novo.
- **Melhorias no cockpit:**
  - um login novo começa sem projeto aberto;
  - um botão **+** leva direto ao assistente de novo projeto;
  - o estado neutro fica sempre a um clique.
- **Reforço de segurança:** o Preview e o fluxo de desfazer foram reforçados depois de revisão independente.
- **Primeiro instalador para servidor novo.** Testado em container; a instalação limpa num servidor real ainda não foi comprovada.

## 0.39.0 — 2026-10-12 · Publicada
- **O EXPLICAR ficou mais resiliente e pode ser configurado.** Usa por padrão um modelo econômico, e diz o que um comando vai fazer e se dá
  para desfazer.
- **Resumos em linguagem simples dos comandos** em projetos de site, sem custo de IA.

## 0.37.0 – 0.38.0 — 2026-10-06 · Publicadas
- **O Chat é o caminho para mudar um projeto.** Os blocos de comando ficam guardados por projeto e não passam para outro. Há um único
  caminho governado de EXECUTAR.
- **Toda alteração é conferida contra a intenção depois de rodar.** Cada item sai como confirmado, falhou ou não verificado. Um código de
  saída de sucesso deixa de ser chamado de sucesso funcional.
- **A Fábrica mostra as etapas reais,** com o agente atual e os tempos reais.

## 0.36.0 — 2026-09-21 · Publicada
- **Projetos isolados no cockpit.** Blocos de comando, conversas e lições pertencem a um projeto.

## 0.35.0 — 2026-08-13 · Publicada
- **É possível definir um modelo para cada agente,** com troca auditável quando um provedor falha.
- **O ciclo de lições é curado por uma pessoa.**

## 0.33.0 – 0.34.0 — 2026-07-25 a 2026-07-28 · Publicadas
- **Reforço de segurança das credenciais e segredos.** Alternativas inseguras foram removidas. Uma troca completa dos segredos foi ensaiada
  e depois feita.

## 0.2.0 – 0.32.8 — 2026-06-30 a 2026-07-03 · Publicadas
- **O cockpit passou a usar uma camada de componentes React,** com cartões dos agentes ao vivo e custo por execução.
- **A versão mostrada no cockpit é lida deste histórico.**

## 0.1.0 — 2026-06-19 · Publicada
- **Primeira versão:** um cockpit multi-IA self-hosted, com aprovação humana antes da execução.

---

## Planejado
Ainda não são funcionalidades. Veja o [roadmap](docs/roadmap-br.md).
- Recuperação completa num servidor limpo.
- Instalador guiado: um comando e um assistente de configuração.
- Mais stacks e bancos de dados.

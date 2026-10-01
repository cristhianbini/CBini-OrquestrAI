# Visão técnica — CBini OrquestrAI

🇧🇷 **Português** · 🇺🇸 [English](technical-overview.md) · [README](../README.pt-BR.md) · [Modelo de segurança](security-model.pt-BR.md)

Esta página explica como o OrquestrAI se organiza e onde ficam as suas fronteiras. Descreve a arquitetura do produto, não a implementação;
o código-fonte é privado.

## A tese

Agentes de IA são motores. O OrquestrAI é a camada de engenharia que decide como o trabalho deles vira realidade.

Ele não concorre com os modelos nem com os agentes de código que usa. Ele organiza o trabalho deles, coloca uma decisão humana no ponto em
que a mudança fica real, isola a execução, mede o custo e guarda a evidência. Modelos e provedores podem mudar por baixo sem que a camada de
governança mude junto. Esta é a aposta de arquitetura do produto; não é apresentada aqui como vantagem de mercado comprovada.

## Dois planos

- **Plano de controle** — onde pessoas e agentes trabalham: conversas, planos, propostas, aprovações, custo, conhecimento, evidência.
  Ele nunca executa sozinho o que a IA produz.
- **Plano de execução** — onde a mudança acontece: ambientes curtos e restritos, que enxergam um projeto por vez.

O diagrama está na [versão em inglês](technical-overview.md#two-planes).

## A vida de uma mudança

| Etapa | O que acontece | Fronteira |
|---|---|---|
| 1. Intenção | O operador descreve a mudança no chat do projeto. | Toda conversa pertence a exatamente um projeto. |
| 2. Planejamento | Um planejador escolhe quais agentes especializados rodam; a saída e o custo de cada um ficam registrados. | Agentes produzem texto, nunca efeitos. |
| 3. Proposta | O que mudaria um sistema vira um bloco de comando com intenção declarada. | O chat não executa. |
| 4. Entendimento | Sob pedido, o bloco é explicado em linguagem simples: intenção, etapas, impacto, risco. | Explicar não executa nada. |
| 5. Decisão | O operador aprova, ou veta com um motivo que volta para o próximo plano. | Uma versão vetada nunca roda. |
| 6. Pré-checagem | O sistema lê o que o bloco pode tocar e recusa o que não consegue analisar com segurança. | Escopo incerto = recusa, não palpite. |
| 7. Execução | O bloco roda num ambiente descartável: sem rede, sistema somente leitura, sem privilégios, só aquele projeto montado. | Um projeto por execução. |
| 8. Evidência | Resultado, efeito medido e um registro encadeado são guardados; páginas alteradas ganham link de preview. | Registros à prova de adulteração. |
| 9. Reverter | O plano do desfazer aparece antes de qualquer reversão; a reversão também é registrada e pode ser refeita. | Só arquivos; dados de app ficam fora, por desenho. |

## O projeto como unidade de isolamento

O projeto é a fronteira de histórico de conversa, execução de comandos, sessões de terminal, previews e atribuição de custo. Trocar o
projeto ativo troca tudo isso junto. O terminal do operador no projeto é somente leitura e sem rede; mudanças passam por blocos aprovados.
O acesso administrativo ao servidor é uma superfície separada, que exige segundo fator a cada sessão.

## Agentes, provedores, custo e conhecimento

- **Agentes:** especializados (estratégia, exploração, arquitetura, código, revisão, testes, documentação, métricas); um planejador escolhe
  quais rodam; os não chamados aparecem como dispensados e não custam nada. Cada agente é roteado para um modelo de forma independente.
- **Provedores:** as rotas validadas usam modelos Anthropic e OpenAI; Groq, Gemini, OpenRouter, Cerebras, Z.ai e APIs compatíveis com
  OpenAI podem ser configurados e testados pelo painel. Chaves cifradas no servidor, nunca devolvidas ao navegador.
- **Custo:** cada chamada é registrada com projeto, agente, superfície, tokens e latência; sem preço conhecido, o custo aparece como
  *desconhecido*, nunca como zero.
- **Conhecimento:** o sistema pode propor lições; no modo governado, elas só chegam aos agentes depois de aprovadas e ativadas por uma pessoa.

## A fábrica de projetos

Um briefing curto vira projeto: agentes planejam, um gerador constrói, checagens automáticas recusam o que não funcionaria no preview
isolado, e o resultado abre em origem separada. Sites estáticos funcionam de ponta a ponta. O primeiro caminho full stack — React + Vite +
TypeScript, Express e SQLite num processo — está em validação: a IA escreve uma especificação validada e a aplicação é gerada a partir de um
modelo testado, com infraestrutura idêntica entre projetos. Rodar cada aplicação no próprio ambiente isolado é o trabalho em andamento.

## Recuperação

Código versionado. Estado operacional replicado continuamente e empacotado diariamente num backup cifrado fora do servidor; um verificador
automático confere cada pacote (completude e ausência de segredo em claro). Restauração provada em ambiente isolado; recuperação completa num
servidor novo está planejada e ainda não provada.

## Evidência de engenharia

Uma capacidade não conta porque o código existe. Conta quando o caminho foi provado: **desenho → prova automática → prova humana num
sistema real → revisão independente quando sensível → promoção**. Mudanças de execução, isolamento e recuperação passam por um auditor
independente, somente leitura, antes de promover; uma reprovação para a promoção mesmo com todos os testes funcionais verdes. O primeiro
gerador full stack é o exemplo: passou nos testes, a revisão achou casos de falha fora do caminho feliz, e ele foi segurado até a correção.

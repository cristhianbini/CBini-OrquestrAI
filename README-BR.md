# CBini OrquestrAI

![Self-hosted](https://img.shields.io/badge/deployment-self--hosted-2f3b4c) ![Human in the loop](https://img.shields.io/badge/governance-human--in--the--loop-2f3b4c) ![Node.js 24](https://img.shields.io/badge/Node.js-24-2f3b4c) ![Status](https://img.shields.io/badge/status-active%20development-2f3b4c)

🇧🇷 Desenvolvido no Brasil pela CBini Soluções em TI

🇧🇷 **Português** · 🇺🇸 [English](README.md)

[Por quê](#por-que-o-orquestrai) · [Como funciona](#como-funciona) · [Arquitetura](docs/arch-br.md) · [Decisões de projeto](docs/design-br.md) · [Segurança](docs/security-br.md) · [Maturidade](#maturidade-atual) · [Roadmap](docs/roadmap-br.md) · [Perguntas](docs/faq-br.md) · [Avalie em 10 minutos](docs/eval-br.md) · [Questione a arquitetura](https://github.com/cristhianbini/CBini-OrquestrAI/discussions/2)

**A camada de engenharia em volta da IA: os agentes propõem, as pessoas decidem, o sistema guarda a evidência.**

Um cockpit instalado na sua infraestrutura, onde agentes de IA especializados planejam e constroem software, todo comando que eles propõem espera
aprovação humana, roda isolada e pode ser rastreada, medida e desfeita.

---

## Por que o OrquestrAI

A IA já escreve boa parte do código de aplicações reais. Produção precisa de mais do que código: alguém tem de decidir o que pode rodar,
impedir que um projeto mexa em outro, provar o que mudou, desfazer erros e prestar contas do custo.

O OrquestrAI foi feito para essa parte. Ele não tenta deixar o modelo mais inteligente. Ele torna a engenharia com IA **governada,
observável, reversível e economicamente controlável** — na infraestrutura que você escolher.

**Agentes de IA são motores. O OrquestrAI é a camada de engenharia que decide como o trabalho deles vira realidade.** Ele não substitui os
melhores modelos ou agentes de código — organiza, governa, isola, mede e registra o trabalho deles, para que os modelos possam mudar sem que
a governança mude junto.

**O que ele não é:** um novo modelo de linguagem, um substituto dos modelos ou agentes de código que usa, um sandbox para código não
confiável de terceiros, uma plataforma de hospedagem multi-tenant, nem — hoje — um projeto open source.

## Construído da fronteira de execução para dentro

O OrquestrAI não começou pelas funcionalidades. Começou pela pergunta *o que acontece quando o que a IA produz toca um sistema real* — e
a respondeu primeiro: confirmação humana, execução isolada, mudanças medidas e reversíveis, registros à prova de adulteração, contabilidade
de custo, backup cifrado e procedimentos de recuperação, e comportamento fail-closed nos pontos críticos. Uma capacidade só recebe o selo *Disponível* depois que testes automáticos e um operador humano numa instalação real a provaram. As funcionalidades são construídas em cima dessa fundação, não ao lado dela.

## O princípio

> **A IA propõe. As pessoas decidem. O sistema guarda a evidência.**
>
> A IA cria o produto. O OrquestrAI fornece o trilho. Você decide o destino.

## O que o diferencia

| | |
|---|---|
| **Aprovação humana no ponto crítico** | Comandos propostos pela IA nunca rodam sozinhos: cada um vira um bloco de comando revisável, que só roda depois da confirmação de uma pessoa. Conteúdo gerado para o projeto (páginas, código da aplicação) é escrito por geradores validados, não pela execução de comandos escritos pela IA. |
| **Explicar antes de aprovar** | Qualquer mudança proposta pode ser explicada em linguagem simples — intenção, etapas, impacto, risco — sem rodar nada. |
| **Execução isolada** | O comando aprovado roda num ambiente descartável, sem rede e sem privilégios, que enxerga só o próprio projeto. |
| **Operações reversíveis** | O sistema registra o que a mudança pode tocar e mede o que ela de fato mudou; desfazer mostra antes o que será revertido. |
| **Evidência por padrão** | Execuções ficam num registro à prova de adulteração; sessões de terminal são seladas. Dá para ver quem propôs, quem aprovou e o que rodou. |
| **Chat, comando e terminal são coisas diferentes** | Conversa, mudança e inspeção são superfícies separadas, com permissões separadas. O terminal do projeto é somente leitura. |
| **Agentes especializados** | Um planejador monta, a cada tarefa, um time de agentes — estratégia, arquitetura, código, revisão, testes, documentação. |
| **Custo visível** | As chamadas a modelo são registradas por agente e superfície, e atribuídas ao projeto a que pertencem. Preço desconhecido continua desconhecido, não vira zero. |
| **Vários provedores** | Os agentes podem usar provedores diferentes; você usa as suas próprias contas e chaves. |
| **Conhecimento governado** | O sistema propõe lições a partir do próprio trabalho; elas só chegam aos agentes depois que uma pessoa aprova. |
| **Instalação própria** | Uma instalação dedicada por organização, em infraestrutura que ela controla. |

## Como funciona

Intenção humana → agentes especializados planejam e constroem → proposta (bloco de comando) → revisão (explicar, vetar com motivo ou
aprovar) → execução isolada → evidência (resultado, preview, custo) → manter ou reverter → lições propostas e aprovadas.
O diagrama está na [versão em inglês](README.md#how-it-works).

## A Fábrica do OrquestrAI

Descreva o projeto em poucas frases; a fábrica planeja, constrói e abre um preview.

- **Sites estáticos — disponível de ponta a ponta:** briefing → plano dos agentes → site gerado → checagens automáticas → preview em origem separada.
- **Aplicações full stack — em validação:** um único caminho totalmente suportado — **React + Vite + TypeScript, Express e SQLite** num só
  processo. A IA escreve a *especificação* da aplicação; o OrquestrAI gera a aplicação a partir de um modelo testado, e a infraestrutura
  sai sempre igual. A geração está provada; rodar cada aplicação no seu próprio ambiente isolado, com preview, é o trabalho em andamento.
  *Como a validação funciona aqui:* o gerador passou nos testes funcionais; depois, uma auditoria independente, somente leitura, encontrou
  casos de falha que o caminho feliz não exercita. Ele não foi promovido — será, depois que esses casos forem corrigidos e a auditoria aprovar.
- **Outras stacks — planejado,** sobre o mesmo padrão, depois que o primeiro caminho full stack estiver completo.

## Evidência de engenharia

Uma capacidade não conta porque o código existe. Conta quando o caminho foi provado:
**desenho → prova automática → prova humana num sistema real → revisão independente quando sensível → promoção.**
Passar no caminho feliz não basta: o primeiro gerador full stack passou nos testes funcionais, uma revisão independente achou casos de falha
e ele foi segurado. Detalhes: [visão técnica](docs/arch-br.md#evidência-de-engenharia).

## Segurança por desenho

Modelo completo — propriedades provadas, o que está em validação, pressupostos, limites e não objetivos: [docs/security-br.md](docs/security-br.md).
Em resumo — propriedades de desenho, não garantias: menor privilégio · execução explícita (nada roda sem confirmação; acesso administrativo separado,
com segundo fator) · isolamento (comandos aprovados e terminais do projeto em containers por projeto, sem rede; previews em origem separada; rede isolada por projeto para aplicações contínuas em validação) · reversibilidade onde suportado · trilha de auditoria à
prova de adulteração · revisão externa independente antes de promover mudanças de execução, isolamento e recuperação · disciplina de
recuperação (controle de versão, backup cifrado fora do servidor com verificação automática, snapshots).

## Provedores de IA

As rotas validadas usam hoje modelos Anthropic e OpenAI. Groq, Gemini, OpenRouter, Cerebras, Z.ai e qualquer API compatível com OpenAI
podem ser configurados e testados pelo painel. Instalação própria dá controle sobre infraestrutura, provedores e fluxo de dados; quando
um provedor de IA em nuvem é usado, o conteúdo enviado a ele segue os termos desse provedor.

## Maturidade atual

| Capacidade | Estado |
|---|---|
| Cockpit com chat, comandos, terminal e custo por projeto | Disponível |
| Blocos de comando com explicar, aprovar e vetar | Disponível |
| Execução isolada das mudanças aprovadas | Disponível |
| Reverter com prévia do desfazer | Disponível |
| Terminal do projeto somente leitura | Disponível |
| Dois fatores e confirmação reforçada | Disponível |
| Mesh de agentes com planejador | Disponível |
| Telemetria de custo por projeto, agente e chamada | Disponível |
| Lições governadas | Disponível |
| Fábrica: sites estáticos | Disponível |
| Backup cifrado fora do servidor com verificação | Disponível |
| Fábrica: aplicações full stack (React · Express · SQLite) | Em validação |
| Outros provedores de IA | Configurável |
| Recuperação completa num servidor novo | Planejado |
| Instalador guiado (um comando + assistente) | Planejado |
| Outras stacks e bancos | Planejado |

**Disponível** — provado por testes automáticos e por um operador humano numa instalação real. **Em validação** — construído e testado,
passando por prova e revisão independente antes da promoção; não liberado para operadores. **Configurável** — pode ser configurado e
testado, sem o nível de validação dos caminhos principais. **Planejado** — ainda não é funcionalidade.

## Para quem

Fábricas de software e agências · times internos de engenharia · times nativos em IA · organizações que precisam que o trabalho com IA
rode sob a própria governança.

## Por que importa para uma empresa

Aprovação humana exatamente onde a mudança fica real · saber quem propôs, quem aprovou e o que rodou em cada comando executado · desfazer mudanças suportadas em vez
de consertar à mão · ver o custo da IA por projeto e por agente, e distribuir o trabalho entre provedores · rodar na infraestrutura
escolhida, com as próprias contas · transformar um conjunto de ferramentas de IA num time com processo.

## Feedback

Preferimos saber onde o OrquestrAI está errado a colecionar estrelas.

- **Discorda de alguma premissa da arquitetura?** [Questione a arquitetura](https://github.com/cristhianbini/CBini-OrquestrAI/discussions/2).
- **Falta um caso de uso?** Abra uma ideia ou sugestão.
- **Algo confuso?** Envie feedback de UX ou um problema de documentação.
- **Achou uma falha de segurança?** Relate em privado — veja o [SECURITY.md](SECURITY.md).

Como participar: [CONTRIBUTING](CONTRIBUTING-BR.md) · [avalie a ideia em 10 minutos](docs/eval-br.md).

## Sobre

**CBini OrquestrAI** — concebido e dirigido por Cristhian Bini, CBini Soluções em TI.

Este repositório é a documentação pública e a vitrine do CBini OrquestrAI. O código-fonte do produto não está publicado aqui e este não
é um projeto open source. Licenciamento e termos comerciais em preparação. Todos os direitos reservados.

Mais: [visão técnica](docs/arch-br.md) · [modelo de segurança](docs/security-br.md) · [roadmap público](docs/roadmap-br.md) · [perguntas frequentes](docs/faq-br.md)

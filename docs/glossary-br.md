# Glossário — CBini OrquestrAI

🇧🇷 **Português** · 🇺🇸 [English](glossary.md) · 🇪🇸 [Español](glossary-es.md) · [README](../README-BR.md)

Definições em linguagem simples dos termos usados nesta documentação.

| Termo | O que significa |
|---|---|
| **Cockpit** | A interface web onde o operador trabalha: projetos, chat, propostas, custos, estado. |
| **Operador** | A pessoa que usa o OrquestrAI e toma as decisões. |
| **Projeto** | A unidade de trabalho e de isolamento. Tem arquivos, conversa, memória, execuções, previews e custos próprios. Outros projetos não o enxergam. |
| **Chat** | Onde você conversa com a IA sobre o projeto ativo. O chat lê e propõe; nunca executa. |
| **Modelo / provedor** | O modelo de IA que responde (e a empresa que o opera). Dá para trocar de modelo; o contexto continua com o projeto. |
| **Agentes** | Papéis especializados de IA — estratégia, arquitetura, código, revisão, testes, documentação — cada um ligado a um modelo. |
| **Malha de agentes / planejador** | O time de agentes de uma tarefa. O planejador decide quais agentes a tarefa precisa; os outros são dispensados e não custam nada. |
| **BLOCO** (bloco de comando) | Uma mudança proposta, mostrada primeiro como resumo humano (objetivo, dados, arquivos, efeito) e depois como código completo. Nada nele roda antes da aprovação. |
| **LAVE** | A rotina de revisão de todo BLOCO: **L**er, **A**valiar, **V**erificar, **E**xecutar. |
| **Explicar** | Pede uma explicação em linguagem simples de um BLOCO, sem executar nada. |
| **Vetar** | Rejeita uma versão de um BLOCO em definitivo; o motivo alimenta o próximo plano. |
| **Execução** | Rodar um BLOCO aprovado, num ambiente isolado que só enxerga aquele projeto. |
| **Revert** | Desfazer uma mudança suportada, depois de mostrar o que será desfeito. O próprio revert fica registrado e pode ser refeito. |
| **Fábrica** | Transforma um briefing curto em projeto: Planejar → Construir → Revisar → Gerar → Publicar, com o progresso visível ao operador. |
| **Site estático** | Projeto em HTML, CSS e JavaScript, gerado pela Fábrica e alterado por BLOCOs. |
| **Aplicação full stack** | App web com interface, API e banco SQLite, gerado a partir de um modelo testado, rodando sem acesso à rede e evoluindo por mudanças aditivas. |
| **Preview** | Onde um site ou aplicação gerado abre, numa origem separada do cockpit. |
| **Publicação** | Colocar no ar uma versão nova de uma aplicação full stack; automática depois de uma mudança aprovada, mantendo a versão anterior se a nova falhar. |
| **Quarentena** | Para onde vai um projeto excluído: sai de uso e da lista, mas não é destruído. |
| **Lições** | Conhecimento que o sistema propõe a partir do próprio trabalho; só chega aos agentes depois que uma pessoa aprova. |
| **Plano de controle / plano de execução** | Onde pessoas e agentes decidem (controle) versus onde as mudanças de fato acontecem (execução). |
| **Revisão independente** | Auditoria técnica somente leitura de mudanças sensíveis, feita por um revisor que não as escreveu. Um achado bloqueante para a promoção. |
| **Gate humano** | Ponto de decisão que só uma pessoa pode liberar, como aprovar uma execução ou promover uma capacidade. |
| **Disponível / Configurável / Planejado** | Selos de maturidade. *Disponível* significa provado por testes automáticos e por uma pessoa numa instalação real. |
| **Self-hosted** | Instalado em infraestrutura que a organização controla. O conteúdo enviado a provedores de IA externos continua sujeito aos termos deles. |

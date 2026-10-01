# Decisões de projeto — CBini OrquestrAI

🇧🇷 **Português** · 🇺🇸 [English](design.md) · [README](../README-BR.md) · [Arquitetura](arch-br.md) · [Segurança](security-br.md)

Por que o produto tem esta forma. Cada decisão declara o custo que aceita.

| Decisão | Por quê | Custo aceito |
|---|---|---|
| **O chat nunca executa** | Conversa é onde mora a incerteza; execução precisa de um artefato estável e revisável. | Um passo a mais entre pedir e mudar. |
| **Chat, bloco de comando e terminal são superfícies separadas** | Conversar, mudar e inspecionar têm riscos diferentes, então têm permissões diferentes. O terminal do projeto é somente leitura. | O operador aprende três superfícies em vez de uma. |
| **Comandos exigem aprovação explícita** | Quem responde por uma mudança deve vê-la antes de rodar, em linguagem simples se preciso. | Mais lento que execução autônoma — de propósito, no ponto em que a mudança fica real. |
| **Versão vetada nunca roda** | Uma rejeição tem de ser definitiva, e o motivo deve melhorar o próximo plano. | Um comando corrigido precisa de nova versão. |
| **Na dúvida sobre o efeito, recusar** | Um palpite sobre o escopo é pior que uma recusa; o operador pode reescrever a mudança de forma explícita. | Alguns comandos válidos são recusados e precisam ser reescritos de forma mais literal. |
| **O projeto é a unidade de isolamento** | Conversa, comando, terminal, preview e custo compartilham uma fronteira; trocar de projeto troca tudo. | Trabalho entre projetos não é uma operação única, de propósito. |
| **Previews em origem separada** | Página gerada não pode enxergar a sessão do operador. | O preview não aproveita o login do cockpit. |
| **Custo desconhecido não é zero** | Preço ausente lido como zero esconde gasto; desconhecido continua visível como desconhecido. | Alguns totais ficam incompletos e dizem isso. |
| **Lições precisam de aprovação humana** | Conhecimento que chega a todos os agentes muda comportamento e recebe a mesma governança do código. | Aprender é mais lento que aprender sozinho. |
| **Código existente não é capacidade** | Uma capacidade só fica *Disponível* depois de prova automática e humana; mudanças sensíveis exigem também revisão independente. | Funcionalidades ficam mais tempo em validação. |
| **Uma stack completa de ponta a ponta antes de várias** | Um caminho provado ensina mais que vários parciais e vira modelo para o próximo. | Menos opções de stack por enquanto. |
| **Não competir com modelos** | Modelos e agentes de código evoluem rápido; a camada durável é governança, isolamento, evidência e custo em volta deles. | O OrquestrAI depende de modelos externos para a inteligência. |
| **Instalação própria, uma organização por instalação** | O cliente controla infraestrutura e escolha de provedores. | Sem oferta hospedada multi-tenant na versão atual. |

A tese das duas últimas linhas é uma aposta do produto, não uma vantagem de mercado comprovada. Discorda de alguma linha?
[Questione a arquitetura](https://github.com/cristhianbini/CBini-OrquestrAI/discussions/2).

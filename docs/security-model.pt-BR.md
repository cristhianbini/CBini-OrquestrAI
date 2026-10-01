# Modelo de segurança — CBini OrquestrAI

🇧🇷 **Português** · 🇺🇸 [English](security-model.md) · [README](../README.pt-BR.md) · [Visão técnica](technical-overview.pt-BR.md)

Esta página diz o que o OrquestrAI foi desenhado para proteger, o que está provado, o que ainda está em validação, o que ele pressupõe e o
que não pretende fazer. É um resumo público; detalhes operacionais foram omitidos de propósito. Relate vulnerabilidades em privado, nunca
em issues ou discussões públicas.

## Contra o que protege

- Saída de IA mudando um sistema sem que uma pessoa tenha decidido.
- Comandos, sessões ou dados de um projeto afetando outro projeto.
- Mudanças que não podem ser explicadas, atribuídas ou desfeitas.
- Perda silenciosa de estado operacional.

## Propriedades provadas

| Propriedade | O que significa |
|---|---|
| Execução explícita | Nenhum caminho executa saída de IA sem uma etapa de confirmação humana. O chat não executa. |
| Veto é definitivo | Uma versão vetada de um comando nunca pode ser executada. |
| Execução isolada | Comandos aprovados rodam num ambiente descartável, sem rede, sistema somente leitura, sem privilégios e só com o próprio projeto montado. |
| Na dúvida, recusa | Comandos cujo efeito não pode ser analisado com segurança são recusados antes de rodar. |
| Inspeção somente leitura | O terminal do projeto é somente leitura e sem rede, num container por conexão. |
| Confirmação reforçada | Login com dois fatores; sessões de terminal e administrativas exigem um segundo fator novo. |
| Evidência à prova de adulteração | Execuções num registro encadeado por hash; sessões de terminal seladas. |
| Mudanças reversíveis | Mudanças de arquivo suportadas são medidas e podem ser revertidas, com prévia do desfazer. |
| Segredos em repouso | Chaves de provedor cifradas no servidor e nunca devolvidas ao navegador. |
| Origens separadas | Previews de projeto servidos em origem diferente do cockpit. |
| Disciplina de recuperação | Backup cifrado diário fora do servidor, verificado automaticamente (completude e segredo em claro); restauração provada em isolamento. |

"Provado" significa coberto por testes automáticos e confirmado por um operador humano numa instalação real.

## Em validação

- **Aplicações contínuas por projeto** (caminho full stack da fábrica): isolamento de rede por projeto, releases imutáveis, limites de
  recursos e controle de ciclo de vida estão desenhados e revisados de forma independente; ainda não liberados para operadores.
- **Backup consistente dos bancos** das aplicações geradas.
- **Recuperação completa num servidor novo.**

## Pressupostos

- O servidor é operado por um administrador de confiança e mantido atualizado.
- Operadores protegem as próprias credenciais e dispositivos de segundo fator.
- Provedores de IA tratam o conteúdo recebido conforme os próprios termos.

## Limites e não objetivos

- **Fronteira de dados.** Instalação própria mantém o plano de controle, os projetos e os registros na sua infraestrutura. Quando um
  provedor de IA em nuvem é usado, o conteúdo necessário a cada chamada — instruções, contexto e trechos de código — é enviado a ele. O
  OrquestrAI não impede isso; ele permite escolher quais provedores configurar.
- **Alcance do reverter.** Cobre arquivos alterados por blocos de comando. Não desfaz dados gravados por uma aplicação em execução; esse é o
  papel do backup.
- **Não é sandbox para código arbitrário.** O isolamento foi feito para mudanças aprovadas pelo operador nos próprios projetos, não para
  rodar cargas de terceiros não confiáveis.
- **Nenhuma certificação de conformidade** é declarada.
- **Instalação de uma organização.** Hospedagem multi-tenant não é objetivo da versão atual.

## Revisão independente

Mudanças que tocam execução, isolamento ou recuperação passam por um auditor independente, somente leitura, antes da promoção. Um achado que
bloqueia a promoção a interrompe, independentemente dos testes funcionais.

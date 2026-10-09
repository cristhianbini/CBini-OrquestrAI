# Perguntas frequentes — CBini OrquestrAI

🇧🇷 **Português** · 🇺🇸 [English](faq.md) · 🇪🇸 [Español](faq-es.md)

**O OrquestrAI é uma IA?**
Não. É uma camada de engenharia que coordena modelos e provedores de IA, agentes especializados, contexto por projeto, execução
supervisionada, auditoria e reversibilidade, com uma pessoa decidindo onde uma mudança vira real.

**Ele substitui o desenvolvedor?**
Não. Ele organiza o trabalho da IA para que um time o use com governança: alguém define a intenção, revisa e aprova.

**O contexto fica preso a um modelo? Os projetos compartilham memória?**
O contexto pertence ao projeto: o operador pode trocar de modelo e o seguinte recebe o mesmo contexto. Outro projeto parte do próprio
contexto e não herda o do primeiro.

**O OrquestrAI é open source?**
Não. Este repositório é a vitrine e a documentação pública. O código-fonte do produto é privado; este projeto não é distribuído como software open source, e o modelo de licenciamento está em definição.

**Este repositório é o código-fonte?**
Não. Ele contém só documentação pública. O produto é desenvolvido num repositório privado.

**O que está disponível hoje e o que está em validação?**
Veja a tabela de maturidade no [README](../README-BR.md#maturidade-atual). *Disponível* significa provado por testes automáticos e por
um operador humano numa instalação real; *em validação* significa construído e testado, mas ainda não promovido.

**A IA executa mudanças sozinha?**
Não. O chat nunca executa. Toda mudança concreta vira um bloco de comando que só roda depois que uma pessoa revisa e confirma.

**O que "reversível" quer dizer aqui?**
Nas mudanças suportadas, o sistema registra o que a mudança pode tocar e mede o que ela de fato mudou; desfazer mostra antes o que será
revertido. Dados gravados por uma aplicação em execução ficam fora desse mecanismo, por desenho; eles são protegidos pelo backup diário. Desfazer
uma mudança numa aplicação full stack restaura o código e republica a versão anterior; colunas já criadas no banco são mantidas, então
nenhum dado se perde.

**Meus dados ficam no meu servidor?**
O OrquestrAI roda em infraestrutura que você controla. Quando provedores de IA externos são usados, o conteúdo enviado a eles segue os
serviços e as políticas de cada provedor. Você escolhe quais provedores configurar.

**Quais provedores de IA são suportados?**
As rotas validadas dos agentes usam hoje modelos Anthropic e OpenAI. Groq, Gemini, OpenRouter, Cerebras, Z.ai e APIs compatíveis com
OpenAI podem ser configurados e testados pelo painel, fora das rotas validadas.

**Ele constrói aplicações completas?**
Sim, dentro de um caminho suportado. Sites estáticos e o primeiro caminho full stack (React + Vite + TypeScript, Express, SQLite) funcionam
de ponta a ponta hoje; a aplicação gerada tem um modelo de dados e evolui por mudanças aditivas que você aprova.

**Posso instalar eu mesmo?**
Hoje a instalação segue um procedimento manual documentado. Um instalador guiado está planejado.

**Como dou feedback?**
Pelas Discussions e Issues deste repositório. Não relate questões de segurança publicamente.

[← Voltar ao README](../README-BR.md)

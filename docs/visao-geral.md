# Visão geral do projeto

## O que é

Este projeto descreve um chat de equipe para navegador desktop, pensado para pequenas e médias
empresas que vendem para outras empresas. Além de canais e conversas diretas, o produto incorpora
agentes de IA que as pessoas acionam dentro das próprias conversas.

O objetivo é reduzir o tempo gasto procurando contexto, evitar que pedidos feitos no chat se
percam e facilitar o acesso a informações de negócio sem exigir que cada pessoa saiba consultar
um banco de dados.

## O que o produto oferece

- Conversas em canais públicos e privados e mensagens diretas entre duas pessoas.
- Mensagens em tempo real, menções e notificações.
- Resumos de conversas com recortes por período, pessoa ou assunto.
- Delegação de tarefas a partir da conversa, com responsável e notificações de acompanhamento.
- Consultas em linguagem natural a dados de vendas e geração de relatórios em PDF.
- Agentes conectáveis ao workspace como módulos do produto.

## Como a IA participa

As pessoas pedem ajuda mencionando um agente na conversa. O agente pode resumir mensagens,
delegar uma tarefa ou responder a uma pergunta sobre dados de negócio. O chat continua útil mesmo
quando o serviço de IA está indisponível: nesse caso, o pedido falha de forma explícita, sem
inventar uma resposta.

As consultas a dados de negócio são somente leitura e dependem da permissão de quem fez o pedido.
Os números apresentados precisam ter lastro em resultados de consulta. Relatórios demorados são
processados em segundo plano para que a conversa continue disponível.

## Público e limites do MVP

O foco inicial são equipes que já trabalham em um chat e precisam recuperar contexto ou obter
números de vendas com mais autonomia. O MVP é para desktop e não inclui, entre outros itens,
aplicativos móveis, chamadas de voz ou vídeo, login corporativo (SSO), múltiplas empresas na mesma
instalação ou agentes que alterem dados de negócio.

## Como ler a documentação

- [Product brief](./product-brief.md): explica o problema, o público, os objetivos e o escopo do
  produto — o que será feito e para quem.
- [HLD](./hld.md): apresenta o desenho de alto nível, os componentes, integrações, fluxos e
  decisões de arquitetura.
- [LLD](./lld.md): detalha a implementação, incluindo estrutura do código, dados, interfaces e
  regras.
- [ADRs](./adr/): registram decisões de arquitetura e suas justificativas.

Esses documentos estão em rascunho e algumas decisões e questões permanecem em aberto. O nome
varia entre os documentos atuais: “Developer Chat” no product brief e “Full Cycle Chat” no HLD e
no LLD; a nomenclatura final ainda precisa ser alinhada.

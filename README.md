# Developer Chat

Chat de equipe para navegador desktop, voltado a pequenas e médias empresas que vendem para outras
empresas. Agentes de IA podem ser acionados dentro das conversas para resumir discussões, delegar
tarefas e responder perguntas sobre dados de vendas.

## Problema que o produto resolve

Em equipes que trabalham pelo chat, decisões e contexto se perdem no volume de mensagens, pedidos
ficam sem responsável e perguntas sobre os números do negócio dependem de alguém com acesso ao
banco ou ao BI. O produto reúne a conversa e a ajuda dos agentes no mesmo lugar, para reduzir esse
retrabalho sem exigir que cada pessoa saiba consultar dados diretamente.

## Funcionalidades do MVP

- Canais públicos e privados, conversas diretas e mensagens em tempo real.
- Menções, notificações, edição e exclusão das próprias mensagens e recuperação após desconexão.
- Resumos de conversas por período, pessoa ou assunto.
- Delegação de tarefas pelo agente, com responsável, notificações e acompanhamento de conclusão.
- Consultas em linguagem natural a dados de vendas e relatórios em PDF.
- Agentes conectáveis ao workspace como módulos do produto.

## Princípios para o uso de IA e dados

- Os pedidos e as respostas dos agentes acontecem dentro da conversa.
- Consultas a dados de negócio são somente leitura e respeitam a permissão de quem fez o pedido.
- Números apresentados precisam ter lastro em resultados de consulta; se não houver resposta
  confiável, o agente informa a falha em vez de inventar.
- Pedidos demorados, como a geração de um PDF, são processados sem bloquear o chat.
- A indisponibilidade do provedor de IA não deve interromper as conversas comuns.

## Arquitetura proposta

O HLD descreve uma aplicação web com Frontend/BFF em Next.js, API de chat em NestJS e serviço de
agentes em Python com Google ADK. Um Worker separado processa pedidos demorados. Postgres armazena
os dados, Redis apoia filas e eventos de tempo real, e um armazenamento compatível com S3 guarda
relatórios. As aplicações são propostas para implantação em uma plataforma gerenciada (PaaS).

Essa arquitetura é uma proposta documentada, não uma afirmação de que todos esses componentes já
estejam implantados.

## Público e limites

O foco inicial são equipes que já usam chat e precisam recuperar contexto ou obter números de
vendas com mais autonomia. O MVP é para desktop. Ficam fora do escopo inicial aplicativos móveis,
voz e vídeo, login corporativo (SSO), múltiplas empresas na mesma instalação e agentes que alterem
dados de negócio.

## Documentação

- [Product brief](docs/product-brief.md): problema, público, objetivos e escopo do produto.
- [HLD](docs/hld.md): arquitetura de alto nível, componentes, integrações, fluxos e decisões.
- [LLD](docs/lld.md): estrutura de implementação, dados, interfaces e regras detalhadas.

Os documentos ainda estão em rascunho. O product brief usa “Developer Chat”, enquanto o HLD e o
LLD usam “Developer Chat Chat”; o nome final precisa ser alinhado. Prazo de lançamento,
dimensionamento, equipe e orçamento também permanecem em aberto.

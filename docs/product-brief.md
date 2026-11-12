# Product Brief: Developer Chat

2026-11-03 · Eduardo Developer · Status: rascunho

## Visão geral

Developer Chat é um chat de equipe no estilo Slack, com canais, conversas 1:1, menções, tarefas
e notificações em tempo real, em que agentes de IA entram como plugins. Os agentes resumem
conversas, delegam tarefas para outras pessoas e consolidam informações do negócio em linguagem
natural, gerando relatórios e contagens a partir do banco de dados da empresa. Hoje as três
capacidades estão em um agente só, o `@assistente`, mas o produto pode ter um ou mais agentes,
conforme fizer sentido.

O produto se apoia em cinco promessas:

- A IA fica dentro da conversa: basta mencionar o agente em qualquer canal ou conversa direta, e
  o pedido e a resposta ficam públicos ali mesmo, sem trocar de ferramenta.
- O agente executa ações: a delegação vira uma tarefa de verdade, com responsável e notificação,
  e o relatório de dados chega como arquivo para baixar.
- Dados de negócio com permissão: o agente só consulta dados quando quem pediu tem acesso. Quem
  não tem vê a resposta bloqueada, e o agente nunca altera os dados da empresa.
- O agente não inventa: todo número precisa estar no resultado de uma consulta. Quando não
  consegue responder, ele diz que não conseguiu, e sem acesso ao modelo de IA o pedido falha em
  vez de receber uma resposta simulada.
- Agentes são plugins: um administrador conecta e desconecta cada agente do workspace.

## Problema e contexto

Em times que trabalham pelo chat, o contexto se perde no volume de mensagens: quem volta de uma
reunião ou chega depois precisa rolar o histórico inteiro. Pedidos feitos na conversa ("alguém
atualiza a planilha?") ficam sem dono e são esquecidos. Perguntas sobre os números do negócio
("quanto faturamos em março?") dependem de alguém com acesso ao banco ou ao BI. Hoje as pessoas
contornam isso rolando a conversa, copiando trechos para um assistente de IA externo (o que expõe
dados da empresa), criando a tarefa à mão em outra ferramenta ou pedindo o número ao time de
dados e esperando.

Por que agora: os modelos de linguagem passaram a usar ferramentas de forma confiável, e o MCP
padronizou como ligar um agente a um banco de dados. Isso torna viável um agente dentro do chat
que consulta dados reais com permissão e somente leitura, sem integração sob medida.

Hipóteses em que a aposta se apoia, ainda não validadas:

- As pessoas preferem pedir ao agente dentro da conversa a abrir outra ferramenta.
- Um resumo com recorte ("só de hoje", "da semana") poupa tempo de quem volta à conversa.
- Delegar pelo chat, com a tarefa registrada e notificada, reduz pedidos esquecidos.
- Empresas aceitam que uma IA consulte dados de negócio quando há permissão por pessoa e somente
  leitura.
- Um número errado destrói a confiança no agente: é melhor dizer "não consegui" do que chutar.

## Público-alvo

- **Perfil principal:** empresas pequenas e médias que vendem para outras empresas, cujo time de
  produto e tecnologia já conversa em um chat de equipe e cujos dados de vendas estão em um banco
  de dados. Quem mais ganha é quem precisa de números sem saber SQL (PM, liderança) e quem perde
  contexto no volume de mensagens.
- **Gatilho de uso ou de compra:** a mesma pergunta de números volta toda semana e trava no time
  de dados, ou uma tarefa pedida no chat se perde e alguém cobra depois.
- **Fora do foco inicial:** grandes empresas que exigem login corporativo, auditoria formal e
  retenção de dados; comunidades abertas e uso pessoal; empresas cujos dados de vendas não estão
  em um banco de dados próprio (planilhas, ERPs fechados); quem precisa de chamadas de voz ou
  vídeo, ou de usar o chat pelo celular.

## Objetivos e métricas de sucesso

| Métrica | O que mede | Meta em prazo a definir |
| --- | --- | --- |
| Uso do agente | % das pessoas ativas na semana que fizeram ao menos um pedido a um agente | A definir |
| Tarefas delegadas concluídas | % das tarefas criadas pelo agente que foram concluídas | A definir |
| Qualidade do agente | % de aprovação na avaliação completa do agente | ≥ 98% |
| Número errado entregue | Respostas ou relatórios com número sem lastro que chegaram à pessoa | 0 |
| Tempo de resposta | p95 de um pedido comum a um agente | ≤ 5 s |
| Custo por pedido | Gasto com o modelo de IA por pedido a um agente | ≤ US$ 0,01 |

## Escopo do MVP

Plataforma: web, no navegador de desktop.

1. Entrar com e-mail e senha, em uma conta criada pela empresa; a sessão vale para o navegador
   todo.
2. Conversar nos canais públicos (que incluem todo o workspace), em canais privados e em conversas
   diretas (1:1); criar canais públicos ou privados e convidar pessoas para um canal privado.
   Só quem foi convidado vê e participa do canal privado.
3. Buscar pessoas por nome ou @usuário para abrir uma conversa direta e ver o perfil de qualquer
   pessoa.
4. Ver as mensagens chegarem em tempo real, com aviso de "digitando", histórico paginado e
   contagem de não lidas e de menções.
5. Mencionar pessoas, responder citando uma mensagem, copiar texto, editar e apagar as próprias
   mensagens, com a mudança aparecendo para todos na hora.
6. Receber notificações de menção, mensagem direta e tarefa, com alerta na tela e, se a pessoa
   ligar, notificação do navegador; clicar leva direto à mensagem. A tela Atividade reúne
   Menções, DMs e Tarefas.
7. Editar o próprio perfil (nome, cargo, telefone, status, presença) e escolher o tema claro ou
   escuro.
8. Como administrador, conectar e desconectar agentes do workspace; quem não administra vê os
   agentes e a quem pedir.
9. Pedir a um agente um resumo da conversa com recorte (hoje, desde ontem, a semana, tudo, o
   que uma pessoa disse, um assunto). Sem recorte, o agente pergunta e oferece botões com a
   quantidade de mensagens de cada opção.
10. Pedir a um agente para delegar uma tarefa a outra pessoa mencionada. A tarefa notifica
    quem recebe, aparece em Atividade → Tarefas e pode ser concluída ou reaberta, e quem delegou
    é avisado quando isso acontece.
11. Consolidar informações do negócio em linguagem natural: contar, somar e comparar dados de
    vendas (faturamento por mês, pedidos por vendedor, clientes ativos). O resultado chega como
    resposta em texto na conversa e, quando a pessoa pedir, como relatório em PDF para baixar. Só
    quem tem permissão de dados recebe o conteúdo, inclusive o arquivo; a resposta fica na
    conversa, bloqueada para quem não tem acesso.
12. Responder a uma pergunta de um agente sem mencioná-lo de novo, ou com um clique em uma das
    respostas prontas que ele oferece.
13. Pedir algo demorado, como um relatório em PDF, e seguir conversando: o agente avisa que
    começou e entrega o resultado na conversa quando termina.

## Fora de escopo

- Gráfico na conversa e relatório agendado. Candidatos ao roadmap: a definir.
- Agente que age sem ser chamado (lembrete de tarefa parada, resumo automático do dia). Candidato
  ao roadmap: a definir.
- Cadastro, convite de pessoas e tela de papéis e permissões: hoje as contas e as permissões são
  criadas por script, fora do produto. Candidato à Fase 2.
- Remover membros de canal privado, entrar e sair de canais. Candidato à Fase 2.
- Busca de mensagens; o resumo por pessoa ou assunto cobre parte da necessidade. Candidato à
  Fase 2.
- Threads, reações e anexos de arquivo: não testam a aposta, que é o agente dentro da conversa.
  Candidatos à Fase 2.
- Criar tarefa à mão, prazo de tarefa e tarefa com vários responsáveis: no MVP a tarefa existe
  para testar a delegação pelo agente.
- Agente que altera dados do negócio: decisão de segurança, a consulta é só leitura.
- Outras fontes de dados além do banco da empresa (planilhas, ERP, outras APIs).
- Vários workspaces ou várias empresas na mesma instalação.
- Login corporativo (SSO) e chamadas de voz e vídeo: fora do público inicial.
- Celular e tablet, no navegador ou em app nativo: o produto é só para desktop.

## Requisitos não funcionais e restrições

| Área | Requisito |
| --- | --- |
| Dados de negócio | Os agentes só leem dados do negócio e não leem mensagens nem usuários do chat. |
| Restrição | A garantia de somente leitura vem do próprio banco, e não do código (imposta). |
| Permissão | Só consulta dados quem tem permissão, e a resposta e o relatório só chegam a quem também tem. Só administradores conectam e desconectam agentes. |
| Isolamento | O conteúdo da conversa não pode influenciar a consulta ao banco. |
| Confiabilidade | Nenhum número sem lastro no resultado de uma consulta, na resposta ou no relatório. Na dúvida, o agente pergunta, recusa ou diz que não conseguiu, nunca inventa. Sem acesso ao modelo, o pedido falha com erro em vez de receber uma resposta simulada. |
| Auditoria | Toda consulta ao banco fica registrada (quem pediu, conversa, pergunta, consulta, desfecho), sem o conteúdo do resultado. Os registros não guardam conteúdo de mensagens. |
| Sessão | Nenhuma credencial acessível ao navegador; a sessão é revogável e vale para o navegador todo. |
| Custo | Teto de custo por pedido a um agente (chamadas ao modelo e tokens) e no máximo 10 pedidos por minuto por pessoa. |
| Desempenho | Pedido comum a um agente com p95 ≤ 5 s; pedido demorado vai para segundo plano. Mensagens em tempo real, sem atraso perceptível, e recuperação do que se perdeu numa queda de conexão. |
| Modelo de IA | Trocável por configuração (OpenAI, Gemini, Anthropic), sem mudar código. |
| Idioma e fuso | Interface e respostas em português do Brasil; o "hoje" de um resumo segue o fuso de quem pediu. |
| Acessibilidade | Tudo funciona por teclado. |
| Hospedagem | A pilha inteira roda em um único servidor de 2 GB de RAM, com HTTPS e implantação automática que volta à versão anterior se algo falhar. |
| Prazo | Sem prazo de lançamento definido. |

## Alternativas e concorrentes

| Alternativa | Pontos fortes | Pontos fracos para o público-alvo | Nosso posicionamento |
| --- | --- | --- | --- |
| Slack com a IA dele (resumos, busca com IA, agentes) | Chat líder de mercado; resume canais e threads | Responder sobre dados próprios da empresa exige integrações e planos mais caros | Consulta ao banco da empresa já pronta, com permissão por pessoa e somente leitura |
| Microsoft Teams com Copilot | Vem com o pacote de escritório; resume conversas e reuniões | Integração com banco de dados próprio depende de conectores ou do BI da própria plataforma | Consulta a dados já pronta e independência de pacote: o modelo de IA é trocável |

## Riscos, dependências e premissas

O maior risco é o agente entregar um número errado com confiança, ou entregar dados a quem não
tem permissão: qualquer um dos dois destrói a confiança no produto.

| Risco | Mitigação |
| --- | --- |
| Produto: número errado em uma resposta ou relatório | Todo número precisa de lastro no resultado da consulta; na dúvida o agente recusa ou pergunta; avaliação com 73 casos para comparar versões |
| Segurança: dados de negócio chegarem a quem não tem permissão, inclusive pelo PDF | Permissão por pessoa; conteúdo bloqueado para quem não tem acesso, inclusive no PDF; agente só leitura; auditoria de cada consulta |
| Segurança: alguém escrever na conversa instruções que manipulam o agente | Conteúdo da conversa tratado como dado não confiável e sem influência na consulta ao banco; só consultas de leitura passam |
| Técnico: o custo com o modelo de IA sair do controle | Teto de chamadas e tokens por pedido; no máximo 10 pedidos por minuto por pessoa |
| Técnico: o provedor do modelo cair, encarecer ou mudar de comportamento | Modelo trocável por configuração; a avaliação compara modelos antes da troca |

**Premissas:** as cinco hipóteses de "Problema e contexto", ainda não validadas.

## Roadmap

As funcionalidades de cada fase, a ordem entre elas e o status estão no
[roadmap](roadmap.md).

- **Fase 1, fechar o MVP.** Objetivo: completar a aposta.
- **Fase 2, operar como produto.** Objetivo: uma empresa conseguir usar sem depender de script para criar contas e permissões.
  Entram cadastro e convite de pessoas, tela de papéis e permissões, remoção de membros de canal
  privado, entrar e sair de canais, busca de mensagens, threads, reações e anexos. Começa
  quando a Fase 1 atingir as metas de qualidade: ≥ 98% na avaliação, 0 número errado entregue,
  p95 ≤ 5 s e ≤ US$ 0,01 por pedido.
- **Sem fase:** gráfico na conversa, relatório agendado e agente que age sem ser chamado, a
  definir.

## Questões em aberto

- [ ] Definir a meta de uso do agente (% das pessoas ativas na semana com ao menos um pedido).
- [ ] Definir a meta de tarefas delegadas concluídas.
- [ ] Definir o prazo das metas: em quanto tempo após o lançamento são medidas e o que conta como
      lançamento.
- [ ] Decidir se gráfico na conversa e relatório agendado entram no roadmap ou ficam fora.
- [ ] Decidir se o agente que age sem ser chamado (lembretes de tarefa, resumo automático) entra
      no roadmap ou fica fora.

## Glossário

O vocabulário do produto está no [GLOSSARY.md](../GLOSSARY.md), na raiz do repositório.
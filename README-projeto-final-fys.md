# Copiloto de Vendas com IA para Atendimento ao Cliente: Copiloto de Escrita FYS

Projeto final do **Bootcamp Heineken - Inteligência Artificial Aplicada a Vendas (DIO)**, construído a partir do desafio "O tom FYS sem virar tiozão do pavê", inspirado no repositório [digitalinnovationone/copiloto-vendas-ia-atendimento-cliente-fys](https://github.com/digitalinnovationone/copiloto-vendas-ia-atendimento-cliente-fys) e na live "FYS: Por Dentro da Marca, Desafios e Ideias para o Projeto Final".

## Tema escolhido

**Assistente de Escrita no Tom FYS**: um revisor de IA que transforma mensagens comerciais formais e genéricas em mensagens no tom autêntico da marca FYS (refrigerante do grupo Heineken) - humor inteligente, irônico, autoirônico e pé no chão, sem virar "tiozão do pavê".

## Quem é o usuário principal

O time de trade/vendas da FYS que se comunica com **donos de padaria** - o canal onde a marca tem menos de 1% de participação de mercado e nenhuma força de vendas dedicada. Também serve qualquer pessoa do time de marketing/trade que precise revisar rapidamente uma mensagem antes de enviar a um ponto de venda.

## Qual problema ele resolve

Segundo a live da FYS, o canal padarias representa uma oportunidade enorme (72 mil padarias no Brasil, 15 mil só em São Paulo) mas a FYS detém apenas 0,9% desse mercado. O motivo principal não é o produto, é a falta de relacionamento: a força de vendas da Heineken prioriza pontos de venda de alto volume de cerveja, então as padarias ficam sem uma abordagem comercial recorrente. Quando alguém do time escreve para esses pontos de venda, o texto tende a sair genérico e institucional - exatamente o oposto do tom que fez a marca crescer (humor, autoironia, "não somos número 1 e tá tudo bem").

O Copiloto de Escrita FYS resolve esse gap: pega qualquer mensagem comercial formal (oferta, follow-up, reposição, apresentação da marca) e devolve a mesma informação, no tom da marca, sem precisar de um redator dedicado para cada mensagem.

## Qual abordagem foi usada

Um prompt mestre (`agents.md`) define o papel do Copiloto, as regras de processamento e os filtros de restrição. O agente usa três arquivos de contexto na pasta `knowledge/` (transcrição da live, guia de tom de voz e dados do mercado de padarias) como base de conhecimento. Para cada mensagem recebida, a resposta segue um formato fixo de 3 partes: mensagem original (resumo), versão no tom FYS, e o que foi ajustado (cortado, mantido, adicionado).

Essa abordagem nasceu do desafio "Quem Não Vende, Ajuda a Vender", cujo prompt final passo a passo está em [`prompt-final-fys.md`](prompt-final-fys.md) - este projeto final é a evolução desse prompt para um agente completo com base de conhecimento.

## Base de conhecimento utilizada

- [`agents.md`](agents.md) - prompt mestre do Copiloto de Escrita FYS (role, regras de processamento, filtros de restrição, formato de saída).
- [`knowledge/transcricao-live-fys.txt`](knowledge/transcricao-live-fys.txt) - transcrição da live "FYS: Por Dentro da Marca, Desafios e Ideias para o Projeto Final", com histórico da marca, portfólio, exemplos de campanha e o desafio do canal padarias.
- [`knowledge/tom-fys.md`](knowledge/tom-fys.md) - guia de tom de voz e posicionamento: o que fazer (humor autoirônico, "não somos número 1") e o que evitar (jargões clichê, palavrões, "tiozão do pavê").
- [`knowledge/contexto-comercial.md`](knowledge/contexto-comercial.md) - dados do mercado de padarias (72 mil no Brasil, 0,9% de participação da FYS, barreiras de conversão) que justificam a oportunidade para IA nesse canal.

## Exemplo de conversa/resposta/análise

Disponível em [`exemplos/exemplo-revisao.md`](exemplos/exemplo-revisao.md), com dois casos completos:

1. Uma mensagem de **oferta** ("Prezado(a) parceiro(a), temos o prazer de apresentar...") reescrita para um tom direto, com autoironia sobre a FYS não ser a marca número 1 e menção ao Guaraná da Amazônia (sabor mais vendido).
2. Uma mensagem de **follow-up** institucional ("Permanecemos à disposição para esclarecer quaisquer dúvidas...") reescrita reconhecendo a rotina da padaria, sem urgência artificial.

Cada exemplo traz a mensagem original, a versão reescrita e a análise do que foi removido, mantido e adicionado - seguindo exatamente o formato de saída definido em `agents.md`.

## Como reproduzir

1. Copie o conteúdo de [`agents.md`](agents.md) como prompt de sistema/instrução do seu agente de IA preferido (Claude, ChatGPT, etc.).
2. Carregue os três arquivos da pasta `knowledge/` como contexto/base de conhecimento do agente.
3. Envie uma mensagem comercial formal (oferta, follow-up, apresentação de produto) destinada a um dono de padaria.
4. O agente responde no formato de 3 partes: mensagem original, versão no tom FYS, e o que foi ajustado - como nos exemplos em [`exemplos/exemplo-revisao.md`](exemplos/exemplo-revisao.md).

## Possíveis melhorias futuras

- Conectar o agente a um histórico real de mensagens trocadas com padarias, para aprender com exemplos reais de respostas que funcionaram.
- Criar variações de tom por canal (WhatsApp, e-mail, tablóide impresso), já que cada formato tem restrições e expectativas diferentes.
- Incorporar dados públicos por região (ex: penetração por estado - Bahia, Rio Grande do Sul, Paraná, Minas Gerais) para personalizar mensagens conforme a praça do ponto de venda.
- Evoluir de um revisor reativo para um copiloto ativo, que sugere proativamente quando e o que enviar para cada padaria com base em gatilhos comerciais (reposição, sazonalidade, lançamento de sabor).

---

## Outros desafios deste bootcamp neste repositório

- [`prompt-final-fys.md`](prompt-final-fys.md) - Desafio "Quem Não Vende, Ajuda a Vender! O Poder da Argumentação", prompt passo a passo que deu origem ao Copiloto de Escrita FYS.

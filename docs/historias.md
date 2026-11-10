# Histórias de usuário — NewsFlow

Autores: Luciano Eude e Gustavo Mariano

## US01 — Salvar rascunho automaticamente
**Como** redatora
**Quero** que meu texto seja salvo enquanto escrevo
**Para** não perder trabalho quando a conexão cair

**Critérios de aceitação**
- O rascunho é salvo após 30 segundos sem digitar.
- Cada salvamento cria uma versão numerada.
- Só as últimas 20 versões ficam disponíveis para restauração.
- Restaurar uma versão não apaga as seguintes.

**Regras cobertas:** RN01
**Prioridade:** Alta — perda de conteúdo é a reclamação número um dos redatores.
**Cenários:** features/us01-rascunho.feature

## US02 — Aprovar edição
**Como** revisor
**Quero** aprovar ou reprovar uma edição escrita por outra pessoa
**Para** que nada seja enviado aos assinantes sem uma segunda leitura

**Critérios de aceitação**
- O revisor aprova uma edição que está em revisão.
- O autor não aprova a própria edição.
- A reprovação devolve a edição ao rascunho.
- A reprovação exige um comentário.

**Regras cobertas:** RN02
**Prioridade:** Alta — sem aprovação, o envio (US03) não pode acontecer e erros chegariam a 40 mil pessoas.
**Cenários:** features/us02-aprovacao.feature

## US03 — Agendar envio
**Como** gestora de comunicação
**Quero** agendar o envio de uma edição aprovada
**Para** que ela chegue no melhor horário sem eu precisar apertar o botão

**Critérios de aceitação**
- Só edição aprovada pode ser agendada.
- O envio exige no mínimo 15 minutos de antecedência (fuso America/Sao_Paulo).
- O envio pode ser reagendado no máximo 2 vezes.
- O envio pode ser cancelado até 5 minutos antes do horário marcado.

**Regras cobertas:** RN03 (e a exigência de aprovação de RN02)
**Prioridade:** Alta — é a entrega de valor central do produto e concentra as regras numéricas.
**Cenários:** features/us03-agendamento.feature

## US04 — Descadastrar-se e voltar à lista
**Como** assinante
**Quero** sair da lista a qualquer momento e só voltar se eu confirmar
**Para** controlar o que chega na minha caixa de entrada

**Critérios de aceitação**
- Todo e-mail de newsletter traz o link de descadastro.
- O descadastro tem efeito imediato e gera e-mail de confirmação.
- Voltar para a lista exige confirmação por e-mail (duplo opt-in).
- O link de confirmação vale por 48 horas.

**Regras cobertas:** RN06
**Prioridade:** Média — protege o assinante e a reputação da lista, mas não bloqueia o fluxo de envio.
**Cenários:** features/us04-descadastro.feature

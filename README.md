# NewsFlow — do Gherkin ao Cucumber

Alunos: Luciano Eude e Gustavo Mariano

Exercício de BDD sobre o NewsFlow, a plataforma de newsletters e notificações da Vértice:
quatro histórias de usuário, cenários em Gherkin e uma suíte Cucumber.js que roda de verdade.

## Como rodar

```bash
npm install
npm test            # executa todos os cenários e gera relatorios/cucumber-report.html
npm run test:dry    # valida a sintaxe e confere se todo passo tem implementação
```

Requer Node.js 18 ou mais recente.

## Onde está cada coisa

| Caminho | Conteúdo |
|---|---|
| [docs/historias.md](docs/historias.md) | As histórias US01–US04, com critérios de aceitação, regras e prioridade |
| [features/](features/) | Um `.feature` por história, em português (`# language: pt`) |
| [features/step_definitions/](features/step_definitions/) | Os steps que ligam cada frase do Gherkin ao domínio |
| [features/support/](features/support/) | O World (estado de cada cenário) e o domínio em memória, com relógio simulado |
| [relatorios/cucumber-report.html](relatorios/cucumber-report.html) | Relatório HTML da última execução |

## Histórias

| ID | História | Regras | Prioridade |
|---|---|---|---|
| US01 | Salvar rascunho automaticamente | RN01 | Alta |
| US02 | Aprovar edição | RN02 | Alta |
| US03 | Agendar envio | RN03 (e a exigência de aprovação da RN02) | Alta |
| US04 | Descadastrar-se e voltar à lista | RN06 | Média |

Os cenários usam etiquetas para seleção: `@feliz`, `@excecao`, `@limite`, `@restauracao`, além do ID da
história e da regra (`@US03`, `@RN03`). Exemplo: `npx cucumber-js --tags "@US03 and @limite"`.

## Fora de escopo

- **RN04 — Segmentação:** exige modelar segmentos e a deduplicação de assinantes; ficaria como uma quinta história, e o prazo cobre quatro.
- **RN05 — Frequência:** o limite de 2 por semana depende de calendário e de uma fila semanal, o que pede uma história própria.
- **RN07 — Falha de entrega:** envolve tentativas com intervalos e tipos de bounce, regras mais técnicas e de menor valor visível aos atores escolhidos.
- **RN08 — Notificação push:** a janela de silêncio e o limite diário pertencem a um canal à parte, distinto do e-mail tratado aqui.

## Premissas

- "Válido por 48 horas" inclui exatamente 48 horas; com 49 horas o link já expirou.
- "Até 5 minutos antes" inclui exatamente 5 minutos; com 4 minutos já não é possível cancelar.
- O relógio é controlado pelo World (início em 10/03/2026, 08h30, America/Sao_Paulo), então não há `sleep` fixo.
- As mensagens exibidas ao ator, quando o enunciado não as define, foram escolhidas por nós.

## Saída do `npm test`

```
.....................................................................................................................................................

30 scenarios (30 passed)
149 steps (149 passed)
0m 0.172s (0m 0.048s executing your code)
```

---
tipo_template: ai-game-template
versao_template: 4.0
---

# 🚀 STARTUP — modo "Startup building" · `ai-game-template`

> **Agente:** este é o **único** arquivo que você lê para iniciar o projeto (além de `MODO.md` e `AGENTS.md`). **Não abra `niveis/*.zip`** e não crie arquivos do SOURCE à mão: a estrutura vem pronta do pacote do nível.

## 0. Regras do modo STARTUP
1. **Gatilho:** `MODO.md` com `modo: STARTUP`, o comando `/startup` ou o usuário escrever "startup".
2. Até o diagnóstico ser **aprovado**, não crie, edite, mova nem apague nada.
3. **Formulário:** use a ferramenta de perguntas com opções quando existir (até 4 perguntas por bloco); senão, numere as perguntas e peça respostas curtas.
4. **No máximo 2 rodadas.** Só é bloqueante a dúvida que muda o **tipo**, a **pontuação** ou o **nome**. O resto vira `a confirmar` e entra nas pendências.
5. **Não invente.** Use só o que o usuário respondeu.
6. Os passos 5 e 6 precisam de terminal (Claude Code, Cowork, Codex). Sem terminal, entregue o diagnóstico e os **passos manuais** da seção 7.

## 1. Fluxo
1. Rodada 1 (seção 2) → 2. Rodada 2, se preciso (seção 3) → 3. Pontuação (seção 4) → 4. **Diagnóstico para aprovação** (seção 6) → 5. Aplicar estrutura (seção 7) → 6. Pré-preencher e concluir (seção 7) → 7. Modo **PLANEJAMENTO**.

## 2. Rodada 1

**Bloco A — Tipo (opções).** Se a resposta não for deste template, **pare** e indique o template certo:

| Tipo de projeto | Template |
|---|---|
| Automação, agente de IA, cowork/documentos ou ferramenta interna | `ai-project-template` |
| Produto SaaS (clientes assinam e usam pela web/app) | `ai-saas-template` |
| Jogo (jam, protótipo ou lançamento) | `ai-game-template` |

**Bloco B — Identidade (texto curto):** B1 nome provisório · B2 objetivo em 1 a 3 frases · B3 quem usa e qual problema resolve · B4 prazo da primeira entrega.

**Bloco C — Pontuação (opções):**

| # | Pergunta | A (0) | B (1) | C (2) |
|---|---|---|---|---|
| C1 | Duração e escopo | Jam ou protótipo, até 2 semanas | Jogo curto, 1 a 3 meses | Mais de 3 meses ou conteúdo extenso |
| C2 | Sistemas e conteúdo | 1 mecânica central e poucas fases | Vários sistemas (economia, loot, progressão) | Muitos sistemas, meta-progressão ou conteúdo procedural grande |
| C3 | Online | Nenhum | Ranking ou leaderboard simples | Co-op, multiplayer ou servidor próprio |
| C4 | Publicação e monetização | Grátis (ex.: itch.io) | Premium em loja (Steam, mobile) | Free-to-play, compras no app ou várias plataformas |
| C5 | Equipe | 1 pessoa + IA | 2 a 3 pessoas | 4 ou mais, ou papéis separados (arte, áudio, design) |

**Bloco D — Contexto técnico (opções + "não sei"):**

| # | Pergunta | Opções sugeridas |
|---|---|---|
| D1 | Engine | Godot · Unity · Phaser/web · outra · não sei |
| D2 | Plataforma | PC · web · mobile · console |
| D3 | Gênero e perspectiva | texto curto (ex.: roguelite top-down) |

## 3. Rodada 2 (só se necessário)
Pergunte apenas o que ficou bloqueante e complete o contexto base:
- Fora do escopo (até 3 itens) · regras inegociáveis (até 3) · métrica de sucesso · quem aprova as entregas
- Pitch em 1 frase e fantasia do jogador
- Core loop de 30 segundos (texto curto)
- Até 3 jogos de referência

## 4. Pontuação
Rode `python tools/startup.py pontuar C1,C2,C3,C4,C5` (ex.: `pontuar 1,2,0,1,2`) e use o `NIVEL_RECOMENDADO`. Sem terminal, aplique a tabela:

| Pontos | Nível |
|---|---|
| 0 a 3 | 🟢 SIMPLES |
| 4 a 7 | 🟡 MÉDIO |
| 8 a 10 | 🔴 COMPLEXO |

**Ajustes obrigatórios**

- Pergunta 3 com resposta **2**: no mínimo **MEDIO** (multiplayer ou servidor próprio).
- Pergunta 4 com resposta **2**: no mínimo **MEDIO** (free-to-play, compras no app ou várias plataformas).
- Três ou mais respostas **2**: **COMPLEXO**.
- Na dúvida entre dois níveis, fique no **menor** e promova depois (é barato; o inverso gera retrabalho).

O usuário pode **sobrescrever** o nível no diagnóstico; registre o motivo.

## 5. Manifesto de níveis (arquivos do SOURCE criados pelo pacote)

**🟢 SIMPLES** — 15 obrigatórios
  - `contexto-master.md`
  - `00-conceito/`: `game-concept.md`
  - `01-design/`: `core-loop.md`, `mecanicas.md`
  - `03-tecnico/`: `engine-e-stack.md`, `arquitetura-de-codigo.md`, `mapa-cenas-nodos.md`, `contrato-de-eventos.md`
  - `04-dados-de-design/`: `entidades.json`
  - `05-agentes/`: `guardrails.md`
  - `05-agentes/skills/`: `prototipar-greybox.md`, `juice-e-feel.md`, `corrigir-bug.md`, `revisar-entrega.md`
  - `06-qualidade/`: `definicao-de-pronto.md`

**🟡 MÉDIO** — 32 obrigatórios (= nível anterior +)
  - `00-conceito/`: `pilares-e-experiencia.md`
  - `01-design/`: `progressao-e-economia.md`, `niveis-e-mundo.md`, `controles-e-ux.md`
  - `02-direcao-arte-audio/`: `art-bible.md`, `convencoes-de-assets.md`
  - `03-tecnico/`: `performance-e-plataformas.md`, `pipeline-de-build.md`
  - `04-dados-de-design/`: `README.md`, `habilidades.csv`, `inimigos.csv`
  - `05-agentes/skills/`: `projetar-mecanica.md`, `implementar-feature.md`
  - `06-qualidade/`: `playtest-e-balanceamento.md`, `checklist-revisao.md`
  - `07-producao/`: `escopo-mvp.md`
  - `09-decisoes/`: `ADR-000-modelo.md`

  - *opcionais (vêm no pacote; o diagnóstico decide se ficam):* `00-conceito/publico-e-mercado.md`, `01-design/narrativa-e-personagens.md`, `02-direcao-arte-audio/direcao-de-audio.md`, `02-direcao-arte-audio/ui-style-guide.md`, `03-tecnico/multiplayer-e-rede.md`, `05-agentes/papeis-e-fluxo.md`, `05-agentes/skills/criar-conteudo-narrativo.md`, `05-agentes/skills/gerar-asset-brief.md`

**🔴 COMPLEXO** — 36 obrigatórios (= nível anterior +)
  - `07-producao/`: `roadmap-e-marcos.md`
  - `08-referencias/`: `jogos-referencia.md`
  - `08-referencias/templates/`: `template-gdd-feature.md`, `template-asset-brief.md`

  - *opcionais (vêm no pacote; o diagnóstico decide se ficam):* `00-conceito/publico-e-mercado.md`, `01-design/narrativa-e-personagens.md`, `02-direcao-arte-audio/direcao-de-audio.md`, `02-direcao-arte-audio/ui-style-guide.md`, `03-tecnico/multiplayer-e-rede.md`, `05-agentes/papeis-e-fluxo.md`, `05-agentes/skills/criar-conteudo-narrativo.md`, `05-agentes/skills/gerar-asset-brief.md`, `08-referencias/exemplos-de-saida/exemplo-gdd-feature.md`, `09-decisoes/ADR-001-exemplo.md`

## 6. Diagnóstico (mensagem para aprovação)

```
🩺 DIAGNÓSTICO DO STARTUP
Projeto: <nome provisório>  →  pasta/repositório: <prefixo-nome>
Tipo: <tipo> (template ai-game-template)
Objetivo: <1 a 3 frases>
Usuários e problema: <resumo>
Pontuação: C1=<n> C2=<n> C3=<n> C4=<n> C5=<n>  → total <n>
Regras aplicadas: <faixa, pisos, 3×2>
Nível recomendado: <NIVEL>   (sobrescrito? <não | sim: motivo>)
Arquivos do SOURCE: <n> obrigatórios; opcionais mantidos: <lista ou nenhum>; opcionais removidos: <lista>
Contexto técnico: <respostas do bloco D>
Pré-preenchimento previsto: <arquivos da seção 7>
Premissas: <o que assumi a partir das respostas>
Pendências (a confirmar): <lista>
Responda "aprovado" ou diga o que ajustar.
```

## 7. Aplicar (somente depois de "aprovado")
1. Se for repositório git com commits, o script cria a tag `template-original`. Sem git, ele guarda o template em `.startup-backup/`.
2. Grave o diagnóstico aprovado em `diagnostico-startup.md` (na raiz).
3. Rode: `python tools/startup.py aplicar --nivel <NIVEL> --nome <prefixo-nome> [--remover caminho1,caminho2]` (`--remover` só aceita opcionais do nível).
4. **Pré-preencha** com as respostas, um arquivo por vez. Troque `<...>` só onde houver dado; o resto fica para o planejamento e entra em `ARTEFATO/_logs/pendencias-startup.md`. Registre cada arquivo em `ARTEFATO/_logs/changelog-source.md` com origem `startup`. Respeite o limite do contexto-master do nível.

| Arquivo (se existir no nível) | O que preencher |
|---|---|
| `contexto-master.md` | nome, pitch, plataforma, regras inegociáveis; mapa só com arquivos existentes |
| `00-conceito/game-concept.md` | nome, gênero, plataforma, pitch, público, fantasia do jogador |
| `01-design/core-loop.md` | loop descrito na rodada 2 |
| `03-tecnico/engine-e-stack.md` | engine e plataforma (bloco D) |
| `05-agentes/guardrails.md` | ações proibidas e que exigem aprovação informadas |
| `06-qualidade/definicao-de-pronto.md` | critério de sucesso e quem aprova |
| `07-producao/escopo-mvp.md` | prazo e o que fica fora |
| `08-referencias/jogos-referencia.md` | jogos de referência citados |

5. Rode `python tools/startup.py concluir`: apaga o script de startup e **renomeia a pasta** para o nome do projeto.
6. Mensagem final: resumo do que foi criado, pendências e o **próximo prompt** (P0 de `PROMPTS-PLANEJAMENTO.md`). Avise que a sessão deve ser reaberta na pasta nova.

**Passos manuais (sem terminal):** descompacte `niveis/<nivel>.zip` numa pasta nova `<prefixo-nome>`; no `MODO.md` dela preencha `projeto:` e `modo: PLANEJAMENTO`; apague os opcionais não mantidos e as linhas deles no mapa do `contexto-master.md`; cole o diagnóstico em `ARTEFATO/_logs/diagnostico-startup.md`.

## 8. Nomenclatura (pasta e repositório)
Padrão `<prefixo>-<nome-curto>`: minúsculas, números e hífens, sem acento, até 40 caracteres. Prefixos deste template: `game-` (jogo) · `jam-` (game jam ou protótipo). Exemplos: `game-farol-perdido`, `jam-luz-e-sombra`. O repositório no GitHub é criado só depois, já em PLANEJAMENTO, com o mesmo nome.

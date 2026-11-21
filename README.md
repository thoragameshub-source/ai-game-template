# 🧩 ai-game-template

> Template para jogos feitos com vibe coding (jam, protótipo ou lançamento). Arquitetura **SOURCE / ARTEFATO**, modos **PLANEJAMENTO / EXECUÇÃO** e **3 níveis de complexidade** escolhidos automaticamente no *Startup building*.

## Como iniciar um projeto
1. No GitHub, **Use this template** → *Download ZIP* (ou clone) e abra a pasta **localmente**.
2. Abra o agente na pasta:
   - **Claude Code:** digite `/startup`
   - **Cowork / Codex / outros:** digite `startup`
3. Responda as perguntas (até 2 rodadas) e **aprove o diagnóstico**.
4. O agente cria a estrutura do nível, pré-preenche o SOURCE, renomeia a pasta (ex.: `game-farol-perdido`, `jam-luz-e-sombra`) e entra em **PLANEJAMENTO**.
5. Termine o planejamento e só então suba o projeto para o GitHub com o mesmo nome.

## Níveis

| Nível | Exemplos | Arquivos no SOURCE |
|---|---|---|
| 🟢 SIMPLES | Game jam, protótipo, mini-jogo de 1 mecânica | 15 |
| 🟡 MÉDIO | Jogo curto com economia, fases e lançamento em loja | 32 |
| 🔴 COMPLEXO | Jogo online, free-to-play, conteúdo extenso, time com papéis | 36 + opcionais |

## Estrutura do template
```
📦 ai-game-template/
├── 📄 README.md         → este arquivo (humanos)
├── 🚀 STARTUP.md        → instruções do Startup building (o agente lê só ele)
├── 🚦 MODO.md           → modo: STARTUP
├── 📄 AGENTS.md · CLAUDE.md · .claude/commands/startup.md
├── 📁 niveis/           → simples.zip · medio.zip · complexo.zip · niveis.json
├── 📁 tools/startup.py  → aplica o nível, renomeia a pasta, checa os pacotes
└── 📁 .github/workflows/checar-template.yml
```

## Uso manual (sem agente)
Baixe `niveis/<nivel>.zip`, descompacte numa pasta `<prefixo>-<nome>` e siga o `README.md` de dentro do pacote.

## Outros templates
`ai-project-template`, `ai-saas-template`

## Manutenção
Os pacotes são **gerados** pelo repositório `ai-template-factory` (`python build.py`). Não edite os zips à mão; o check `checar-template` falha se pacote, `niveis.json` e `STARTUP.md` divergirem.

# Planejamento do ecossistema de vídeo — da ideia à medição

Referência analisada: [howtoyoutube.dev](https://howtoyoutube.dev/) ("YouTube playbook for technical creators", fonte em [joelhooks/howtoyoutube](https://github.com/joelhooks/howtoyoutube), atualizado em 08/10/2026). O playbook é um conjunto de práticas, não um software. Este documento traduz essas práticas em **módulos, fluxos, dados e métricas** do nosso produto.

---

## 1. Princípios que vamos herdar da referência

| Princípio do playbook | O que significa para o produto |
|---|---|
| **Elevar o piso** ("seu pior vídeo deve melhorar") | O painel principal mostra o *piso* (pior vídeo / percentil 25) e não só os picos. |
| **Embalar antes de gravar** (título + thumbnail primeiro) | Um vídeo não avança para "Gravação" sem título e rascunho de thumbnail aprovados. |
| **Título "stretch"** (nem verdade literal, nem clickbait) | Editor de títulos com escada Verdade → Stretch → Clickbait e geração em lote. |
| **Primeiros 15–20 s roteirizados palavra por palavra** | O roteiro separa *intro roteirizada* de *corpo em tópicos*. |
| **"Arena" dos primeiros 6 minutos** (reengajar em ~1, ~3 e ~6 min) | Marcadores de tempo no roteiro, na edição e no gráfico de retenção. |
| **AVD vale mais que CTR** | A métrica principal do painel é a duração média de visualização (AVD); o CTR avalia a embalagem. |
| **Formatos repetíveis** (a continuação mantém 85–90% das views) | Biblioteca de formatos com taxa de repetição calculada. |
| **Julgar a estratégia em 4–6 meses** | Visão de estratégia com janela de 4–6 meses, não de vídeo a vídeo. |
| **Reembalar vídeos estagnados** | Alertas automáticos de "estagnado → trocar título/thumbnail". |
| **Cadência previsível** (1 vídeo longo por semana, com mais de 8 min) | Calendário com meta de cadência e alerta de irregularidade. |

---

## 1.1 Trilhas de criação

A criação é dividida em três trilhas, cada uma com seu agente, seu modelo de briefing e seu checklist:

| Trilha | Formatos | Agente | Modelo |
|---|---|---|---|
| Vídeo horizontal | 16:9: YouTube longo | `briefing-video-horizontal` | `briefings/_modelo-video-horizontal.md` |
| Vídeo vertical | 9:16: Reels, Shorts, TikTok (nativo ou corte do horizontal) | `briefing-video-vertical` | `briefings/_modelo-video-vertical.md` |
| Criativos de imagem | Thumbnail, capa, post, carrossel, story | `briefing-criativo-imagem` | `briefings/_modelo-criativo-imagem.md` |

As trilhas se conectam assim: o horizontal marca os trechos que viram vertical, e tanto o horizontal quanto o vertical pedem a thumbnail ou capa à trilha de imagem. A edição dos dois tipos de vídeo fica com o agente `edicao`.

## 2. Pipeline (estágios do quadro Kanban)

```
Ideia → Validação → Embalagem → Roteiro → Gravação → Edição (V1, V2…) → Revisão → Pré-lançamento (não listado) → Publicado → Medição → (Reembalagem)
                                                                                                                                   ↑______________|
```

Cada estágio tem um **checklist de saída**, extraído do checklist do playbook. A ideia é o checklist "que se usa numa terça-feira".

### 2.1 Ideação e "content brain"
- **Banco de ideias**, com origem: trabalho do dia a dia, sala de roteiristas, outlier observado, notícia.
- **Radar de outliers**: canais acompanhados e alerta quando um vídeo faz mais de 5× a média do canal ("um canal de 100 mil que faz 1 milhão: entenda por quê").
- **Lista de estudo compartilhada** entre criador e editor, com meta de 4–5 h por semana e registro do que cada um assistiu.
- **Revisão semanal de concorrentes**: intros, edição e embalagem.
- **Sala de roteiristas**: sessão em que as ideias chegam já formadas e recebem votos e comentários.
- Regra de triagem: se o vídeo tem só 1–2 pontos, ele vira Short ou post. Isso é uma sugestão automática do sistema.

### 2.2 Validação
- Pesquisa do título no YouTube: guardar os principais resultados e anotar o que funcionou, o que evitar e qual ângulo ficou de fora.
- Classificar a **pista (lane)**: amplo, nicho ou projeto pessoal. O painel mostra o mix do catálogo, e a meta é ~95% de vídeos em que acreditamos.
- Marcar se o vídeo é de **crescimento** (público novo, segue a fórmula) ou um **mergulho profundo** (seguidores, a fórmula fica livre).

### 2.3 Embalagem
- **Escada de títulos**: escrever a versão literal e depois o "stretch". O teste é provocar um "hein?" e não um "não acredito". Usar Title Case.
- **Brainstorm em lote** com várias opções e votação. Também é possível combinar dois títulos.
- **Thumbnail**:
  - Estrutura: ideia + inimigo ou salvador + rosto. O rosto fica numa posição fixa.
  - No máximo 1–2 palavras de texto. Usar a primeira metáfora óbvia.
  - **Teste do "squint"**: prévia desfocada e em tamanho de celular.
  - **Biblioteca de retratos**, organizada por expressão: bravo, sobrancelha levantada, joinha.
  - **Simulador da página do canal**, para ver se ficou repetitivo demais.
- Ligação explícita entre a frase da intro e a imagem da thumbnail.

### 2.4 Roteiro em 4 camadas
1. Embalagem: título e thumbnail.
2. Intro: 2–3 frases, 15–20 s, com contador de tempo de leitura.
3. Framework: como o vídeo entrega a promessa.
4. Pontos macro, em tópicos.

Validações automáticas:
- O primeiro ponto real chega até ~3:00.
- Existem reengajamentos previstos em ~1, ~3 e ~6 min.
- Pontos com mais de 2 min têm um reengajamento interno.
- O final está dentro do último ponto, sem outro separado.
- A duração estimada passa de 8 min.

Gerar **várias intros** para ler em voz alta.

### 2.5 Gravação
- Checklist do set ("o equipamento deve ser só apertar botões").
- Lista de tomadas: intros alternativas, final modular, seções opcionais gravadas soltas e versão de 20 s das explicações longas.
- Abrir antes todas as páginas e exemplos que serão mostrados.
- Notas faladas para o editor ("não use essa").

### 2.6 Edição (fluxo criador ↔ editor)
- **3 passes com status próprio**: estrutura → fluxo (assistir tudo) → polimento e gráficos.
- **Comentários com timecode** na versão (V1, V2…), separando *história* de *ofício de edição*.
- Sobreposição dos marcadores de 1, 3 e 6 min na linha do tempo.
- O corte V1 inclui as seções opcionais, e o editor recomenda a versão final (por exemplo, "18 min → 15 min").
- **Notas de produção** devolvidas ao criador: regravar intro, enquadramento, segundo ângulo.
- **Mood board** e guia de marca do editor: fontes, transições, estilo gráfico.
- Papéis: o editor executa e o criador tem o sim ou não final.

### 2.7 Pré-lançamento e publicação
- **Semeadura**: um dia como *não listado* para a comunidade mais engajada, com rastreio de quem assistiu.
- Descrição: 1–2 frases literais e depois os links. Capítulos ficam opcionais, porque o playbook sugere evitá-los quando o público é de desktop.
- Agendamento e distribuição simultânea no X, Discord e comunidade, com cortes para Shorts que alimentam o canal principal.
- Notícias: SLA de publicação no mesmo dia.

### 2.8 Medição e reembalagem
- **Retenção dos primeiros 6 min** comparada com a faixa média do YouTube Studio, com marcadores em 1, 3 e 6 min e no "precipício" do final.
- **Regras de reembalagem**:
  - Embalagem voltada ao núcleo de fãs: lembrete em 48–72 h para testar uma versão mais ampla.
  - Vídeo evergreen estagnado (a definir numericamente: views/dia abaixo de X% da média por N dias): sugerir troca.
  - Vídeo indo bem: **não mexer**.
  - Notícia: só trocar no primeiro dia.
- **Histórico de embalagens** por vídeo (título e thumbnail com data), para ver a virada da curva depois de uma troca.
- **Testes A/B**: só recomendados acima de ~1.000–10.000 impressões por dia. Abaixo disso, vale a intuição.
- **Formatos**: taxa de repetição (views da continuação ÷ original) e espaçamento de cerca de 1 por mês.

---

## 3. Métricas do painel

| Métrica | Uso |
|---|---|
| AVD e % de retenção (geral, em 1, 3 e 6 min, no final) | Métrica principal de distribuição. |
| CTR de impressões | Qualidade da embalagem. |
| Piso do canal (P25 de views em 7 e 28 dias) | Objetivo "elevar o piso". A meta de referência é ~10 mil. |
| Views médias por vídeo | Inscritos vêm depois das views. |
| Cadência (vídeos longos por semana e regularidade) | Previsibilidade. |
| Taxa de repetição de formato | Decidir se o formato continua. |
| Ganho pós-reembalagem | Views/dia antes vs. depois da troca. |
| Mix de pistas do catálogo | Amplo, nicho e projeto pessoal. |

Fontes de dados: YouTube Data API v3 (vídeos, metadados, troca de título e thumbnail) e YouTube Analytics API (retenção, AVD, CTR, impressões).

---

## 4. Modelo de dados (rascunho)

- `Channel`, `TrackedChannel` (concorrentes e referências)
- `Idea` (origem, pista, crescimento ou profundo, status)
- `Video` (estágio, formato, datas, duração-alvo)
- `PackageVersion` (título, thumbnail, vigência de/até, motivo da troca)
- `Script` (intro, framework, pontos macro com tempo estimado, marcadores de reengajamento)
- `Take` / `ShotList`
- `EditVersion` (V1…Vn, passe atual) e `TimecodedComment` (tipo: história ou ofício)
- `Format` (vídeo original, continuações, taxa de repetição)
- `MetricSnapshot` (diário por vídeo) e `RetentionCurve`
- `PortraitAsset` (expressão, posição)
- `StudyLog` e `WritersRoomSession`

---

## 5. Onde entra IA (seguindo o playbook)

- **Sim**: organizar o roteiro, reunir exemplos, rascunhar documentos e slides, gerar variações de título para *o humano escolher*, cortes e máscaras automáticos, transcrição e detecção de silêncio.
- **Não automatizar sem antes dominar**: a decisão criativa de título, thumbnail e "o que deixar no corte". Arte com cara de IA prejudica.

---

## 6. Roadmap sugerido

| Fase | Entregas |
|---|---|
| **MVP** | Quadro de pipeline com checklists por estágio; editor de embalagem (escada de títulos e teste do squint); roteiro em 4 camadas com contador de tempo e marcadores 1/3/6; integração com a Data API para importar vídeos. |
| **Fase 2** | Analytics: retenção com marcadores, painel de piso e AVD, histórico de embalagens e alertas de reembalagem. |
| **Fase 3** | Colaboração com o editor: versões, comentários com timecode, 3 passes, mood board e notas de produção. |
| **Fase 4** | Content brain: radar de outliers, lista de estudo, sala de roteiristas e revisão de concorrentes. Também a biblioteca de formatos com taxa de repetição. |
| **Fase 5** | Distribuição: agendamento, semeadura como não listado, posts em X e Discord, cortes para Shorts e IA de apoio. |

---

## 7. Decisões em aberto
(adaptadas das "perguntas para estrategista e editor" do playbook)

1. Qual o nosso mix de pistas (amplo, nicho, projeto pessoal)?
2. Em números, o que é "estagnado" para disparar a reembalagem?
3. A cadência de 1 vídeo por semana é realista? Qual é a edição mínima viável?
4. Quem é responsável pelas thumbnails? Fazemos uma sessão de fotos para a biblioteca de retratos?
5. Que formato pode se repetir todo mês sem nos rotular?
6. O produto é só para uso interno ou multi-canal / SaaS? Essa resposta define a autenticação e o modelo de dados.

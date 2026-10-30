# Mona's Octoverse Arcade — revisao e QA (v2)

## Escopo e arquitetura
O projeto preserva `.github/extensions/monas-octoverse-arcade-starter/extension.mjs` sem alteracoes. O jogo e implementado exclusivamente em `game.html`, com HTML, CSS e JavaScript puro, sem CDN, build nem dependencias externas.

## Defeitos corrigidos
| ID | Antes | Depois | Aceitacao |
|---|---|---|---|
| UX-01 | Canvas 760:480 com barras vazias em telas estreitas | Dimensoes do canvas acompanham a area CSS; pixel ratio otimizado | Sem letterboxing nos tamanhos 280/320/390 |
| UX-02 | Dica completa do Copilot apenas na coluna lateral | Dica no pop-up dentro do jogo a cada dez commits | Mensagem visivel durante a partida |
| UX-03 | Controles mobile reduzidos | Alvos tacteis maiores e jogabilidade por toque, botoes ou teclado | Controle utilizavel em painel estreito |
| UI-04 | Qualidade visual/colisao variavel em DPR alto | Backing store redimensionado com DPR e posicoes remapeadas no resize | Canvas nitido e toque alinhado |
| JOG-05 | Bugs podiam nascer sobre commits na mesma onda | Tentativas de spawn em uma coluna desocupada | Conflitos de spawn menos frequentes |
| KEY-06 | Atalho Espaco competia com clique nativo | Elementos button mantem ativacao propria | Inicio/reinicio consistentes |
| UX-07 | Foco podia se perder em transicoes | Foco retorna ao Canvas ou ao botao de overlay | Navegacao por teclado |

## Regras de negocio e recursos
- Mona coleta quadrados verdes e cada commit aumenta score e streak em 1.
- Bugs vermelhos encerram a rodada, exceto quando dash, invulnerabilidade ou escudo protegem a personagem.
- Escudo absorve um impacto; magnetismo atrai commits durante 8 segundos.
- Dash dura 0,24s, cooldown de 4s; disponivel por espaco ou botao.
- Dificuldade cresce pelo maior entre pontuacao e tempo de sobrevivencia, ate o nivel 12.
- Copilot oferece dicas a cada multiplo de dez pontos.
- A partida exibe ready, running, paused e game over; o recorde e salvo localmente.
- Audio e opt-in; modo de movimento reduzido e respeitado.

## Plano de verificacao
| Caso | Procedimento | Resultado |
|---|---|---|
| UI-01 | Navegador Chromium em 280, 320, 390, 768 e 1440 CSS px | PASS: sem overflow horizontal ou falhas JavaScript |
| GAME-01 | Iniciar partida e mover com teclas | PASS |
| GAME-02 | Ativar dash | PASS: entra em cooldown |
| STATE-01 | Pausar e retomar pelo overlay | PASS |
| RESP-01 | Conferir dimensoes CSS/backing store | PASS: DPR refletido no canvas |
| FUNC-10 | Coletar exatamente dez commits e ler dica | NOT_RUN como teste automatizado |
| GAME-OVER | Colisao fatal e reinicio | NOT_RUN como teste automatizado |
| COPILOT | Abrir via Copilot App real | NOT_RUN |

## Operacao
Nenhuma migration, configuracao ou package.json necessario. Publicar apenas em branch isolada. Rollback: restaurar `game.html` da branch main. A avaliacao de diversao e o teste do Canvas no Copilot App dependem de execucao humana no ambiente do workshop.

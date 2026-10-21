# Relatório de testes — Galeria Pro Clínica 1.4.1 (21/10/2026)

Ambientes, separados: **Linux** (testes automatizados), **Wine 9.0** (Windows simulado: instalador
e programa compilados). **Windows real e impressora física: não testados.**

## 1. Data fixa no cabeçalho (testes obrigatórios)
PDFs gerados com: nome curto, nome médio, nome extremamente longo, nome com vários espaços — cada
um num exame de **3 páginas** com os modelos **6, 9 e 12** (12 páginas por ambiente). A posição foi
lida **do próprio PDF** (coordenadas do texto).

| Verificação | Linux | Wine (programa instalado) |
|---|---|---|
| Coordenada horizontal da data em todas as 12 páginas | idêntica (517,28 pt) | idêntica (503,61 pt) — passo H1 |
| Borda direita da data = margem direita da área útil = borda direita das fotos | sim (±0,3 mm no PDF; exata na geometria) | sim |
| Nome termina antes de “Data:” (sem sobreposição) | sim, nos 4 casos | sim |
| Mesma linha de base para nome e data, cabeçalho com uma linha | sim | sim |
| Nome extremamente longo: fonte reduzida até 80% + “…” só no nome | sim | sim |
| Margem direita configurada diferente (20 mm): a data acompanha | sim | — |

(A coordenada difere entre Linux e Wine porque as fontes instaladas em cada ambiente têm larguras
diferentes; dentro de cada ambiente ela não muda.) Prévia, PDF e impressão usam a mesma função.

## 2. “Sobre”
Janela aberta e conferida (texto novo; “Versão 1.4.1 — 2026” lida do programa).

## 3. Linux — total: 139 testes (138 aprovados como administrador + 1 de permissão aprovado como usuário comum)
Novos: data fixa com 6 nomes × 5 modelos, nome longo reduzido/truncado, margem configurável,
PDF real com os 4 nomes × 3 páginas. O teste antigo que esperava o nome longo quebrado em várias
linhas (com a data embaixo) foi substituído pela regra nova.

## 4. Wine 9.0 — instalador e programa 1.4.1
- Atualização 1.4.0 → 1.4.1 por cima: 25 arquivos de exames/configuração intactos (SHA-256),
  cópia `config.backup-antes-v1.4.1.json`, versão 1.4.1 no registro, arquivos idênticos à distribuição.
- Autoteste do programa instalado: **36 passos aprovados**, nenhuma falha (inclui a reutilização
  U0–U10, a regressão 6/9/12, a estabilidade E1–E3 e o cabeçalho H1).

## 5. NÃO testado
- Impressora física; Windows 10/11 real com mouse físico; arrastar físico; Capture Pro ao vivo.

---
## Versão anterior — 1.4.0

Ambientes, separados: **Linux** (testes automatizados, janela real), **Wine 9.0** (Windows
simulado: instalador e programa compilados). **Windows real e impressora física: não testados.**

### 1.4.0 — Fotografias reutilizáveis — testes obrigatórios (seção 6 do pedido)
Cliques reais na miniatura (eventos de mouse), Delete real na prévia.

| Teste | Linux (janela real) | Wine (programa instalado) |
|---|---|---|
| **Critério: 10 cliques na mesma foto = 10 usos** (5 pares rápidos = duplo clique do Windows) | aprovado (6 + 4, página nova) | aprovado (U0) |
| 1. Adicionar com um clique | aprovado | aprovado (U1) |
| 2. Clicar de novo: aparece duas vezes | aprovado | aprovado (U2) |
| 3. A mesma foto 6 vezes numa página de 6 | aprovado | aprovado (U3) |
| 4. Reutilizar em outra página | aprovado | aprovado (U4) |
| 5. Retirar só uma ocorrência (prévia + Delete) | aprovado (com e sem “Reorganizar ao retirar”) | aprovado (U5) |
| 6. As demais continuam intactas; a foto continua na galeria | aprovado | aprovado (U6) |
| 7. Limpar uma página sem afetar as outras (Ctrl+Z restaura) | aprovado | aprovado (U7) |
| 8. Salvar e reabrir com as repetições; nenhum arquivo duplicado no disco | aprovado | aprovado (U8) |
| 9. PDF com todas as ocorrências (JPEG original byte a byte em cada uma) | aprovado | aprovado (U9: [5, 2]) |
| 10. Galeria livre: miniatura usada desenhada com a mesma borda/fundo de uma nunca usada | aprovado | aprovado (U10) |

Também verificado: a lupa amplia sem mexer na impressão; Delete na galeria não retira nada (só
orienta); arrastar na prévia move/troca só aquela ocorrência; arrastar da galeria coloca mais uma
ocorrência ou substitui só aquela; “Retirar todas as ocorrências” pelo menu; **Selecionar fotos**
continua escolhendo fotos distintas (Completar mantém as repetições manuais e acrescenta fotos novas).

## 2. Compatibilidade
- Exame **sem** repetição grava formato 2: a 1.3 abre normalmente (verificado com o código da 1.3).
- Exame **com** repetição grava formato 3: a 1.3 **recusa** abrir (“salvo por uma versão mais nova”),
  em vez de descartar as repetições (verificado com o código da 1.3).
- Atualização 1.3.1 → 1.4.0 por cima (Wine): 25 arquivos de exames/configuração intactos (SHA-256),
  cópia `config.backup-antes-v1.4.0.json`, versão 1.4.0 no registro, arquivos instalados idênticos
  à distribuição.

## 3. Mantido da 1.3.1 (sem piscadas)
Autoteste do programa instalado: E1 (510 larguras da galeria sem redesenho contínuo), E2 (parado:
0 redesenhos, CPU 1,7%), E3 (após cliques, trocas 6/9/12 e navegação a janela assenta). Teste
automático da varredura da galeria aprovado.

## 4. Linux — total: 132 testes (131 aprovados como administrador + 1 de permissão aprovado como usuário comum)
Novos: reutilização (composição, ocorrências independentes, automático distinto), 10 cliques,
cliques rápidos + lupa, fluxo obrigatório 1–10, PDF com repetição sem perda, formato 3.
Testes antigos que exigiam “2º clique desmarca” ou “nunca repete” foram atualizados para a regra
nova, mantendo o que verificam (posições, páginas independentes, PDF, galeria intacta).

## 5. Wine 9.0 — autoteste do programa instalado 1.4.0
**35 passos aprovados**, nenhuma falha (fluxo 1–9, regressão 6/9/12 R1–R10, reutilização U0–U10,
estabilidade E1–E3). Substitutos de `icuuc.dll`/`mscms.dll` só no ambiente de teste; **não estão**
no instalador.

## 6. NÃO testado
- Impressora física; Windows 10/11 real com mouse físico; arrastar físico; Capture Pro ao vivo.

---
## Versão anterior — 1.3.1 (correção das piscadas)

### 1.3.1 — investigação (antes de alterar o programa)
- Vídeo da 1.3.0 analisado quadro a quadro: pisca **a galeria** (terceira coluna "fantasma",
  miniaturas mudando entre quadros); prévia, controles e janela estáveis.
- Instrumentação (`tools/instrument_flicker.py`): contagem de redesenhos, redimensionamentos e
  mudanças de grade por componente, com o programa parado, varrendo a largura da galeria pixel a
  pixel e a da janela de 3 em 3 px (8 e 46 fotos, ajuste à página e à largura).
- Resultado na 1.3.0: com 8 fotos e a galeria entre **438 e 462 px** (janela de 1920 px), a grade
  muda ~480 vezes/s e a barra de rolagem aparece/some a cada ciclo; **CPU parado ≈ 84%** de um núcleo.
- Causa: realimentação colunas ↔ barra de rolagem na galeria (detalhes nas notas da versão).
- Revisados sem defeito: temporizadores, conexões de sinais, threads de miniaturas/importação/PDF,
  acompanhamento da pasta, prévia.

### Resultado depois da correção
| Verificação | 1.3.0 | 1.3.1 |
|---|---|---|
| Medições instáveis (1.100 larguras; 8 fotos) | 34 | **0** |
| Medições instáveis (1.100 larguras; 46 fotos) | — | **0** |
| CPU parado, galeria 440 / 446 / 452 px | 83,9 / 84,2 / 84,4 % | **1,6 / 1,8 / 1,6 %** |
| Filmagem da janela real, 3 s a 30 quadros/s | 3 telas diferentes alternando | **90 quadros idênticos** |
| Teste automático da varredura da galeria | **falha** (≈220 redesenhos em 0,6 s) | aprovado |

O CPU inclui o laço de medição (≈ 1,5%). O único redesenho periódico com o programa parado é o
cursor de texto piscando no campo do paciente quando ele tem o foco (padrão do Windows).

###  Testes obrigatórios (programa real)
| Teste | Linux (janela real) | Wine (programa instalado) |
|---|---|---|
| Interface aberta e parada | aprovado (0 redesenhos em 3 s) | aprovado (E2: 0 redesenhos, CPU 1,7%) |
| Seleção e desmarcação repetidas (cliques reais) | aprovado | aprovado (passos 1, 1b, 2, 5, 7, 9, E3) |
| Mudança entre 6, 9 e 12 | aprovado, janela assenta após cada troca | aprovado (R, R7, E3) |
| Geração de PDF | aprovado, janela assenta depois | aprovado (8, 9, R10: páginas com 6/9/12 imagens) |
| Navegação entre páginas | aprovado | aprovado (R1-2, E3) |
| Varredura da largura da galeria | aprovado | aprovado (E1: 510 larguras, 2 alturas) |
| Travamentos | nenhum | nenhum |

###  Linux — total: 126 testes (125 aprovados como administrador + 1 de permissão aprovado como usuário comum)
Inclui os 2 testes novos de estabilidade e todos os anteriores (um clique, duplo clique, páginas
independentes, Limpar, regressão 6/9/12, arrastar, Selecionar fotos 10 em 6, Capture Pro, PDF
byte a byte, salvamento, recuperação, exames da 1.0).

###  Wine 9.0 — instalador e programa 1.3.1
- Atualização 1.3.0 → 1.3.1 por cima: 24 arquivos de exames/configuração intactos (SHA-256),
  cópia `config.backup-antes-v1.3.1.json`, versão 1.3.1 no registro, arquivos instalados
  idênticos à distribuição.
- Autoteste do programa instalado: **24 passos aprovados**, nenhuma falha.
- Substitutos de `icuuc.dll`/`mscms.dll` só no ambiente Wine de teste; **não estão** no instalador.


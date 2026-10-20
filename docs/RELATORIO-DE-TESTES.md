# Relatório de testes — Galeria Pro Clínica 1.3.1 (20/10/2026)

Ambientes, separados: **Linux** (testes automatizados; janela real em servidor X para a
filmagem), **Wine 9.0** (Windows simulado: instalador e programa compilados).
**Windows real e impressora física: não testados nesta versão.**

## 1. Correção P0 — piscadas contínuas
### Investigação (antes de alterar o programa)
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

## 2. Testes obrigatórios (programa real)
| Teste | Linux (janela real) | Wine (programa instalado) |
|---|---|---|
| Interface aberta e parada | aprovado (0 redesenhos em 3 s) | aprovado (E2: 0 redesenhos, CPU 1,7%) |
| Seleção e desmarcação repetidas (cliques reais) | aprovado | aprovado (passos 1, 1b, 2, 5, 7, 9, E3) |
| Mudança entre 6, 9 e 12 | aprovado, janela assenta após cada troca | aprovado (R, R7, E3) |
| Geração de PDF | aprovado, janela assenta depois | aprovado (8, 9, R10: páginas com 6/9/12 imagens) |
| Navegação entre páginas | aprovado | aprovado (R1-2, E3) |
| Varredura da largura da galeria | aprovado | aprovado (E1: 510 larguras, 2 alturas) |
| Travamentos | nenhum | nenhum |

## 3. Linux — total: 126 testes (125 aprovados como administrador + 1 de permissão aprovado como usuário comum)
Inclui os 2 testes novos de estabilidade e todos os anteriores (um clique, duplo clique, páginas
independentes, Limpar, regressão 6/9/12, arrastar, Selecionar fotos 10 em 6, Capture Pro, PDF
byte a byte, salvamento, recuperação, exames da 1.0).

## 4. Wine 9.0 — instalador e programa 1.3.1
- Atualização 1.3.0 → 1.3.1 por cima: 24 arquivos de exames/configuração intactos (SHA-256),
  cópia `config.backup-antes-v1.3.1.json`, versão 1.3.1 no registro, arquivos instalados
  idênticos à distribuição.
- Autoteste do programa instalado: **24 passos aprovados**, nenhuma falha.
- Substitutos de `icuuc.dll`/`mscms.dll` só no ambiente Wine de teste; **não estão** no instalador.

## 5. NÃO testado
- Impressora física; Windows 10/11 real com mouse físico; arrastar físico; Capture Pro ao vivo.

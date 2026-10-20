# Relatório de testes — Galeria Pro Clínica 1.2.0 (20/10/2026)

Ambientes, separados: **Linux** (testes automatizados), **Wine** (Windows simulado, com o instalador
e o programa compilados) e **Windows real** (só o vídeo enviado pelo usuário com a 1.1 — a 1.2 ainda
não foi usada em Windows real). **Nenhum teste em impressora física.**

## 1. Análise dos vídeos (1.1.0 em Windows real × UltraCap)
| Critério | UltraCap (vídeo) | Galeria Pro 1.1 (vídeo) | Galeria Pro 1.2 |
|---|---|---|---|
| Cliques para selecionar uma foto | 1 (caixa da miniatura) | 1, mas só acertando a caixinha; clicar na foto apenas realçava → vários cliques e ampliação aberta sem querer | **1 em qualquer ponto da miniatura**; outro clique desmarca |
| Selecionar N fotos de uma vez | número + “Selecionar Fotos” (1 clique) | “Selecionar fotos” + Quantidade (1 clique) | igual (1 clique), com Completar/Refazer se já houver composição |
| Clareza da seleção | caixa marcada + número | borda azul fina; fotos não usadas esbranquiçadas (confuso) | **borda e fundo azuis, ✔, número**, fotos sempre nítidas, **contador** |
| Montar páginas | G6/G8 e inserção no editor de texto | modelos 1/2/6/9/12, células | igual + números das posições na prévia |
| Reorganizar a impressão | não observado no vídeo | arrastar, trocar, substituir | igual; ao retirar, as seguintes **sobem automaticamente** (opcional) |
| Prévia | editor de texto (as imagens podem sair do lugar ao editar) | folha real = PDF | folha real = PDF (mesmo desenho) |
| Resultado impresso | não conferido nos vídeos | PDF sem perda | PDF sem perda (conferido abaixo) |

## 2. Linux — testes automatizados: 113 (112 aprovados como administrador + 1 de permissão aprovado como usuário comum)
Os 9 testes funcionais pedidos, na janela real, com **cliques de mouse na miniatura**:

| # | Teste | Resultado |
|---|---|---|
| 1 | Um clique seleciona e outro desmarca (no meio da miniatura); contador atualiza | aprovado (`test_t1_*`) |
| 1b | Duplo clique (sequência do Windows: press, release, dblclick, release) amplia sem mudar a seleção, nas fotos selecionadas e não selecionadas; clique seguinte funciona | aprovado — **defeito encontrado e corrigido** (um clique recente podia ser desfeito) |
| 1c | Gesto de arrastar não marca a foto | aprovado |
| 2 | Seleção manual de 6 fotos por clique, em ordem livre | aprovado |
| 3–4 | Selecionar fotos: 10 com 6 por página → 6 + 4 | aprovado |
| 5 | Duas fotos acrescentadas por clique completam a página 2 | aprovado |
| 6 | Trocar a ordem (arrastar uma foto sobre outra) | aprovado |
| 7 | Retirar uma foto da impressão: continua na galeria e no disco, sem duplicatas | aprovado |
| 8 | Gerar PDF: 2 páginas, 6 + 5 imagens | aprovado; inspeção visual: proporção mantida, sem números/bordas da interface |
| 9 | 6 ciclos de captura nova (pasta acompanhada) + cliques + Selecionar fotos (6/9/12) + impressão: sem perda, duplicação ou travamento | aprovado |
| — | Números das posições aparecem na prévia (pixel azul) e não no PDF (texto extraído) | aprovado |

Todos os testes da 1.1 continuam aprovados (composição, lacunas com a opção desligada, migração
da 1.0, PDF byte a byte, armazenamento, recuperação, acompanhamento da pasta).

## 3. Wine 9.0 — instalador e programa compilados 1.2.0
- Atualização 1.1.0 → 1.2.0 por cima: 21 arquivos de exames/configuração **intactos** (SHA-256),
  `config.backup-antes-v1.2.0.json` criado, versão 1.2.0 no registro, arquivos instalados idênticos à distribuição.
- **Autoteste do programa instalado** (`GaleriaProClinica.exe --autoteste`), com eventos reais de
  mouse na galeria: aprovados os passos 1, 1b, 2, 3–4, 5, 6, 7, 8 e 9, e salvar/reabrir.
- Substitutos de `icuuc.dll`/`mscms.dll` existem só no ambiente Wine de teste; **não estão** no instalador.

## 4. NÃO testado
- **Impressão em impressora física** (não há impressora aqui).
- **1.2.0 em Windows 10/11 real** e o clique com o mouse físico (testado com os mesmos eventos de
  mouse que o Windows entrega, no Linux e no Wine).
- **Arrastar com o mouse físico** (testado pelos sinais que o arrastar dispara).
- **Capture Pro gravando ao vivo** (simulado gravando arquivos na pasta acompanhada).

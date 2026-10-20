# Relatório de testes — Galeria Pro Clínica 1.1.0 (20/10/2026)

Três ambientes, separados abaixo: **Linux** (testes automatizados), **Wine** (Windows simulado)
e **Windows real** (não disponível aqui — pendente). Nada foi testado em impressora física.

## 1. Linux — testes automatizados (pytest): 106 testes, todos aprovados
Python 3.13, PySide6 6.12.0, Qt offscreen. 105 aprovados como administrador; o teste de pasta
sem permissão (pulado como administrador) foi executado e aprovado como usuário comum.

| Arquivo | Testes | O que verifica |
|---|---|---|
| `test_composition.py` | 31 | **Exemplo obrigatório** (10 em 6 → 6+4 com 2 vazias; 2 inclusões manuais preenchem as vazias; a 3ª cria a página 3; nada se mexe); seleção manual sem duplicar; célula vazia escolhida; pedido maior que o disponível; **Completar** preserva posições e preenche lacunas primeiro; Completar sem necessidade não altera; **Refazer**; seleção segue a ordem visível da galeria; **reordenar galeria não muda impressão**; **reordenar impressão não muda galeria**; **retirar mantém a lacuna e as demais posições**; **Reorganizar** preenche lacunas mantendo a sequência e remove página que sobra; **substituir** devolve a anterior à galeria, **trocar** e **mover** sem perda nem duplicação; mover para página cheia recusado sem alterar; troca de modelo com cascata sem perda e preservando os modelos das outras páginas; criação de páginas quando necessário (no modelo da última página); “aplicar em todas” preserva sequência e lacunas; redução absorve lacunas antes de empurrar; excluir página (devolver/passar adiante); mover página; remover do exame deixa lacuna; texto da barra de estado; instantâneo de desfazer; migração do formato 1; saneamento de arquivo editado à mão; células exatas nos 5 modelos |
| `test_layout.py` | 14 | Os cinco modelos e a ordem de leitura; **2 fotos sempre 1 coluna × 2 linhas**; encaixe sem deformar/cortar; nome longo; rodapé de várias linhas; logo; ausência de logo; limites |
| `test_render.py` | 13 | JPEG original **byte a byte** no PDF; PNG/cinza pixel a pixel; BMP sem perda; recorte+rotação; logo transparente; páginas escolhidas; nome seguro; A4 e textos; prévia × PDF rasterizado; imagem ausente; impressão por QPrinter; cálculo de redução para margens da impressora; **células vazias e marcas da interface nunca no PDF** (contagem de imagens por página, texto extraído sem “vazia/posição/P1”, célula vazia branca na rasterização) |
| `test_store.py` | 20 | Nomes iguais não colidem; **salvar/reabrir preserva posições, lacunas, ordem da galeria e edições**; independência da pasta de origem; cópia bit a bit; duplicatas; danificados; formato mais novo recusado; recuperação; gravação atômica; disco cheio; permissão; identidade copiada; histórico; descarte; configuração corrompida; Capture Pro só lido; **exame no formato 1 abre com a mesma impressão e a cópia de segurança é criada uma única vez**; histórico conta fotos nos formatos 1 e 2; **arquivo real gravado pela 1.0.0** abre com a mesma ordem de impressão, lacunas, rotação e rodapé |
| `test_ui.py` | 21 | Janela real: exemplo obrigatório com botões e **desfazer/refazer passo a passo**; diálogo **Completar / Refazer / Cancelar**; quantidade maior que a disponível; caixa de marcação, Espaço e Delete; Ctrl+Z no campo de nome; ordens independentes (arrastar galeria, ordenar por nome, trocar/mover na prévia, reorganizar); clique na célula, Delete deixa lacuna, célula vazia selecionada recebe a foto marcada, botão Reorganizar e desfazer; soltar da galeria substitui / da prévia troca / em vazia move / várias fotos — sem duplicar; **escolher foto para célula sem arrastar** e trocar posição pelo menu; troca de modelo (página e todas) sem perda e desfazendo; salvar e reabrir com lacunas; recuperação após queda; **PDF ignorando página vazia com “Página 1 de 1”**; novas capturas vão para a galeria sem alterar a impressão (e separação entre pacientes); recorte/rotação não destrutivos; remover da galeria deixa lacuna e não apaga a origem; Desmarcar todas; alterações pendentes ao fechar; exame vazio descartado; configurações; busca no histórico |
| `test_watcher.py` | 7 | Imagens antigas não entram; nova captura uma única vez após estabilizar; arquivo pela metade espera; JPEG/BMP incompletos; nova sessão; pasta inexistente; não-imagens ignoradas |

Defeito encontrado e corrigido durante os testes desta versão: o autoteste afirmava ter testado a
inclusão manual mesmo quando não havia foto para isso — agora registra “NÃO TESTADO”.
Ajuste de comportamento após inspeção: páginas criadas pela troca de modelo seguem o modelo da
última página (antes seguiam o modelo reduzido e criavam páginas a mais).

## 2. Compatibilidade com a 1.0.0 (Linux)
Um exame foi criado **com o código da versão 1.0.0** (do histórico do projeto): 16 fotos, 13
marcadas, páginas 1/2/6 + 1 automática, uma foto girada, logo e rodapé. Aberto na 1.1.0: mesmas
páginas (1, 2, 6, 6 com 2 vazias); **PDF da 1.0.0 e PDF da 1.1.0 idênticos pixel a pixel** nas 4
páginas, com as mesmas imagens e codificação; `exame.formato1-backup.json` idêntico ao original;
arquivo regravado no formato 2. O `exame.json` real da 1.0.0 ficou como teste permanente.

## 3. Wine 9.0 (Windows simulado) — instalador e programa compilados
- **Atualização 1.0.0 → 1.1.0** com o instalador silencioso sobre a 1.0.0 instalada, com um exame
  da 1.0 e a configuração na pasta do usuário: 1.552 arquivos instalados idênticos à distribuição
  1.1.0 (SHA-256); versão 1.1.0 no registro; **exame e configuração intactos** (19 arquivos,
  SHA-256); `config.backup-antes-v1.1.0.json` criado.
- **Python e código instalados** abriram o exame da 1.0 (aviso de conversão), geraram o PDF
  (mesmas páginas, fotos e ordem) e salvaram no formato 2 com a cópia de segurança. A comparação
  pixel a pixel com o PDF da 1.0 gerado em Linux difere apenas porque o Wine não tem Arial e usa
  Tahoma (altura de linha diferente desloca o corpo alguns décimos de mm); no mesmo ambiente o
  resultado é idêntico (seção 2).
- **Autoteste do programa instalado** (interface com o plugin `qwindows`): 16 imagens importadas;
  Selecionar fotos 10 em 6 = 2 páginas com 2 células vazias; inclusão manual ocupou a primeira
  vazia (P2 · posição 5); troca de modelo sem perder fotos; PDF; salvar e reabrir com as mesmas
  posições e células vazias.
- **Somente no ambiente de teste do Wine** foram usados substitutos de `icuuc.dll` e
  `mscms.dll` (o Windows 10/11 já traz os verdadeiros). Eles **não estão** na distribuição nem no
  instalador — verificado na pasta `dist` e na pasta instalada.

## 4. NÃO testado (pendente no consultório, Windows real)
- **Impressão em impressora física** (não há impressora aqui). Testado só com a impressora PDF do Qt.
- **Windows 10/11 real**: fontes Arial/Segoe UI, escala de tela, diálogos nativos.
- **Gesto físico de arrastar com o mouse** (a lógica foi testada pelos mesmos sinais que o arrastar
  dispara; a indicação de destino foi conferida por captura de tela).
- **Capture Pro gravando ao vivo** na pasta (simulado com arquivos, inclusive gravação pela metade).
- **Queda de energia real** (a recuperação após fechamento abrupto foi testada).

## Roteiro sugerido no consultório (10 minutos)
1. Instalar a 1.1.0 por cima da 1.0; abrir um exame antigo (aviso de conversão; mesma folha).
2. Novo exame; Acompanhar capturas; capturar 12 imagens no Capture Pro.
3. Fotos por página = 6; Quantidade = 10; Selecionar fotos → conferir 6 + 4 e 2 vazias.
4. Marcar mais 2 fotos (preenchem as vazias) e mais 1 (cria a página 3). Arrastar uma foto
   sobre outra (trocar) e uma da galeria sobre uma ocupada (substituir).
5. Retirar uma foto (Delete) → lacuna; Reorganizar e preencher espaços.
6. Gerar PDF e **imprimir uma página**; comparar papel × PDF × prévia.

# Galeria Pro Clínica 1.3.1 — correção das piscadas (P0)

Versão de correção. **Todas as funções da 1.3.0 foram mantidas**: modelo próprio por página,
Limpar página / Limpar tudo, navegação Anterior/Próxima, Nova página ▾, seleção com um clique,
duplo clique para ampliar, Selecionar fotos + Quantidade, PDF sem perda e os modelos 1, 2, 6, 9 e 12.
Exames e configurações da 1.3.0 abrem sem conversão.

## O que piscava
A **galeria** (não a janela inteira, não a prévia nem os botões). Ela alternava sem parar
entre 2 e 3 colunas, cerca de 480 vezes por segundo, gastando ~84% de um núcleo do processador
com o programa parado. A câmera do celular registrou a média das telas: a terceira coluna "fantasma".

## Causa (medida antes de corrigir)
A quantidade de colunas era calculada pela largura útil da galeria, e essa largura muda quando
a barra de rolagem aparece ou some:

3 colunas → miniaturas maiores → não cabem na altura → **barra aparece** → largura menor →
2 colunas → miniaturas menores → cabem → **barra some** → largura maior → 3 colunas → …

O laço só acontece numa faixa estreita de largura da galeria (≈ 438–462 px, com poucas fotos),
que é exatamente a da janela maximizada em tela de 1920 px na 1.3.0. Na 1.3.0, a nova barra de
navegação mudou a divisão entre galeria e prévia e colocou a galeria nessa faixa. Na 1.1 o
mesmo defeito existia; na 1.2 a galeria ficava fora da faixa, por isso "não piscava".

## Correção (na causa, não cosmética)
- A barra de rolagem vertical da galeria fica **sempre presente**: a largura útil não depende
  mais da quantidade de fotos, e o laço deixa de existir.
- A grade só é recalculada quando a largura da própria galeria muda (não a cada redimensionamento
  de altura) e só é aplicada se mudou de fato.
- Atualizar só o que mudou: ao marcar uma foto, a galeria redesenha só as miniaturas cujo
  estado mudou (antes, todas); a lista de páginas só é reconstruída quando o conteúdo dela muda;
  o estilo do texto da barra inferior só é reaplicado quando muda.

## Verificado também (sem defeito encontrado)
Temporizadores (todos de disparo único), sinais (sem conexões duplicadas), miniaturas e
importação em segundo plano (comunicam-se com a tela só por sinais), acompanhamento da pasta
(só avisa quando há foto nova), prévia (barra fixa desde a 1.3.0; ajuste não oscila).
O único redesenho periódico com o programa parado é o **cursor de texto piscando** no campo
"Nome do paciente" quando ele está com o foco (padrão do Windows, 2 vezes por segundo).

## Testes novos
- Varredura da largura da galeria pixel a pixel (2 alturas de janela): o programa parado não
  pode continuar se redesenhando. **Este teste falha na 1.3.0 e passa na 1.3.1.**
- Janela inteira estável depois de cada operação: marcar/desmarcar repetido, troca 6/9/12,
  Selecionar fotos, navegação entre páginas e geração de PDF.
- Autoteste do programa instalado (passos E1–E3): estabilidade, CPU parado e operações.

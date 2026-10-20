# Galeria Pro Clínica 1.3 — Manual rápido

Organiza as fotos de um exame, monta folhas A4 com a identidade da clínica e imprime ou
gera PDF. Funciona **sem internet**, sem login. As fotos originais **nunca são alteradas**.

## A ideia principal: galeria × impressão
- **Galeria** (à esquerda): todas as fotos do exame. Pode ser ordenada por *importação*, *nome*,
  *data de captura* ou arrastando as miniaturas. **Isso não muda a impressão.**
- **Impressão** (prévia, ao centro): páginas com **células**. Cada foto ocupa uma posição
  (ex.: “P2 · posição 4”). Uma célula pode ficar **vazia**. Mexer na impressão não muda a galeria.

## Primeira vez (uma vez só)
1. **Configurações → Identidade da clínica → Escolher logo…** (PNG transparente ou JPEG).
2. **Rodapé**: endereço, telefone etc. (várias linhas); “Página X de Y”.
3. **Página e impressão**: margens, espaço entre fotos, modelo inicial, impressora.
4. **Pastas**: pasta de capturas do Capture Pro, pasta dos exames, pasta dos PDFs.

## Uso diário
1. **Novo exame** (Ctrl+N): nome do paciente e data.
2. Traga as fotos: **Acompanhar capturas** (as novas do Capture Pro aparecem sozinhas, como
   *disponíveis*), **Adicionar fotos**, **Abrir pasta de capturas** ou arrastar arquivos/pastas.
   Fotos novas **nunca** entram sozinhas na impressão.
3. Escolha o **Modelo** da página (1, 2, 6, 9 ou 12) — na barra acima da prévia ou à direita.
   **Cada página tem o seu modelo**; o seletor vale só para a página atual.

   **Trabalhar página por página (como no UltraCap):** escolha o modelo, clique nas fotos,
   clique em **Nova página ▾** escolhendo o modelo da próxima, clique nas fotos dela, e assim por
   diante. Use **◀ Anterior / Próxima ▶** para navegar; cada página continua como você deixou.
4. Escolha a **Quantidade** (o TOTAL de fotos, não por página) e clique em **Selecionar fotos**.
   Exemplo: 6 por página e quantidade 10 → página 1 com 6, página 2 com 4 e **2 células vazias**.
   As fotos são escolhidas na ordem que a galeria está mostrando. Nenhuma foto é repetida nem
   ampliada para ocupar as células vazias.
   - Se já houver fotos na impressão, o programa pergunta: **Completar seleção até N fotos**
     (mantém tudo e só acrescenta o que falta, preenchendo primeiro as células vazias),
     **Refazer seleção com N fotos** ou **Cancelar**.
5. Ajuste à mão:
   - **Um clique** na miniatura seleciona a foto (borda azul, ✔ e número); **outro clique** desmarca.
     A foto entra na **página em que você está** (primeira posição vazia dali em diante); sem espaço,
     cria uma página nova no final. Páginas anteriores não mudam.
     **Duplo clique** amplia a foto sem mudar a seleção. O contador azul mostra quantas estão selecionadas.
   - Clique numa **célula vazia** da prévia e depois marque uma foto: ela entra **naquela** célula.
     Ou clique com o botão direito na célula → **Escolher foto para esta posição…**
   - **Arrastar** na prévia: sobre célula vazia = *mover*; sobre outra foto = *trocar*.
     Da galeria para a prévia: célula vazia = *colocar*; foto ocupada = *substituir* (a anterior
     volta a ficar disponível). O destino mostra o que vai acontecer antes de soltar.
   - Sem arrastar: botão direito na foto → *Substituir por outra foto…*, *Trocar com a posição
     anterior/seguinte*, *Mover para a página* (páginas com célula vazia).
6. **Gerar PDF** ou **Imprimir** (Ctrl+P). Se houver página sem fotos, o programa pergunta se
   deve ignorá-la. Células vazias, números e destaques da tela **não** saem no papel nem no PDF.
7. **Salvar exame** (Ctrl+S). O trabalho também é guardado automaticamente (rascunho).

## Retirar, remover e reorganizar
- **Retirar da página** (clique de novo na miniatura, ou Delete): sai da impressão e continua na
  galeria. Com **“Reorganizar ao retirar foto”** ligado (padrão), as fotos seguintes sobem para
  ocupar o espaço; desligado, **a célula fica vazia** para você preencher depois.
- **Remover da galeria deste exame** (botão direito na miniatura): tira do exame. Se a foto
  estiver na impressão, o programa avisa onde ela está. O arquivo original no computador **não** é apagado.
- Com **“Reorganizar ao retirar foto”** ligado, retirar uma foto fecha o espaço **só na página dela**.
- **Reorganizar todas as páginas** (painel de páginas, com confirmação) fecha os espaços de todas,
  puxando as fotos seguintes — é a única ação que move fotos de uma página para outra.
- **Desmarcar todas**: tira todas as fotos da impressão (a galeria fica igual).
- Tudo pode ser desfeito e refeito (Ctrl+Z / Ctrl+Y), inclusive Selecionar fotos e Reorganizar.

## Trocar o modelo de página
- Escolher outro modelo muda **só a página atual**; as outras páginas nunca são alteradas.
- Aumentar a capacidade mantém as fotos no lugar e cria posições vazias.
- Se o novo modelo comportar menos fotos, o programa pergunta: **levar as que sobram para uma
  nova página no final**, **retirá-las da impressão** (ficam na galeria) ou **cancelar**.
- **Em todas** aplica o modelo a todas as páginas (cada uma isoladamente), com a mesma pergunta.

## Limpar
- **Limpar página**: retira as fotos só da página atual (sem confirmação).
- **Limpar tudo**: retira as fotos de todas as páginas (pede confirmação).
- Nada é apagado da galeria, dos exames ou da pasta do Capture Pro. **Ctrl+Z** desfaz.

## Bom saber
- **Ordem de leitura**: esquerda → direita, de cima para baixo.
- A miniatura mostra **P2 · posição 4** quando a foto está na impressão, ou **disponível**.
- A barra inferior mostra, por exemplo: *10 foto(s) na composição · 2 página(s) · 2 espaço(s) disponível(is)*.
- **Recortar e girar** não alteram o arquivo; “Restaurar original” volta.
- Um ⚠ amarelo na foto indica resolução baixa para o tamanho impresso (não impede imprimir).
- Cada exame guarda cópia das fotos e da identidade visual usada.
- Exames feitos na versão 1.0 abrem normalmente, com a mesma impressão; ao salvar, o arquivo
  antigo fica guardado como `exame.formato1-backup.json` na pasta do exame.
- Se o computador desligar no meio do trabalho, ao abrir de novo o programa oferece **Recuperar**.

## Atalhos
| Tecla | Ação |
|---|---|
| Ctrl+N / Ctrl+O / Ctrl+S | Novo / Abrir / Salvar exame |
| Ctrl+P | Imprimir |
| Ctrl+Z / Ctrl+Y | Desfazer / Refazer |
| Clique na miniatura | Selecionar / desmarcar |
| Espaço (na galeria) | Incluir/retirar as miniaturas realçadas (Ctrl/Shift + clique realça várias) |
| Delete | Retirar da página (deixa a célula vazia; não apaga nada) |
| Esc (na prévia) | Cancelar a seleção da célula |
| Duplo clique | Ampliar a foto (roda do mouse = zoom; Esc fecha) |
| Ctrl + roda do mouse | Zoom da prévia |
| Page Up / Page Down | Página anterior / seguinte |

## Onde ficam os arquivos
- Exames: `Documentos\Galeria Pro Clínica\Exames\AAAA-MM-DD_NOME_xxxxxx\`
- PDFs: `Documentos\Galeria Pro Clínica\PDFs\` (configurável)
- Configurações e registro de eventos: `%APPDATA%\GaleriaProClinica\`

Desinstalar o programa **não apaga** exames nem configurações.

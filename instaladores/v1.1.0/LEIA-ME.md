# Galeria Pro Clínica 1.1.0 — notas da versão

Atualização conservadora da 1.0.0: mantém logo, identificação, rodapé, os cinco modelos
(1, 2, 6, 9, 12), PDF sem perda, prévia = PDF = impressão, salvamento/recuperação/histórico,
acompanhamento da pasta do Capture Pro e a preservação dos arquivos originais.

## O que mudou
1. **Galeria e impressão são independentes.** Reordenar a galeria (arrastar, ou ordenar por
   importação/nome/data de captura) não muda a impressão; mexer na impressão não muda a galeria.
2. **Células explícitas, com lacunas.** Cada foto ocupa uma posição (“P2 · posição 4”, mostrado na
   miniatura). Retirar uma foto deixa a célula **vazia**; as outras não se mexem.
3. **Selecionar fotos + Quantidade** (acima da galeria): seleciona o TOTAL indicado, na ordem
   visível da galeria, no modelo de “Fotos por página”. Ex.: 6 por página e 10 fotos → 6 + 4,
   com 2 células vazias. Se já houver composição: *Completar seleção até N*, *Refazer com N* ou
   *Cancelar*. Pedir mais do que há seleciona as existentes e informa.
4. **Seleção manual**: marcar uma foto ocupa a primeira célula vazia (ou a célula vazia
   selecionada na prévia); sem espaço, cria a página seguinte. Nunca duplica.
5. **Prévia interativa**: clique seleciona a célula; arrastar mostra o que vai acontecer
   (*Colocar*, *Mover*, *Trocar*, *Substituir*); da galeria para uma foto = substituir (a anterior
   volta a ficar disponível). Alternativas sem arrastar no botão direito: *Escolher foto para esta
   posição*, *Substituir por outra foto*, *Trocar com a posição anterior/seguinte*, *Mover para a página*.
6. **Reorganizar e preencher espaços** (painel de páginas): única ação que fecha lacunas.
7. **Troca de modelo** (“Aplicar nesta página” / “Aplicar em todas”) preserva a sequência; o
   excedente vai para as páginas seguintes; as outras páginas mantêm seus modelos; tudo desfazível.
8. **Barra de estado**: “10 foto(s) na composição · 2 página(s) · 2 espaço(s) disponível(is)”.
9. **Páginas vazias** na saída: o programa pergunta se deve ignorá-las (a numeração conta só as
   páginas impressas).
10. **Formato do exame 2**, com migração automática dos exames da 1.0 (mesma impressão) e cópia
    de segurança `exame.formato1-backup.json` antes da primeira gravação.

## Como atualizar a instalação existente
1. Feche o Galeria Pro Clínica (se estiver aberto, o instalador o encerra; o rascunho automático
   protege o trabalho).
2. Baixe `GaleriaProClinica-Setup-1.1.0.exe` e confira o SHA-256 (opcional):
   no PowerShell, `Get-FileHash .\GaleriaProClinica-Setup-1.1.0.exe` deve mostrar o valor de `SHA256SUMS.txt`.
3. Execute o instalador **por cima** da 1.0 (não é preciso desinstalar). Se aparecer “O Windows
   protegeu o computador”, clique em *Mais informações → Executar assim mesmo*.
4. Exames e configurações são mantidos; é criada a cópia `config.backup-antes-v1.1.0.json` em
   `%APPDATA%\GaleriaProClinica`.
5. Ao abrir um exame da 1.0, aparece o aviso de conversão; a impressão é a mesma. Ao salvar,
   o arquivo antigo fica guardado como `exame.formato1-backup.json`.

Observação: depois de salvo na 1.1, um exame não abre mais na 1.0 (o programa antigo recusa o
formato novo em vez de estragá-lo). O backup do formato 1 continua na pasta do exame.

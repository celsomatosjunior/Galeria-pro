# Galeria Pro Clínica 1.4.1 — data fixa no cabeçalho e novo “Sobre”

- **Data do exame sempre no mesmo lugar**: “Data: DD/MM/AAAA” fica presa à direita, alinhada com
  a borda direita das fotos, em todas as páginas — não importa o tamanho do nome do paciente.
  Nome muito longo é reduzido um pouco e, se preciso, encurtado com “…”, sem cobrir a data.
- **Sobre** (ícone “i”): novo texto de apresentação; a versão mostrada é sempre a instalada.

![Data na mesma posição com nomes diferentes](../../docs/cabecalho-data-fixa.png)

Mantém tudo da 1.4.0 (fotos reutilizáveis) e da 1.3.1 (sem piscadas).
Detalhes: [notas da versão](../../docs/NOTAS-DA-VERSAO-1.4.1.md) ·
[relatório de testes](../../docs/RELATORIO-DE-TESTES.md) · [manual](../../docs/MANUAL.md).

## Como atualizar
Feche o programa e execute `GaleriaProClinica-Setup-1.4.1.exe` por cima da versão instalada.
Exames e configurações são mantidos (cópia de segurança `config.backup-antes-v1.4.1.json`).

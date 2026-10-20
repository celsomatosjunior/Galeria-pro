# Relatório de testes — Galeria Pro Clínica 1.3.0 (20/10/2026)

Ambientes, separados: **Linux** (testes automatizados), **Wine** (Windows simulado, instalador e
programa compilados). **Windows real e impressora física: não testados nesta versão.**

## 1. Teste obrigatório de regressão (pedido da 1.3.0, seção 5)
Exame com 32 fotos (Linux, janela real com cliques nas miniaturas) e 46 fotos (programa instalado, Wine).

| Passo | Resultado |
|---|---|
| Montar P1 = 6 (6 fotos), P2 = 9 (9 fotos), P3 = 12 (12 fotos), página por página com “Nova página” | aprovado |
| 1–2. Alternar repetidamente entre as 3 páginas (botões e lista): cada uma conserva o seu modelo; o seletor mostra o modelo da página | aprovado (20 alternâncias) |
| 3–4. **Limpar página** 2: só ela esvazia (modelo 9 mantido); P1 e P3 intactas; galeria intacta; sem confirmação | aprovado |
| 5. **Ctrl+Z** restaura a página 2 | aprovado (atalho de teclado real no Linux) |
| 6. Acrescentar e retirar fotos manualmente: a foto nova entra na página atual; outras páginas intactas | aprovado |
| 7. Alterar o modelo de uma página (12 → 9; 6 → 12; 6 → 2): nenhuma outra página muda; pergunta sobre as excedentes (cancelar / retirar / nova página no final) | aprovado |
| 8–9. Salvar, fechar e reabrir: modelos 6/9/12, posições e espaços vazios preservados | aprovado |
| 10. PDF: 3 páginas com 6, 9 e 12 imagens, “Página X de 3” em cada uma; inspeção visual sem marcas da interface | aprovado |
| Piscadas: com o programa parado, a prévia não se redesenha (≤ 2 redesenhos em 2 s, ajuste à página e à largura) | aprovado |

Outros testes da 1.3: **Limpar tudo** pede confirmação (Não = nada muda; Sim = impressão vazia, galeria e
arquivos intactos; Ctrl+Z restaura); menu **Nova página ▾** oferece os 5 modelos; reduzir usa
primeiro os espaços vazios da página; excluir página leva as fotos para uma página nova no final.

## 2. Linux — total: 124 testes (123 aprovados como administrador + 1 de permissão aprovado como usuário comum)
Mantidos e aprovados os testes das versões anteriores (um clique, duplo clique, arrastar, substituir
e trocar, Selecionar fotos 10 em 6, acompanhamento do Capture Pro, PDF byte a byte, salvamento,
recuperação, exames da 1.0). Testes que exigiam a antiga transferência para a página seguinte
foram atualizados para o comportamento novo (a página seguinte nunca é alterada).

## 3. Wine 9.0 — instalador e programa 1.3.0
- Atualização 1.2.0 → 1.3.0 por cima: 21 arquivos de exames/configuração intactos (SHA-256),
  cópia `config.backup-antes-v1.3.0.json`, versão 1.3.0 no registro, arquivos instalados idênticos à distribuição.
- Autoteste do programa instalado: todos os passos aprovados (um clique, duplo clique, 6 manuais,
  10 em 6, trocar, retirar, PDF, repetição, e a regressão 6/9/12 completa com PDF [6, 9, 12]).
- Substitutos de `icuuc.dll`/`mscms.dll` só no ambiente Wine de teste; **não estão** no instalador.

## 4. NÃO testado
- Impressora física; Windows 10/11 real com mouse físico; arrastar físico; Capture Pro ao vivo.

# Galeria Pro Clínica 1.4.0 — fotografias reutilizáveis

Mantém tudo da 1.3.1 (inclusive a correção das piscadas): modelo próprio por página
(1, 2, 6, 9, 12), Nova página, Limpar página, Limpar tudo, arrastar e soltar, trocar,
substituir, reorganizar, desfazer/refazer, salvamento automático e recuperação, PDF sem perda
e impressão. A arquitetura não foi reescrita.

## O que mudou
1. **Uma foto da galeria pode ser usada ilimitadas vezes.** Cada clique na miniatura coloca a
   foto mais uma vez na página atual — inclusive várias vezes na mesma página e em páginas
   diferentes. Página cheia → página nova no final (como antes). O arquivo **não** é duplicado
   no disco: as células guardam a referência da foto.
2. **A galeria não marca mais as fotos usadas**: sem borda azul, sem ✔, sem número, sem escurecer.
   Só um texto discreto “usada N×” no rodapé da miniatura (o tooltip mostra as posições).
3. **Cada ocorrência é independente.** Para retirar uma: clique nela **na prévia** e tecle
   **Delete** (ou botão direito → *Retirar esta ocorrência da página*). As outras ocorrências da
   mesma foto ficam. Retirar todas de uma vez: botão direito na miniatura → *Retirar todas as
   ocorrências da impressão*.
4. **Arrastar na prévia** move/troca **aquela ocorrência**; arrastar da galeria para uma célula
   coloca mais uma ocorrência (célula vazia) ou substitui só aquela ocorrência (célula ocupada).
5. **Selecionar fotos** (automático) continua escolhendo fotos **diferentes**; a repetição é só manual.

## Mudanças necessárias em comandos antigos
- **Ampliar** passou para a **lupa** no canto da miniatura (e Enter, e o duplo clique na prévia).
  Motivo: cliques rápidos seguidos na mesma foto chegam ao programa como “duplo clique”; para que
  **dez cliques deem dez ocorrências** (critério desta versão), todo clique na miniatura acrescenta.
- **Delete na galeria** não retira mais nada (só explica como fazer): como a foto pode estar em
  várias células, retirar é feito na prévia, ocorrência por ocorrência.
- O botão “Desmarcar todas” passou a se chamar **Retirar todas** (mesma função, com confirmação).

## Compatibilidade
- Exames da 1.0–1.3 abrem normalmente, iguais.
- Exames **sem** foto repetida continuam no formato 2 (abrem também na 1.3).
- Exames **com** foto repetida gravam formato 3; a 1.3 recusa abri-los (pede atualização) em vez
  de perder as repetições.

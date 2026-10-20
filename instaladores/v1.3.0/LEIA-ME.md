# Galeria Pro Clínica 1.3.0 — notas da versão

Refinamento do fluxo de impressão, página por página (como no UltraCap). Mantém tudo da 1.2:
seleção com um clique, duplo clique para ampliar, arrastar e soltar, substituir e trocar,
acompanhamento do Capture Pro, logo, rodapé, PDF sem perda, salvamento automático e recuperação,
exames antigos. O formato do exame não muda.

## O que mudou
1. **Cada página tem o seu próprio modelo** (1, 2, 6, 9 ou 12), totalmente independente.
   Ex.: página 1 com 6, página 2 com 9, página 3 com 12. Ao voltar a uma página, o seletor mostra
   o modelo salvo dela.
2. **O seletor de modelo atua só na página atual.** Mudar a página 3 não altera as páginas 1 e 2.
3. **Reduzir o modelo nunca mexe nas outras páginas.** Se as fotos não couberem, o programa
   pergunta: *Levar para uma nova página no final*, *Retirar da impressão (ficam na galeria)* ou
   *Cancelar*. (Na 1.2, as excedentes iam para a página seguinte.)
4. **Barra de navegação**: ◀ Anterior · Página X de Y · Próxima ▶ · **Nova página ▾** (escolhendo o
   modelo da página nova) · **Modelo** da página atual · **Limpar página** · **Limpar tudo**.
5. **LIMPAR PÁGINA** retira as fotos só da página atual, sem confirmação. **LIMPAR TUDO** retira de
   todas as páginas, com confirmação. As fotos continuam na galeria, nos exames e na pasta do
   Capture Pro. **Ctrl+Z desfaz** as duas.
6. **Clicar numa foto da galeria coloca-a na página em que você está** (na primeira posição vazia
   dali em diante; sem espaço, cria uma página nova no final). Páginas anteriores não mudam.
7. **Retirar uma foto reorganiza só a página dela** (opção “Reorganizar ao retirar foto”).
   “Reorganizar todas as páginas” continua disponível, com confirmação.
8. **Excluir página** com fotos: devolver à galeria ou levar para uma página nova no final
   (as outras páginas não mudam).

## Como atualizar
Feche o programa e execute `GaleriaProClinica-Setup-1.3.0.exe` por cima da versão instalada.
Exames e configurações são mantidos (cópia de segurança `config.backup-antes-v1.3.0.json`).
A versão 1.2.0 continua disponível para download.

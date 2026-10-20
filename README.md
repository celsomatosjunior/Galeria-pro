# Galeria Pro Clínica 1.1

> ## ⬇️ Download — versão 1.1.0 (atual)
>
> **[GaleriaProClinica-Setup-1.1.0.exe](https://github.com/celsomatosjunior/Galeria-pro/raw/main/instaladores/v1.1.0/GaleriaProClinica-Setup-1.1.0.exe)** — instalador único, Windows 10/11 64 bits (22 MB).
> SHA-256: `7424bba8b271150d501d9c83e87b8db295404dcb68d7aeb9f362f1a0568216ce`
>
> Versão portátil (sem instalar): [GaleriaProClinica-Portatil-1.1.0.zip](https://github.com/celsomatosjunior/Galeria-pro/raw/main/instaladores/v1.1.0/GaleriaProClinica-Portatil-1.1.0.zip) — SHA-256: `6c078499ace1a302d5b4f04e76c19daee2c6d9a5f111114f6fc70251e5d09254`
>
> [Notas da versão e como atualizar](instaladores/v1.1.0/LEIA-ME.md) · [Manual](docs/MANUAL.md) · [Relatório de testes](docs/RELATORIO-DE-TESTES.md) · [Avisos de terceiros](instaladores/v1.1.0/AVISOS-DE-TERCEIROS.md)

Organiza as fotografias de exames, monta folhas A4 com a identidade visual da clínica (logo,
paciente, data e rodapé) e **imprime ou gera PDF**. Complementar ao **Capture Pro**: acompanha a
pasta de capturas, sem alterar aquele programa. Funciona **100% offline**: sem login, sem internet.

![Tela principal](docs/tela-principal.png)

## Novidades da 1.1
- **Galeria e impressão independentes**: ordenar a galeria não muda a impressão, e vice-versa.
- **Selecionar fotos + Quantidade** (total): ex. 6 por página e 10 fotos → 6 + 4, com 2 células vazias.
  Com composição existente: *Completar*, *Refazer* ou *Cancelar*.
- **Células com posição** (“P2 · posição 4”), **lacunas** ao retirar uma foto e
  **Reorganizar e preencher espaços** para fechá-las.
- **Arrastar** mostra o que vai acontecer (colocar, mover, trocar, substituir); tudo também pelo menu.
- Exames da 1.0 abrem com a mesma impressão (cópia de segurança do arquivo original ao salvar).

![Arrastar e substituir](docs/arrastar-substituir.png)

## Instalação
1. Baixe o instalador (link acima) e execute. Ele pede permissão de administrador.
2. Se o Windows mostrar “O Windows protegeu o computador” (sem assinatura digital paga):
   *Mais informações → Executar assim mesmo*.
3. **Atualizar**: execute o instalador novo por cima da versão anterior. Exames e configurações
   são mantidos (é criada uma cópia de segurança das configurações).
4. Desinstalar não apaga exames nem configurações.

Tudo vem incluído (não é preciso instalar Python nem outra ferramenta).

## Modelos de página
1 foto · 2 fotos (uma em cima da outra) · 6 fotos (2×3) · 9 fotos (3×3) · 12 fotos (3×4).
Modelos diferentes podem ser usados no mesmo exame. As fotos nunca são deformadas nem cortadas
automaticamente; no PDF entram sem perda (JPEG original byte a byte).

## Testes
106 testes automatizados (Linux), instalação/atualização 1.0 → 1.1 e autoteste do programa
instalado em Windows simulado (Wine). **Ainda não validado em Windows real nem em impressora
física** — ver o [relatório de testes](docs/RELATORIO-DE-TESTES.md).

---
Distribuição gratuita do instalador; código-fonte proprietário (ver [LICENCA.md](LICENCA.md)).

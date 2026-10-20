# Avisos de terceiros — Galeria Pro Clínica 1.2

O Galeria Pro Clínica é distribuído com os componentes abaixo, sem modificação. Os textos
completos das licenças estão na pasta `licencas\` da instalação.

| Componente | Versão | Licença | Uso |
|---|---|---|---|
| Python (CPython, build python-build-standalone) | 3.12.8 | PSF License Version 2 | Interpretador embutido |
| Qt 6 (via PySide6-Essentials) — QtCore, QtGui, QtWidgets, QtPrintSupport, QtSvg | 6.12.0 | GNU LGPL v3 | Interface, desenho, PDF e impressão |
| PySide6-Essentials / Shiboken6 | 6.12.0 | GNU LGPL v3 | Ligação Python–Qt |
| pypdf | 6.21.1 | BSD 3-Clause | Substituição sem perda das imagens dentro do PDF |
| Microsoft Visual C++ Runtime (msvcp140, vcruntime140…) | incluso no PySide6 | Licença de redistribuição da Microsoft | Bibliotecas de execução |

## Qt e PySide6 (LGPL v3)
As bibliotecas Qt/PySide6 são usadas como bibliotecas dinâmicas, em arquivos separados
(`Lib\site-packages\PySide6\*.dll`, `*.pyd`), sem modificação. O usuário pode substituí-las por
outras versões compatíveis. O código-fonte do Qt está em https://download.qt.io/ e o do
PySide6 em https://code.qt.io/cgit/pyside/pyside-setup.git/.

## Fontes e marcas
- Nenhuma fonte é distribuída: o programa usa as fontes já instaladas no Windows (Arial, Segoe UI).
- Ícones e ícone do aplicativo: desenho próprio deste projeto.
- Nenhuma marca, logotipo ou elemento visual de terceiros (inclusive dos sistemas usados como
  referência) é distribuído. A logo da clínica é escolhida pelo usuário nas Configurações.

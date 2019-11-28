---
layout: post
title:  "Pip freeze de dentro de um python shell"
category: Tutoriais
---

Como obter as coisas instaladas no environment de dentro de um python shell? É muito simples, basta rodar o seguinte comando:

``` python
try:
    from pip._internal.operations import freeze
except ImportError:  # pip < 10.0
    from pip.operations import freeze

x = freeze.freeze()
for p in x:
    print (p)
```
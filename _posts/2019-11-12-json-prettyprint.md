---
layout: post
title:  "Conferindo se um JSON está bem formado pelo terminal"
category: Tecnologia
---

Pode ser dificil visualizar se um arquivo JSON está estruturado corretamente só batendo o olho. Com o código abaixo, você pode verificar se o seu _arquivo.json_ está estruturado corretamente pela linha de comando.

```shell
cat seu_arquivo.json | python -m json.tool | pygmentize -l json
```

Até a próxima!
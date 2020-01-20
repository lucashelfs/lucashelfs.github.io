---
layout: post
title:  "Removendo um pedaço de um arquivo usando cut"
category: Tecnologia
published: True
---

Estava com um problema muito particular aqui, remover todas os primeiros 5 caracteres de todas as linhas de um arquivo. O arquivo era grande demais e quando tentava realizar essa operação simples utilizando Python o computador apresentava problemas de desempenho.

Para isso, recorri ao **cut**, uma ferramenta da linha de comando do Unix. Atualmente o **cut** é parte do pacote GNU coreutils.

Para resolver o problema em questão, utilizei o seguinte comando:

``` shell
cut -c6- meu_arquivo_gigante.csv > meu_arquivo_sem_os_5_primeiros.csv
```

Isso serve para imprimir cada uma das linhas, partindo do sexto caractere (a contagem começa partindo do 1). 

O _-c_ serve para sinalizar que estamos considerando caractere. 

O _>_ redireciona o output da saída para _meu_arquivo_sem_os_5_primeiros.csv_.

Mais referências podem ser encontradas [na página de manual do cut](http://man7.org/linux/man-pages/man1/cut.1.html "Man page do cut").

---
layout: post
title:  "Copiando milhares de arquivos pequenos"
category: Tecnologia
published: True
---

Recentemente, me deparei com uma tarefa aparentemente simples: transferir um diretório com 19GB de dados de um servidor para outro. Esse diretório possui milhares de arquivos com pequeno tamanho.

A solução natural para o problema seria a seguinte:

``` shell
scp -r meu_diretorio/ usuario@servidor:/novo_diretorio
```

A questão é ao utilizar **scp** é estabelecida uma nova conexão via **ssh** diversas vezes, o que deixa o processo muito demorado.

Uma solução para esse problema é utilizar o **rsync**  que cria apenas uma conexão e trata de sincronizar os dois diretórios. Caso haja um problema na conexão, **rsync** consegue lidar com os problemas.

O comando a ser utilizado é o seguinte:

``` shell
rsync -av -P carf_abjur/ jota@137.117.43.115:/sdd/carf
```

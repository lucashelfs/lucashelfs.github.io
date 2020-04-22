---
layout: post
title:  "Copiando milhares de arquivos pequenos - usando uma chave"
category: Tecnologia
published: True
---

Há algum tempo, coloquei aqui uma solução utilizando **rsync** para sincronizar dois diretórios, sendo um deles o de um servidor externo. Essa é a melhor saída para copiar um diretório que tenha um grande tamanho mas com milhares de arquivos pequenos.

E quando o servidor que vocẽ está tentando sincronizar é protegido com uma chave criptográfica? Daí o comando a ser utilizado é o seguinte:

``` shell
rsync --progress -avz -e "ssh -i sua_chave.pem" usuario@servidor:/pasta_com_muitos_arquivos/ .
```

Espero que o comando acima lhe seja útil em algum momento.
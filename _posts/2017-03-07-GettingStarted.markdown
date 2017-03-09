---
layout: post
title: Começando no Django-CMS
date:   2017-03-07 16:34:40 -0300
categories: django-cms python
---

Um começo no Django CMS, *versão 3.4.1*.

Instalação
==========

Crie um ambiente virtual e ative-o:

{% highlight bash %}
virtualenv env
source env/bin/activate
{% endhighlight %}


Baixe o instalador do Django-CMS:

{% highlight bash %}
pip install djangocms-installer
{% endhighlight %}


Crie e vá para um diretório onde ficará o projeto:

{% highlight bash %}
mkdir tutorial-project
cd tutorial-project
{% endhighlight %}


Crie um projeto de Django-CMS:

{% highlight bash %}
djangocms -f -p . meusite
{% endhighlight %}


Você pode rodar o projeto:

{% highlight bash %}
python manage.py runserver
{% endhighlight %}


Ele estará disponível em <http://localhost:8000/>


### Integração de apps

Primeiro, crie um app:

{% highlight bash %}
python manage.py startapp seuapp
{% endhighlight %}


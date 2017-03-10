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


O par de login padrão *(usuario/senha)* é: admin/admin


Ele estará disponível em <http://localhost:8000/>


### Integração de apps

Primeiro, crie um app:

{% highlight bash %}
python manage.py startapp meuapp
{% endhighlight %}

.......


Apphook
-------

O que é um apphook?
===================

Um apphook permite que você atribua um app de django para uma página fixa do seu site em CMS, você pode também configurar para tudo trabalhar de acordo com o namespace do seu app, como um projeto de Django qualquer.

Você cria uma página do DjangoCMS em branco e anexa nela o app desejado.


Para fazer um apphook do SeuApp no projeto de DjangoCMS, faça o seguinte.

Assumindo que você tem um app chamado MeuApp.

Crie um arquivo cms_apps.py na pasta da aplicação em CMS, o diretório deve ficar da seguinte maneira:

```
meusite
│   LEIAME.md
│
└── meuapp
│   │    migrations/
│   │    templtates/
│   │    __init__.py
│   │    admin.py
│   │    apps.py
│   │    forms.py
│   │    models.py
│   │    tests.py
│   │    urls.py
│   └─── views.py
│
└── meusite
    │    static/
    │    templates/
    │    __init__.py
    │    cms_apps.py
    │    settings.py
    │    urls.py
    └─── wsgi.py
```

No arquivo cms_apps.py, é necessário ter uma subclasse de *CMSApp* da seguinte maneira:

{% highlight python %}
from cms.app_base import CMSApp
from cms.apphook_pool import apphook_pool
from django.utils.translation import ugettext_lazy as _

class MeuApphook(CMSApp):
    name = _("Meu Apphook")
    app_name = "meuapp"  # caso seu app use namespaces

    def get_urls(self, page=None, language=None, **kwargs):
        return ["meuapp.urls"]       # replace this with the path to your application's URLs module

apphook_pool.register(MeuApphook)
{% endhighlight %}




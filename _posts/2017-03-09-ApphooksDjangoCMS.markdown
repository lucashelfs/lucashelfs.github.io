---
layout: post
title: "Django-CMS: Apphooks"
date:   2017-03-09 15:30:00 -0300
categories: django-cms python apphooks
---

Django-CMS: Apphooks
====================

O que é um apphook?
-------------------

Um apphook permite que você atribua um app de django para uma página fixa do seu site em CMS, você pode também configurar para tudo trabalhar de acordo com o namespace do seu app, como um projeto de Django qualquer.

Você cria uma página do DjangoCMS em branco e anexa nela o app desejado.


Para fazer um apphook do seu app no projeto de DjangoCMS, faça o seguinte.

{% highlight bash %}
python manage.py startapp meuapp
{% endhighlight %}

Assumindo que você criou um app chamado meuapp como acima e o configurou de acordo com a sua preferência.

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
        # return ["mysite.apps.joinus.urls"]

apphook_pool.register(MeuApphook)
{% endhighlight %}



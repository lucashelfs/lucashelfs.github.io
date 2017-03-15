---
layout: post
title: "Django-CMS: Apphooks"
date:   2017-03-14 11:56:00 -0300
categories: django-cms python menus
---


Django-CMS: Menus customizados
==============================

Para criar um menu personalizado para um app (meuapp) crie um arquivo *cms_menus.py* na pasta correspondente. Basicamente o que precisamos fazer é passar uma lista de nós que são anexados na árvore de hierarquia dos menus.

O arquivo deve conter algo como:

{% highlight python %}
from menus.base import NavigationNode
from menus.menu_pool import menu_pool
from django.utils.translation import ugettext_lazy as _
from cms.menu_bases import CMSAttachMenu
# from cms.menu_bases import Menu


class JoinUsMenu(CMSAttachMenu):

    name = _("Join-us menu")

    def get_nodes(self, request):
        nodes = []
        n = NavigationNode(_('Join us ROOTS'), "./", 1)
        n2 = NavigationNode(_('Join now'), "./now", 2)
        nodes.append(n)
        nodes.append(n2)
        return nodes

menu_pool.register_menu(JoinUsMenu)
{% endhighlight %}

O código acima se trata de um menu que pode ser anexado a alguma página do cms. Se usássemos a classe *Menu* de *cms.menu_bases* o menu seria fixo para todas as páginas.

O diretório deve ficar da seguinte maneira:

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
│   │    cms_menus.py
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




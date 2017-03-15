---
layout: post
title: "Django-CMS: Custom wizards"
date:   2017-03-15 10:00:00 -0300
categories: django-cms python menus
---


Django-CMS: Custom Wizards
==============================

O quê é um custom wizard?
-------------------------

Um apphook permite que crie páginas, usuários ou o quê for de sua preferência rapidamente usando o botão create da toolbar do CMS.


Como fazer?
-----------

Para criar um custom wizard para um app (meuapp) crie um arquivo *cms_wizards.py* na pasta correspondente. 

O arquivo deve conter algo como:

{% highlight python %}
	from cms.wizards.wizard_base import Wizard
	from cms.wizards.wizard_pool import wizard_pool

	from .forms import JoinUsWizardForm


	class JoinUsWizard(Wizard):
	    pass

	poll_wizard = JoinUsWizard(
	    title="JoinUs",
	    weight=200,
	    form=JoinUsWizardForm,
	    description="Quickly insert a new JoinUs",
	)

	wizard_pool.register(poll_wizard)
{% endhighlight %}

O código acima se trata de um form que também precisa ser criado. 

O arquivo deve conter um Model form de algum modelo de sua aplicação, algo como:

{% highlight python %}
	class JoinUsWizardForm(ModelForm):
	    class Meta:
	        model = JoinUs
	        exclude = []
{% endhighlight %}

Precisa também definir o método *get_absolute_url* no model utilizado. 

{% highlight python %}
from django.core.urlresolvers import reverse

    def get_absolute_url(self):
        return reverse('joinus:success')
{% endhighlight %}

Note que é necessário a existência de uma url correta nos templates de joinus e configurada corretamente nas *urls.py* de joinus. No caso acima o nome da url é *success*.

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
│   │    cms_wizards.py
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

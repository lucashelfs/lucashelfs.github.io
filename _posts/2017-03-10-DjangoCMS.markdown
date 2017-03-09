---
layout: post
title:  Começando no Django-CMS
date:   2017-03-10 17:00:00 -0300
categories: django-cms python
---

Criar um ambiente virtual e ativá-lo:

{% highlight %}
virtualenv env
source env/bin/activate
{% endhighlight %}

Instalador do Django-CMS:

pip install djangocms-installer


Criar e ir para um diretório

mkdir tutorial-project
cd tutorial-project


Criar um projeto de Django-CMS:

djangocms -f -p . mysite


To add new posts, simply add a file in the `_posts` directory that follows the convention `YYYY-MM-DD-name-of-post.ext` and includes the necessary front matter. Take a look at the source for this post to get an idea about how it works.


{% highlight ruby %}
def print_hi(name)
  puts "Hi, #{name}"
end
print_hi('Tom')
#=> prints 'Hi, Tom' to STDOUT.
{% endhighlight %}

Check out the [Jekyll docs][jekyll-docs] for more info on how to get the most out of Jekyll. File all bugs/feature requests at [Jekyll’s GitHub repo][jekyll-gh]. If you have questions, you can ask them on [Jekyll Talk][jekyll-talk].

[jekyll-docs]: https://jekyllrb.com/docs/home
[jekyll-gh]:   https://github.com/jekyll/jekyll
[jekyll-talk]: https://talk.jekyllrb.com/

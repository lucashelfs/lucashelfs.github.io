---
layout: post
title:  "Encontrando diretórios vazios"
category: Tecnologia
published: True
---

Neste post dou um exemplo de como deve ser feita a __docstring__ em uma função de Python.

As __Docstrings__ são strings que inserimos dentro de nosso código com o intuito de fornecer uma explicação melhor sobre seu funcionamento. Serve muito bem naqueles momentos que você escreveu um código e gostaria de saber exatamente o que aquela determinada função ou classe faz, esse momento sempre chega.

As explicações sobre a convenção podem ser vistas [aqui](https://www.python.org/dev/peps/pep-0257/).

Abaixo segue um exemplo de como escrever uma __docstring__ e como acessar seus conteúdos.

``` python
def count_letter(content, letter):
	"""Count the number of times `letter` appears in `content`.

	Args:
	content (str): The string to search.
	letter (str): The letter to search for.

	Returns:
	int

	# Add a section detailing what errors might be raised
	Raises:
	ValueError: If `letter` is not a one-character string.
	"""
	if (not isinstance(letter, str)) or len(letter) != 1:
		raise ValueError('`letter` must be a single character string.')
	return len([char for char in content if char == letter])
```

Você pode acessar os conteúdos da sua docstring:

``` python
help(count_letter)
```

ou também da seguinte maneira:

``` python
f = count_letter
print(f.__doc__)
``` 

Sempre que possível, use __docstrings__!
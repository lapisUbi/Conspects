
Наследование шаблонов (Template Inheritance) - Это инструмент, позволяющий избежать дублирования HTML-кода на разных страницах сайта.

```
{% extends "base.html" %}
{% block content %}Home Page{% endblock %}
```



Создается базовый шаблон (например, `base.html`), который содержит общие элементы для всего сайта (шапку, подвал, навигационную панель).

base.html
```
<html>
<head>
		<title>{% block title %}{% endblock %} </title>
		</head>
		<body>
			<h1>Website</h1>
			{% block content %}
			{% endblock %}
		</body>
	</html>
```

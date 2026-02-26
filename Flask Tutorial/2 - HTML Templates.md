```
from flask import Flask, redirect, url_for, render_template

app = Flask(__name__)

@app.route("/")
def home():
	return render_template("index.html", content=name)
	
	
if __name__ == "__main__":
	app.run()
```

Позволяет подключать HTML и CSS файлы
```
from flask import Flask, render_template
```

Какой именно файл рендерить
``render_template("index.html")``

Можно передавать переменные из Python в HTML через именованные аргументы
`render_template("index.html", content=name`)


Внутри проекта создать папку и внутри файл /templates/index.html

```
<html>
<head>
		<title>Home page </title>
		</head>
		<body>
			<h1>Home Page!</h1>
			<p>{{content}}</p>
		</body>
	</html>
```

{{content}} - переменная


## Логика внутри шаблона (Jinja2)


В шаблонах можно писать логические конструкции, используя синтаксис **{% %}**:

- **Циклы**: Позволяют перебирать списки или выполнять действия несколько раз.
    - Пример: `{% for x in content %}` ... `{% endfor %}`.
- **Условия**: Позволяют отображать контент выборочно.
    - Поддерживаются `if`, `elif` и `else`.
    - Любое условие должно заканчиваться тегом `{% endif %}`.
- **Ограничения**: Хотя в шаблонах можно использовать Python-подобный код (например, `range()` или оператор остатка от деления `%`), этот язык шаблонов не поддерживает абсолютно все возможности чистого Python.


```
<html>
<head>
		<title>Home page </title>
		</head>
		<body>
			<h1>Home Page!</h1>
			{% for x in range(10) %}
				{% if x % 2 == 1 %}
					<p>{{x}}</p>
				{% endif %}
			{% endfor %}
		</body>
	</html>
```

![[Pasted image 20260226100921.png]]


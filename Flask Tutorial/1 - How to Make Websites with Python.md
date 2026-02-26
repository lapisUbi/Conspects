## Initialization

from flask import Flask

```
from flask import Flask

app = Flask(__name__)

if __name__ == "__main__":
	app.run()

```
**__name__** — это специальная переменная Python, которая представляет имя текущего файла. Она сообщает Flask, где искать связанные ресурсы, такие как шаблоны HTML и статические файлы (изображения, CSS).

**if __name__ == "__main__":**: Это стандартное условие Python, которое проверяет, **запускается ли файл напрямую**. Если вы импортируете этот файл как модуль в другую программу, код внутри этого условия (запуск сервера) не выполнится.


## Routing

```
from flask import Flask

app = Flask(__name__)

@app.route("/")
def home():
	return "<h1>HELLO<h1> world!"
	
@app.route("/<name>")
def user(name):
	return f"<h1>HELLO<h1> {name}!"
	
if __name__ == "__main__":
	app.run()

```

@app.route("/") - Дефолтный раут, при вписании домена, или ip 


```
@app.route("/<name>")
def user(name):
	return f"<h1>HELLO<h1> {name}!"
```

**Динамические пути**: Можно передавать параметры через URL, используя синтаксис `<name>`. Значение из URL автоматически передается в функцию как аргумент.


## Redirects

```
from flask import Flask, redirect, url_for

app = Flask(__name__)

@app.route("/")
def home():
	return "<h1>HELLO<h1> world!"
	
@app.route("/<name>")
def user(name):git remote add origin https://github.com/lapisUbi/Conspects.git
	return f"<h1>HELLO<h1> {name}!"
	
@app.route("/admin")
def user():
	return redirect(url_for("home"))
	
if __name__ == "__main__":
	app.run()

```

Этот фрагмент кода выполняет **перенаправление (редирект)** пользователя с одной страницы на другую. Разберем каждую строку на основе предоставленных источников:

```
from flask import Flask, redirect, url_for
```

Добавление библиотек

```
@app.route("/admin")
def user():
	return redirect(url_for("home"))
```

**redirect()**: Эта функция (её нужно предварительно импортировать из `flask`) отправляет пользователя на другой адрес.

   url_for `("home"):` Это важный момент. Вместо того чтобы вручную писать путь (например,  /), используется функция `url_for`, которая принимает имя функции (в данном случае `"home"`) и автоматически находит связанный с ней URL-адрес.

   В результате, когда кто-то пытается зайти на страницу `/admin`, приложение мгновенно перенаправит его на страницу, за которую отвечает функция `home`.

```
from flask import Flask, redirect, url_for

app = Flask(__name__)

@app.route("/")
def home():
	return "<h1>HELLO<h1> world!"
	
@app.route("/<name>")
def user(name):git remote add origin https://github.com/lapisUbi/Conspects.git
	return f"<h1>HELLO<h1> {name}!"
	
@app.route("/admin")
def user():
	return redirect(url_for("user", name="Admin!"))
	
if __name__ == "__main__":
	app.run()

```

Редирект в страницу админа /admin , сайт перенаправляет на /Admin

```
@app.route("/admin")
def user():
	return redirect(url_for("user", name="Admin!"))
```
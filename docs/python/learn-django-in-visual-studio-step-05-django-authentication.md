---
title: 'Руководство по Django в Visual Studio, шаг 5: аутентификация'
titleSuffix: ''
description: Пошаговое руководство по основам Django в контексте проектов Visual Studio с описанием функций аутентификации, предоставляемых в шаблонах веб-проектов Django.
ms.date: 11/19/2018
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: ea708c1721d85468d99a0ccc327f378042579f85
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99942494"
---
# <a name="step-5-authenticate-users-in-django"></a>Шаг 5. Аутентификация пользователей в Django

**Предыдущий шаг. [Использование полного шаблона веб-проекта Django](learn-django-in-visual-studio-step-04-full-django-project-template.md)**

Так как аутентификация является распространенным требованием для веб-приложений, в шаблоне "Веб-проект Django" предусмотрен базовый поток проверки подлинности. (В шаблоне "Веб-проект опроса Django", который описан в шаге 6 этого руководства, также реализован такой поток.) При использовании любого из шаблонов проектов Django в Visual Studio в файл *settings.py* проекта Django включаются все модули, необходимые для проверки подлинности.

На этом шаге вы научитесь делать следующее:

> [!div class="checklist"]
> - Как использовать поток проверки подлинности, предоставляемый в шаблонах Visual Studio (шаг 5.1)

## <a name="step-5-1-use-the-authentication-flow"></a>Шаг 5-1. Использование потока проверки подлинности

Далее приведены инструкции по тестированию потока проверки подлинности и описаны связанные части проекта:

1. Если вы еще не выполнили инструкции по созданию учетной записи суперпользователя (администратора) в файле *readme.html* в корневом каталоге проекта, сделайте это сейчас.

1. Запустите приложение из Visual Studio. Для этого последовательно выберите **Отладка** > **Начать отладку** (**F5**). Когда приложение появится в браузере, обратите внимание, что элемент управления **входом** отображается в правом верхнем углу панели навигации.

    ![Элемент управления входом на странице приложения "Веб-проект Django"](media/django/step05-login-control.png)

1. Откройте *templates/app/layout.html* и обратите внимание, что элемент `<div class="navbar ...>` содержит тег `{% include app/loginpartial.html %}`. Тег `{% include %}` указывает системе шаблонов Django получить содержимое включенного на этом этапе файла в шаблоне.

1. Откройте *templates/app/loginpartial.html* и посмотрите, как используется условный тег `{% if user.is_authenticated %}` и тег `{% else %}` для отображения разных элементов пользовательского интерфейса в зависимости от того, прошел ли пользователь проверку подлинности:

    ```html
    {% if user.is_authenticated %}
    <form id="logoutForm" action="/logout" method="post" class="navbar-right">
        {% csrf_token %}
        <ul class="nav navbar-nav navbar-right">
            <li><span class="navbar-brand">Hello {{ user.username }}!</span></li>
            <li><a href="javascript:document.getElementById('logoutForm').submit()">Log off</a></li>
        </ul>
    </form>

    {% else %}

    <ul class="nav navbar-nav navbar-right">
        <li><a href="{% url 'login' %}">Log in</a></li>
    </ul>

    {% endif %}
    ```

1. Так как при первом запуске приложения пользователи, прошедшие аутентификацию, отсутствуют, код шаблона отображает только ссылку входа по относительному пути "login". В соответствии с заданным значением в *urls.py*, как показано в предыдущем разделе, этот маршрут сопоставляется с представлением `django.contrib.auth.views.login`. Это представление получает следующие данные:

    ```python
    {
        'template_name': 'app/login.html',
        'authentication_form': app.forms.BootstrapAuthenticationForm,
        'extra_context':
        {
            'title': 'Log in',
            'year': datetime.now().year,
        }
    }
    ```

    `template_name` определяет шаблон для страницы входа. В нашем случае это *templates/app/login.html*. Свойство `extra_context` добавляется к данным контекста, по умолчанию переданным в шаблон. Наконец, `authentication_form` указывает класс формы для использования с именем для входа. В шаблоне это свойство отображается как объект `form`. Значение по умолчанию — `AuthenticationForm` (из `django.contrib.auth.views`). В шаблоне проекта Visual Studio вместо него используется форма, определенная в файле приложения *forms.py*:

    ```python
    from django import forms
    from django.contrib.auth.forms import AuthenticationForm
    from django.utils.translation import ugettext_lazy as _

    class BootstrapAuthenticationForm(AuthenticationForm):
        """Authentication form which uses boostrap CSS."""
        username = forms.CharField(max_length=254,
                                   widget=forms.TextInput({
                                       'class': 'form-control',
                                       'placeholder': 'User name'}))
        password = forms.CharField(label=_("Password"),
                                   widget=forms.PasswordInput({
                                       'class': 'form-control',
                                       'placeholder':'Password'}))
    ```

    Как видим, этот класс формы является производным от `AuthenticationForm`. В частности он переопределяет поля имени пользователя и пароля для добавления текста заполнителя. Шаблон Visual Studio включает этот явный код, основываясь на предположении, что вам потребуется настроить форму, например добавить функцию для проверки надежности пароля.

1. При переходе на страницу входа в приложении отображается шаблон *login.html*. Переменные `{{ form.username }}` и `{{ form.password }}` отвечают за отображение форм `CharField` из `BootstrapAuthenticationForm`. Кроме того, есть встроенный раздел для отображения сведений об ошибках проверки и готовый элемент для входа в социальные сети на тот случай, если вы решите добавить эти службы.

    ```html
    {% extends "app/layout.html" %}

    {% block content %}

    <h2>{{ title }}</h2>
    <div class="row">
        <div class="col-md-8">
            <section id="loginForm">
                <form action="." method="post" class="form-horizontal">
                    {% csrf_token %}
                    <h4>Use a local account to log in.</h4>
                    <hr />
                    <div class="form-group">
                        <label for="id_username" class="col-md-2 control-label">User name</label>
                        <div class="col-md-10">
                            {{ form.username }}
                        </div>
                    </div>
                    <div class="form-group">
                        <label for="id_password" class="col-md-2 control-label">Password</label>
                        <div class="col-md-10">
                            {{ form.password }}
                        </div>
                    </div>
                    <div class="form-group">
                        <div class="col-md-offset-2 col-md-10">
                            <input type="hidden" name="next" value="/" />
                            <input type="submit" value="Log in" class="btn btn-default" />
                        </div>
                    </div>
                    {% if form.errors %}
                    <p class="validation-summary-errors">Please enter a correct user name and password.</p>
                    {% endif %}
                </form>
            </section>
        </div>
        <div class="col-md-4">
            <section id="socialLoginForm"></section>
        </div>
    </div>

    {% endblock %}
    ```

1. При отправке формы в Django выполняется аутентификация учетных данных (например, учетных данных суперпользователя). Если аутентификация не будет пройдена, вы останетесь на текущей странице, но для `form.errors` будет задано значение true. При успешной аутентификации Django выполняет переход по относительному URL-адресу в следующее поле, `<input type="hidden" name="next" value="/" />`. В нашем случае это домашняя страница (`/`).

1. Теперь, когда снова отображается домашняя страница, при отображении шаблона *loginpartial.html* свойство `user.is_authenticated` имеет значение true. В результате отображается сообщение **Hello (имя пользователя)** и элемент управления **выходом**. С помощью `user.is_authenticated` можно проверить аутентификацию в других частях приложения.

    ![Приветственное сообщение и элемент управления выходом на странице приложения "Веб-проект Django"](media/django/step05-logoff-control.png)

1. Чтобы проверить, авторизован ли прошедший аутентификацию пользователь для доступа к определенным ресурсам, необходимо получить от базы данных конкретные разрешения. Дополнительные сведения см. в статье об [использовании системы аутентификации Django](https://docs.djangoproject.com/en/2.0/topics/auth/default/#permissions-and-authorization) (документация Django).

1. В частности суперпользователь или администратор авторизованы для доступа к встроенным интерфейсам администратора Django с использованием относительных URL-адресов /admin/ и /admin/doc/. Включить их можно так:

    1. Установите в своей среде пакет docutils Python. Для этого удобно добавить docutils в файл *requirements.txt*, а затем в **обозревателе решений** развернуть узел **Среды Python**, щелкнуть правой кнопкой мыши используемую среду и выбрать **Установить из файла requirements.txt**.

    1. Откройте файл *urls.py* проекта Django и удалите комментарии по умолчанию из следующих записей:

        ```python
        from django.conf.urls import include
        from django.contrib import admin
        admin.autodiscover()

        # ...
        urlpatterns = [
            # ...
            url(r'^admin/doc/', include('django.contrib.admindocs.urls')),
            url(r'^admin/', include(admin.site.urls)),
        ]
        ```

    1. В файле *settings.py* проекта Django перейдите к коллекции `INSTALLED_APPS` и добавьте `'django.contrib.admindocs'`.

    1. Когда вы перезапускаете приложение, можно перейти по адресам /admin/ и admin/doc/, чтобы выполнять такие задачи, как создание дополнительных учетных записей пользователей.

        ![Интерфейс администратора Django](media/django/step05-administrator-interface.png)

1. Последняя часть потока аутентификации — это процедура выхода. Как видим в *loginpartial.html*, ссылка **Выход** просто отвечает за выполнение запроса POST по относительному URL-адресу /login. Затем запрос обрабатывается встроенным представлением `django.contrib.auth.views.logout`. В этом представлении не отображается пользовательский интерфейс. Просто выполняется переход к домашней странице (как показано в файле *urls.py* для шаблона ^logout$). Если вам нужно, чтобы отображалась страница выхода из системы, сначала измените шаблон URL-адреса следующим образом, добавив свойство template_name и удалив свойство next_page:

    ```python
    url(r'^logout$',
        django.contrib.auth.views.logout,
        {
            'template_name': 'app/loggedoff.html',
            # 'next_page': '/',
        },
        name='logout')
    ```

    Затем создайте *templates/app/loggedoff.html* со следующим (минимальным) содержимым:

    ```html
    {% extends "app/layout.html" %}
    {% block content %}
    <h3>You have been logged off</h3>
    {% endblock %}
    ```

    Выводится следующий результат:

    ![Добавленная страница выхода](media/django/step05-logged-off-page.png)

1. По завершении остановите работу сервера и снова зафиксируйте изменения в системе управления версиями.

### <a name="question-what-is-the-purpose-of-the--csrf_token--tag-that-appears-in-the-form-elements"></a>Вопрос. Для чего нужен тег {% csrf_token %}, который отображается в элементах \<form\>?

Ответ. Тег `{% csrf_token %}` содержит встроенную в Django функцию [защиты от подделки межсайтовых запросов (CSRF)](https://docs.djangoproject.com/en/2.0/ref/csrf/) (документация Django). Обычно этот тег добавляется в каждый элемент, для которого используются методы запросов POST, PUT или DELETE, такой как форма. С помощью функции отображения в шаблон (`render`) затем вставляются необходимые средства защиты.

## <a name="next-steps"></a>Следующие шаги

> [!div class="nextstepaction"]
> [Использование шаблона веб-проекта Django для опросов](learn-django-in-visual-studio-step-06-polls-django-web-project-template.md)

## <a name="go-deeper"></a>Дополнительные подробности

- [User authentication in Django](https://docs.djangoproject.com/en/2.0/topics/auth/) (Аутентификация пользователя в Django) (docs.djangoproject.com)
- Исходный код учебника на GitHub: [Microsoft/python-sample-vs-learning-django](https://github.com/Microsoft/python-sample-vs-learning-django)

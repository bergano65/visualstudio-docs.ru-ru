---
title: 'Руководство по Django в Visual Studio, шаг 4: шаблон веб-проекта'
titleSuffix: ''
description: Пошаговое руководство по основам Django в контексте проектов Visual Studio с описанием функций, предоставляемых в шаблоне веб-проекта Django.
ms.date: 11/19/2018
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 3c0a0f0f4e009d689a69e840b31281e65bc5a0e2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99942559"
---
# <a name="step-4-use-the-full-django-web-project-template"></a>Шаг 4. Использование полного шаблона веб-проекта Django

**Предыдущий шаг: [Обработка статических файлов, добавление страниц и использование наследования шаблонов](learn-django-in-visual-studio-step-03-serve-static-files-and-add-pages.md)**

Теперь, когда вы ознакомились с основами Django, создав в Visual Studio приложение на основе шаблона "Пустой веб-проект Django", вам будет легче создать более полное приложение с помощью шаблона "Веб-проект Django".

На этом этапе вы сделаете следующее:

> [!div class="checklist"]
> - создадите более полное веб-приложение Django с помощью шаблона "Веб-проект Django" и изучите структуру проекта (шаг 4.1);
> - узнаете, какие представления и шаблоны страниц создаются при использовании шаблона проекта, в котором содержится три страницы, наследованные от шаблона базовой страницы, и используются статические библиотеки JavaScript, такие как jQuery и Bootstrap (ша 4.2);
> - узнаете, как реализуется маршрутизация URL-адресов, предоставляемая шаблоном (шаг 4.3).

В шаблоне также предусмотрена обычная аутентификация, которая рассматривается на шаге 5.

## <a name="step-4-1-create-a-project-from-the-template"></a>Шаг 4.1. Создание проекта на основе шаблона

1. В Visual Studio перейдите к **обозревателю решений**, щелкните правой кнопкой мыши решение **LearningDjango**, созданное ранее в рамках этого руководства, и выберите **Добавить** > **Новый проект**. (Если же вы хотите использовать новое решение, вместо этого выберите **Файл** > **Создать** > **Проект**.)

1. В диалоговом окне создания проекта найдите и выберите шаблон **Веб-проект Django**, присвойте проекту имя DjangoWeb и нажмите кнопку **ОК**.

1. Так как шаблон также включает файл *requirements.txt*, в Visual Studio запрашивается расположение для установки этих зависимостей. Выберите параметр **Install into a virtual environment** (Установка в виртуальном окружении) и в диалоговом окне **Добавление виртуального окружения** выберите **Создать**, чтобы принять значения по умолчанию.

1. Когда в Visual Studio завершится настройка виртуального окружения, следуйте инструкциям в отображаемом файле *readme.html*, чтобы создать суперпользователя Django (т. е. администратора). Щелкните правой кнопкой мыши проект Visual Studio и выберите команду **Python** > **Создать суперпользователя Django**, а затем следуйте инструкциям на экране. Обязательно запишите имя пользователя и пароль, так как они понадобятся для тестирования аутентификации в приложении.

1. Назначьте проект **DjangoWeb** в качестве проекта по умолчанию для решения Visual Studio. Для этого в **обозревателе решений** щелкните правой кнопкой мыши имя проекта и выберите **Назначить запускаемым проектом**. Запускаемый проект, выделенный полужирным шрифтом, выполняется при запуске отладчика.

    ![Обозреватель решений с выбранным в качестве запускаемого проектом DjangoWeb](media/django/step04-second-project-in-solution-set-as-startup-project.png)

1. Выберите **Отладка** > **Начать отладку** (**F5**) или нажмите кнопку **Веб-сервер** на панели инструментов, чтобы запустить сервер:

    ![Кнопка панели инструментов запуска веб-сервера в Visual Studio](media/django/run-web-server-toolbar-button.png)

1. Приложение, созданное с помощью шаблона, содержит три страницы — домашнюю страницу, а также страницы со сведениями и контактными данными. Вы можете перемещаться между ними, используя панель навигации. Выделите пару минут, чтобы просмотреть части приложения. Чтобы пройти аутентификацию в приложении с помощью команды **Вход**, используйте учетные данные суперпользователя, созданные ранее.

    ![Полное представление приложения веб-проекта Django в браузере](media/django/step04-full-app-desktop-view.png)

1. Приложение, созданное с помощью шаблона "Веб-проект Django", использует созданный на основе Bootstrap адаптивный макет, учитывающий форм-факторы мобильных устройств. Чтобы увидеть, как работает адаптивность, уменьшите размер окна браузера так, чтобы содержимое отображалось по вертикали, а панель навигации была в виде значка меню.

    ![Мобильное (уменьшенное) представление приложения веб-проекта Django](media/django/step04-full-app-mobile-view.png)

1. Вы можете оставить приложение запущенным и пройти следующие разделы.

    Чтобы остановить работу приложения и [зафиксировать изменения в системе управления исходным кодом](learn-django-in-visual-studio-step-02-create-an-app.md#commit-to-source-control), сначала откройте страницу **Изменения** в **Team Explorer**, щелкните правой кнопкой мыши папку виртуального окружения (возможно, **env**) и выберите **Игнорировать эти локальные элементы**.

### <a name="examine-what-the-template-creates"></a>Просмотр элементов, созданных с помощью шаблона

В общем на основе шаблона "Веб-проект Django" создается следующая структура:

- Файлы в корневом каталоге проекта:
  - *manage.py* — административная служебная программа Django;
  - *db.sqlite3* — база данных SQLite по умолчанию;
  - *requirements.txt* — файл, который содержит зависимость от Django 1.x;
  - *readme.html* — файл, который отображается в Visual Studio после создания проекта. Как упоминалось в предыдущем разделе, следуйте приведенным ниже инструкциям, чтобы создать учетную запись суперпользователя (администратора) для приложения.
- В папке *app* содержатся все файлы приложения, включая представления, модели, тесты, формы, шаблоны и статические файлы (см. шаг 4–2). Обычно эту папку нужно переименовать, указав более уникальное имя приложения.
- В папке *DjangoWeb* проекта Django содержатся стандартные файлы проекта: *\_\_init\_\_.py*, *settings.py*, *urls.py* и *wsgi.py*. На основе шаблона в *settings.py* уже задана конфигурация для файлов базы данных и приложения. Также в *urls.py* уже указаны пути ко всем страницам приложения, включая форму входа.

### <a name="question-is-it-possible-to-share-a-virtual-environment-between-visual-studio-projects"></a>Вопрос. Можно ли предоставлять проектам Visual Studio общий доступ к виртуальному окружению?

Ответ. Да, но при этом учитывайте, что, вероятно, со временем для разных проектов будут использоваться разные пакеты. Таким образом, в общем виртуальном окружении будут содержаться все пакеты для всех проектов, в которых используется окружение.

Чтобы все равно использовать существующее виртуальное окружение, сделайте следующее:

1. Когда в Visual Studio будет предложено установить зависимости, выберите вариант **Я установлю их самостоятельно**.
1. В **обозревателе решений** щелкните правой кнопкой мыши узел **Окружения Python** и выберите **Добавить существующее виртуальное окружение**.
1. Перейдите к папке виртуального окружения и выберите ее. Затем нажмите кнопку **ОК**.

## <a name="step-4-2-understand-the-views-and-page-templates-created-by-the-project-template"></a>Шаг 4.2. Сведения о представлениях и шаблонах страниц, созданных с использованием шаблона проекта

При запуске проекта вы увидите, что приложение содержит три представления: домашняя страница, а также страницы со сведениями и контактными данными. Код этих представлений хранится в папке *app/views*. Каждая функция представления просто вызывает `django.shortcuts.render` с путем к шаблону и простым объектом словаря. Например, страница сведений обрабатывается функцией `about`:

```python
def about(request):
    """Renders the about page."""
    assert isinstance(request, HttpRequest)
    return render(
        request,
        'app/about.html',
        {
            'title':'About',
            'message':'Your application description page.',
            'year':datetime.now().year,
        }
    )
```

Шаблоны хранятся в папке *templates/app* приложения. Как правило, *app* нужно переименовать, указав имя фактического приложения. Файл базового шаблона (*layout.html*) является самым большим. В нем содержатся ссылки на все необходимые статические файлы (JavaScript и CSS), определяется блок content, переопределяемый другими страницами, и предоставляется еще один блок с именем scripts. Эти области показаны в следующем фрагменте файла *layout.html*:

```html
<!DOCTYPE html>
<html>
<head>
    <meta charset="utf-8" />

    <!-- Define a viewport for Bootstrap's responsive rendering -->
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>{{ title }} - My Django Application</title>

    {% load staticfiles %}
    <link rel="stylesheet" type="text/css" href="{% static 'app/content/bootstrap.min.css' %}" />
    <link rel="stylesheet" type="text/css" href="{% static 'app/content/site.css' %}" />
    <script src="{% static 'app/scripts/modernizr-2.6.2.js' %}"></script>
</head>
<body>
    <!-- Navbar omitted -->

    <div class="container body-content">

<!-- "content" block that pages are expected to override -->
{% block content %}{% endblock %}
        <hr/>
        <footer>
            <p>&copy; {{ year }} - My Django Application</p>
        </footer>
    </div>

<!-- Additional scripts; use the "scripts" block to add page-specific scripts.  -->
    <script src="{% static 'app/scripts/jquery-1.10.2.js' %}"></script>
    <script src="{% static 'app/scripts/bootstrap.js' %}"></script>
    <script src="{% static 'app/scripts/respond.js' %}"></script>
{% block scripts %}{% endblock %}

</body>
</html>
```

Каждый шаблон отдельной страницы (*about.html*, *contact.html* и *index.html*) дополняет основной шаблон *layout.html*. *about.html* — это самый простой шаблон, в котором отображаются теги `{% extends %}` и `{% block content %}`.

```html
{% extends "app/layout.html" %}

{% block content %}

<h2>{{ title }}.</h2>
<h3>{{ message }}</h3>

<p>Use this area to provide additional information.</p>

{% endblock %}
```

Шаблоны *index.html* и *contact.html* имеют такую же структуру, но предоставляют больше содержимого в блоке content.

В папке *templates/app* есть еще и файл четвертой страницы *login.html* вместе с файлом *loginpartial.html*, указанным в *layout.html* с помощью `{% include %}`. Эти файлы шаблона рассматриваются на шаге 5 с инструкциями по аутентификации.

### <a name="question-can--block--and--endblock--be-indented-in-the-django-page-template"></a>Вопрос. Можно ли добавить отступ перед тегами {% block %} и {% endblock %} в шаблоне страницы Django?

Ответ. Да, шаблоны страниц Django будут работать без шибок, если добавить отступ перед тегами блоков, например, чтобы выровнять их в соответствующих родительских элементах. Они не отделяются отступом в шаблонах страниц, созданных на основе шаблона проекта Visual Studio, чтобы вы могли четко видеть, где они расположены.

## <a name="step-4-3-understand-the-url-routing-created-by-the-template"></a>Шаг 4.3. Сведения о маршрутизации URL-адресов, создаваемой на основе шаблона

Файл *urls.py* проекта Django, созданный на основе шаблона "Веб-проект Django", содержит такой код:

```python
from datetime import datetime
from django.conf.urls import url
import django.contrib.auth.views

import app.forms
import app.views

urlpatterns = [
    url(r'^$', app.views.home, name='home'),
    url(r'^contact$', app.views.contact, name='contact'),
    url(r'^about$', app.views.about, name='about'),
    url(r'^login/$',
        django.contrib.auth.views.login,
        {
            'template_name': 'app/login.html',
            'authentication_form': app.forms.BootstrapAuthenticationForm,
            'extra_context':
            {
                'title': 'Log in',
                'year': datetime.now().year,
            }
        },
        name='login'),
    url(r'^logout$',
        django.contrib.auth.views.logout,
        {
            'next_page': '/',
        },
        name='logout'),
]
```

Первые три шаблона URL-адресов сопоставляются непосредственно с представлениями `home`, `contact` и `about` в файле *views.py* приложения. А в шаблонах `^login/$` и `^logout$` используются встроенные представления Django вместо представлений, определяемых приложением. Также в вызовах метода `url` содержатся дополнительные данные для настройки представления. Эти вызовы рассматриваются на шаге 5.

### <a name="question-in-the-project-i-created-why-does-the-about-url-pattern-uses-about-instead-of-about-as-shown-here"></a>Вопрос. Почему в созданном мной проекте в шаблоне URL-адреса about используется ^about, а не ^about$, как показано в этом разделе?

Ответ. Отсутствие символа $ в конце регулярного выражения — это просто ошибка, которая встречается во многих версиях шаблона проекта. Шаблон URL-адреса для страницы сведений работает без ошибок. Но без символа $ в конце он также соответствует таким URL-адресам: about=django, about09876, aboutoflaughter и т. д. В этом примере символ $ в конце выражения используется для создания URL-адресов, соответствующих *только* about.

## <a name="next-steps"></a>Дальнейшие действия

> [!div class="nextstepaction"]
> [Аутентификация пользователей в Django](learn-django-in-visual-studio-step-05-django-authentication.md)

## <a name="go-deeper"></a>Дополнительные подробности

- [Развертывание веб-приложения в Службе приложений Azure](publishing-python-web-applications-to-azure-from-visual-studio.md)
- [Writing your first Django app, part 4 - forms and generic views](https://docs.djangoproject.com/en/2.0/intro/tutorial04/) (Написание первого приложения Django. Часть 4 — формы и универсальные представления) (docs.djangoproject.com)
- Руководство по исходному коду на сайте GitHub: [Microsoft/python-sample-vs-learning-django](https://github.com/Microsoft/python-sample-vs-learning-django)

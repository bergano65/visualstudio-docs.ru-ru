---
title: Шаблон веб-проекта Django для Python | Документы Майкрософт
description: Обзор шаблонов веб-приложений, написанных на языке Python с использованием платформы Django, в Visual Studio.
ms.custom: ''
ms.date: 07/13/2017
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-python
dev_langs:
- python
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.author: kraigb
manager: ghogen
ms.workload:
- python
- data-science
ms.openlocfilehash: 941ec5191e440be95d66da983508de36cef6d4fd
ms.sourcegitcommit: 29ef88fc7d1511f05e32e9c6e7433e184514330d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/28/2018
---
# <a name="django-web-project-template"></a>Шаблон веб-проекта Django

[Django](https://www.djangoproject.com/) — это высокоуровневая платформа Python для быстрого создания безопасных и масштабируемых веб-систем. Поддержка Python в Visual Studio предоставляет шаблон проекта для настройки структуры веб-приложения на основе Django. Чтобы использовать этот шаблон в Visual Studio, выберите **Файл > Создать > Проект**, выполните поиск по запросу "Django" и выберите шаблон **Веб-проект Django**. Созданный проект содержит стандартный код и базу данных SQLite по умолчанию. Шаблон **Пустой веб-проект Django** выглядит так же, но не включает базу данных.

Visual Studio предоставляет полную поддержку технологии IntelliSense для проектов Django.

- Переменные контекста, передаваемые в шаблоне:

    ![IntelliSense для переменных контекста](media/template-django-intellisense.png)

- Добавление тегов и фильтрация для обоих встроенных и определяемых пользователем элементов:

    ![IntelliSense для тегов и фильтров](media/template-django-intellisense-filter.png)

- Цветовая маркировка синтаксиса для внедренного CSS и JavaScript:

    ![IntelliSense для CSS](media/template-django-intellisense-css.png)

    ![IntelliSense для JavaScript](media/template-django-intellisense-js.png)

Также Visual Studio предоставляет полную [поддержку отладки](debugging-python-in-visual-studio.md) для проектов Django: 

![Точки останова](media/template-django-debugging.png)

Обычно проекты Django управляются с помощью файла `manage.py`, являющегося предположением, которому следует Visual Studio. Если прекратить использовать этот файл в качестве точки входа, это нарушит работу файла проекта. В этом случае нужно [повторно создать проект из существующих файлов](managing-python-projects-in-visual-studio.md#creating-a-project-from-existing-files), не помечая его как проект Django.

## <a name="django-management-console"></a>Консоль управления Django

Консоль управления Django можно открыть несколькими разными командами в меню **Проект** или щелкнув проект правой кнопкой мыши в обозревателе решений.

- **Открыть оболочку Django...** открывает оболочку в контексте приложения, где вы можете управлять моделями.

    ![Консоль](media/template-django-console-shell.png)

- **Django Sync DB** (База данных синхронизации Django) выполняет в интерактивном окне команду `manage.py syncdb`:

    ![Консоль](media/template-django-console-sync-db.png)

- **Collect Static** (Сбор статических файлов) выполняет `manage.py collectstatic --noinput` для копирования всех статических файлов в путь, указанный параметром `STATIC_ROOT` в файле `settings.py`. Обратите внимание, что при [публикации в Microsoft Azure](python-web-application-project-templates.md#publishing-to-azure-app-service) статические файлы автоматически сохраняются в процессе публикации.

    ![Консоль](media/template-django-console-collect-static.png)

- **Validate** (Проверка) выполняет `manage.py validate`, чтобы получить сообщения обо всех ошибках проверки установленных моделей, заданных параметром `INSTALLED_APPS` в файле `settings.py`:

    ![Консоль](media/template-django-console-validate.png)
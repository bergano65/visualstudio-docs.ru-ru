---
title: Шаблон веб-проекта Django для Python
description: Обзор шаблонов веб-приложений, написанных на языке Python с использованием платформы Django, в Visual Studio.
ms.date: 07/03/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- python
- data-science
ms.openlocfilehash: e847322b1bbbefec5c7013d7e90475e08f42694b
ms.sourcegitcommit: 1c2ed640512ba613b3bbbc9ce348e28be6ca3e45
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/03/2018
ms.locfileid: "39499547"
---
# <a name="django-web-project-template"></a>Шаблон веб-проекта Django

[Django](https://www.djangoproject.com/) — это высокоуровневая платформа Python для быстрого создания безопасных и масштабируемых веб-систем. Благодаря поддержке Python в Visual Studio предоставляется несколько шаблонов проектов для настройки структуры веб-приложения на основе Django. Чтобы использовать шаблон в Visual Studio, последовательно выберите **Файл** > **Создать** > **Проект**, выполните поиск по слову "Django" и выберите шаблон **Пустой веб-проект Django**, **Веб-проект Django** или **Веб-проект опроса Django**. Инструкции по использованию всех шаблонов см. в [руководстве по изучению Django](learn-django-in-visual-studio-step-01-project-and-solution.md).

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

Обычно проекты Django управляются с помощью файла *manage.py*, являющегося предположением, которому следует Visual Studio. Если прекратить использовать этот файл в качестве точки входа, это нарушит работу файла проекта. В этом случае нужно [повторно создать проект из существующих файлов](managing-python-projects-in-visual-studio.md#create-a-project-from-existing-files), не помечая его как проект Django.

## <a name="django-management-console"></a>Консоль управления Django

Консоль управления Django можно открыть несколькими разными командами в меню **Проект** или щелкнув проект правой кнопкой мыши в **обозревателе решений**.

- **Открыть оболочку Django** открывает оболочку в контексте приложения, где вы можете управлять моделями.

    ![Консоль](media/template-django-console-shell.png)

- **Django Sync DB** (База данных синхронизации Django) выполняет в **интерактивном** окне команду `manage.py syncdb`:

    ![Консоль](media/template-django-console-sync-db.png)

- **Собирать статические файлы** выполняет `manage.py collectstatic --noinput` для копирования всех статических файлов в путь, указанный параметром `STATIC_ROOT` в файле *settings.py*. При [публикации в Службе приложений Azure](publishing-python-web-applications-to-azure-from-visual-studio.md) статические файлы автоматически сохраняются в процессе публикации.

    ![Консоль](media/template-django-console-collect-static.png)

- **Проверка** выполняет `manage.py validate`, чтобы получить сообщения о всех ошибках проверки установленных моделей, заданных параметром `INSTALLED_APPS` в файле *settings.py*:

    ![Консоль](media/template-django-console-validate.png)

## <a name="see-also"></a>См. также

- [Руководство по изучению Django](learn-django-in-visual-studio-step-01-project-and-solution.md)
- [Публикация в службу приложений Azure](publishing-python-web-applications-to-azure-from-visual-studio.md)
---
title: "Шаблон веб-проекта Django в Инструментах Python для Visual Studio | Документация Майкрософт"
ms.custom: 
ms.date: 3/7/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c479be58-13eb-4d77-9a27-c97ddc290963
caps.latest.revision: 1
author: kraigb
ms.author: kraigb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: a42f5a30375192c89c9984e40ba0104da98d7253
ms.openlocfilehash: 7f65641fbf15edfe16931badc19602a0fc773bff
ms.lasthandoff: 03/07/2017

---

# <a name="django-web-project-template"></a>Шаблон веб-проекта Django

[Django](https://www.djangoproject.com/) — это высокоуровневая платформа Python для быстрого создания безопасных и масштабируемых веб-систем. Инструменты Python для Visual Studio (PTVS) предоставляют шаблон проекта для настройки структуры веб-приложения на основе Django. Чтобы использовать этот шаблон в Visual Studio, выберите **Файл > Новый > Проект**, выполните поиск по запросу Django и выберите шаблон "Веб-проект Django". Созданный проект будет содержать стандартный код и базу данных SQLite по умолчанию. Шаблон "Пустой веб-проект Django" выглядит так же, но не включает базу данных.

PTVS предоставляет полную поддержку технологии IntelliSense для проектов Django.

- Переменные контекста, передаваемые в шаблоне:

    ![IntelliSense для переменных контекста](media/template-django-intellisense.png)

- Добавление тегов и фильтрация для обоих встроенных и определяемых пользователем элементов:

    ![IntelliSense для тегов и фильтров](media/template-django-intellisense-filter.png)

- Цветовая маркировка синтаксиса для внедренного CSS и JavaScript:

    ![IntelliSense для CSS](media/template-django-intellisense-css.png)

    ![IntelliSense для JavaScript](media/template-django-intellisense-js.png)


Также PTVS предоставляет полную [поддержку отладки](debugging.md) для проектов Django: 

![Точки останова](media/template-django-debugging.png)

## <a name="django-management-console"></a>Консоль управления Django

Консоль управления Django можно открыть несколькими разными командами в меню **Проект** или щелкнув проект правой кнопкой мыши в обозревателе решений.

- **Open Django Shell...** (Открыть оболочку Django...) открывает оболочку в контексте приложения, в которой вы можете управлять моделями:

    ![Консоль](media/template-django-console-shell.png)

- **Django Sync DB** (База данных синхронизации Django) выполняет в интерактивном окне команду `manage.py syncdb`:

    ![Консоль](media/template-django-console-sync-db.png)

- **Collect Static** (Сбор статических файлов) выполняет `manage.py collectstatic --noinput` для копирования всех статических файлов в путь, указанный параметром `STATIC_ROOT` в файле `settings.py`. Обратите внимание, что при [публикации в Microsoft Azure](template-web.md#publishing-to-azure-app-service) статические файлы автоматически сохраняются в процессе публикации.

    ![Консоль](media/template-django-console-collect-static.png)

- **Validate** (Проверка) выполняет `manage.py validate`, чтобы получить сообщения обо всех ошибках проверки установленных моделей, заданных параметром `INSTALLED_APPS` в файле `settings.py`:

    ![Консоль](media/template-django-console-validate.png)

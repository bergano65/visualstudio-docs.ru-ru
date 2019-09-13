---
title: начало работы с Python | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-python
ms.topic: conceptual
ms.assetid: 33f4f6fb-0ae4-4234-9df2-531f2d3af17f
caps.latest.revision: 13
author: kraigb
ms.author: kraigb
manager: jillfra
ms.openlocfilehash: 5c5cea89b337f4da586ba4ca1954e49b96c84638
ms.sourcegitcommit: 3cda0d58c5cf1985122b8977b33a171c7359f324
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/29/2019
ms.locfileid: "70154948"
---
# <a name="getting-started-with-python"></a>Начало работы с Python
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Инструменты Python для Visual Studio (PTVS) — это бесплатный подключаемый модуль с [открытым исходным кодом](https://github.com/Microsoft/ptvs) для Visual Studio, который является мощным процессом разработки Python.  
  
## <a name="python-the-language"></a>Язык Python.
  
Python — это популярный язык программирования, который используется многими университетами, специалистами, разработчиками приложений, пользователями, посвященными и профессиональным разработчикам, работающим над приложениями, веб-сайтами и облачными службами.

Язык программирования Python:
  
- Надежность.
- Обычно это удобно при написании сценариев для быстрых программ, сценариев приложений, настольных приложений, веб-серверов, веб-служб и научных вычислений.
- Легкий для понимания; хорошая архитектура, упрощающая написание качественного кода (многие университеты используют его для начальных курсов обучения программированию).
- Гибкие возможности, поддерживающие императивные, функциональные и объектно-ориентированные стили программирования.
- Бесплатно и с открытым кодом.
- Хорошо работает на всех основных операционных системах.  
- Поддерживается многими бесплатными, полезными и хорошо спроектированными библиотеками.  
- Поддерживается множеством документации, примерами и надежным сообществом разработчиков.  

Чтобы узнать больше о языке, начните с [Python для начинающих](https://www.python.org/about/gettingstarted/) на Python.org.

Чтобы установить Python, посетите [https://www.python.org/download/](https://www.python.org/download/).

## <a name="python-tools-for-visual-studio"></a>Python Tools for Visual Studio
  
Инструменты Python для Visual Studio, который можно установить из [VisualStudio.com](https://www.visualstudio.com/explore/python-vs), предоставляет следующие возможности.  
  
- Поддержка нескольких интерпретаторов: различные версии CPython, IronPython и IPython.  
- Система проектов, которая неявно получает структуру папок кода Python и обеспечивает явное управление, позволяя определять код приложения, тестовый код, веб-страницы, JavaScript, скрипты сборки и т. д.  
- Шаблоны проектов для консольных приложений, веб-приложений, Azure, обработки и анализа данных и других типов проектов.    
- Пакет Azure SDK для Python (см. ниже)    
- Широкие возможности редактирования и понимания кода, включая раскраску синтаксических конструкций, автозавершение для всего кода и библиотек, справку по сигнатурам, представление классов, переход к определению, поиск всех ссылок, рефакторинг и т. д.    
- Интерактивное окно (REPL)
- IPython с визуализацией данных.
- Поддержка IronPython, а также .NET и WPF.    
- Широкие возможности отладки без проекта Visual Studio, вложение в существующий исполняемый файл, смешанный режим отладки, удаленная отладка для Windows, Linux и Mac и отладка в интерактивном окне.   
- Средства профилирования.  
- Средства тестирования.  
  
Используйте следующие ресурсы для начала работы:

- [Руководство по установке](https://github.com/Microsoft/PTVS/wiki/PTVS-Installation)    
- [Короткие видеоролики по началу работы и углубленному рассмотрению](https://www.youtube.com/playlist?list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff)  
- Демонстрация установки и возможностей (27 минут)](https://www.youtube.com/watch?v=JNNAOypc6Ek)  
- [Документация](https://github.com/Microsoft/PTVS/wiki)  

Обратите внимание, что Visual Studio в настоящее время не предоставляет средств для создания автономного исполняемого файла с помощью Python, что по сути означает программу с внедренным интерпретатором Python. Но предназначенные для выполнения этой задачи средства можно найти в сообществе Python, как описано на сайте [StackOverflow](http://stackoverflow.com/questions/5458048/how-to-make-a-python-script-standalone-executable-to-run-without-any-dependency). CPython также можно внедрять в приложение машинного кода. Об этом можно узнать в записи блога [Using CPython's Embeddable Zip File](https://devblogs.microsoft.com/python/cpython-embeddable-zip-file/) (Использование внедряемого ZIP-файла CPython).
  
## <a name="building-ui-with-python"></a>Создание пользовательского интерфейса с помощью Python  

Основным предложением для создания пользовательского интерфейса с помощью Python является [проект Qt](https://www.qt.io/qt-for-application-development/)с привязками для Python, известными как [PySide (официальная привязка)](http://wiki.qt.io/PySide) (также см. раздел [загрузки PySide](https://download.qt.io/official_releases/pyside/.)) и [PyQt](https://wiki.python.org/moin/PyQt). В настоящее время поддержки Python в Visual Studio не включает какие-либо конкретные средства для разработки пользовательского интерфейса.

## <a name="azure-sdk-for-python"></a>Пакет Azure SDK для Python
  
Пакет Azure SDK для Python — это удобное средство для использования служб Microsoft Azure и управления ими. Оно поддерживает ОС Windows, Mac и Linux. Подробные сведения см. в перечисленных ниже ресурсах. 

- Чтобы установить пакет SDK, используйте [индекс пакета Python](https://pypi.python.org/pypi/azure) или следуйте инструкциям по [установке Python и пакета SDK](https://docs.microsoft.com/azure/python/python-sdk-azure-install) в документации Azure. 
- В [Центре разработчиков пакета Azure SDK для Python](https://azure.microsoft.com/develop/python/) содержится много полезных сведений, начиная с описания установки и заканчивая документацией с учебниками.  Описание некоторых особенностей  
- Практические руководства
  - [Хранилище BLOB-объектов](https://azure.microsoft.com/develop/python/how-to-guides/blob-service/)  
  - [Очередь хранилища](https://azure.microsoft.com/develop/python/how-to-guides/queue-service/)  
  - [Таблица хранилища](https://azure.microsoft.com/develop/python/how-to-guides/table-service/)  
  - [Очереди служебной шины](https://azure.microsoft.com/develop/python/how-to-guides/service-bus-queues/)
  - [Разделы и подписки, связанные со служебной шиной Service Bus](https://azure.microsoft.com/develop/python/how-to-guides/service-bus-topics/) 
  - [Управление службами](https://azure.microsoft.com/develop/python/how-to-guides/service-management/)  

## <a name="scientific-computing"></a>Научные вычисления

В дополнение ко всем библиотекам научных данных Python Инструменты Python для Visual Studio поддерживают среды IPython и IPython Notebook, которые можно разместить в Azure.

Мы рекомендуем получить среду IPython и библиотеки научных вычислений (matplotlib, scipy, numpy и т. д.) из [Калифорнийского университета в Ирвайне](http://www.lfd.uci.edu/~gohlke/pythonlibs/#scipy-stack).  
  
## <a name="see-also"></a>См. также  

[Начало работы с PTVS. Настройка Начало работы Visual Studio](../python/getting-started-with-ptvs-setting-up-visual-studio.md)
[с помощью PTVS: Начните программировать (проекты)](../python/getting-started-with-ptvs-start-coding-projects.md)
[начало работы с PTVS: Редактирование кода](../python/getting-started-with-ptvs-editing-code.md)
НачалоработыспомощьюPTVS[: Отладка](../python/getting-started-with-ptvs-debugging.md)
начало работыспомощьюPTVS:[ Интерактивный](../python/getting-started-with-ptvs-interactive-python.md)начало работы Python
[с PTVS: Создание веб-сайта в Azure](../python/getting-started-with-ptvs-building-a-website-in-azure.md)

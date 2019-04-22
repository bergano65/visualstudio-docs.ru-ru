---
title: Приступая к работе с Python | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-python
ms.topic: conceptual
ms.assetid: 33f4f6fb-0ae4-4234-9df2-531f2d3af17f
caps.latest.revision: 13
author: kraigb
ms.author: kraigb
manager: jillfra
ms.openlocfilehash: 9c18ae2731d92e6d128d13e7687bac77ae76dc8a
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59648459"
---
# <a name="getting-started-with-python"></a>Начало работы с Python
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Инструменты Python для Visual Studio (PTVS), — это бесплатный, [открытый](https://github.com/Microsoft/ptvs) подключаемый модуль для Visual Studio, который получить мощные Разработка на Python.  
  
## <a name="python-the-language"></a>Язык Python.
  
Python — это популярный язык программирования, который используется многими университеты, ученые, авторами сценариев приложений, непрофессиональных разработчиков и профессиональных разработчиков, работа приложений, веб-сайты и облачные службы.

Язык программирования — Python:
  
- Надежность.
- Обычно полезно для сценариев быстрого программ, сценариев приложений, классических приложений, веб-серверы, веб-служб и научные вычисления.
- Легкий для понимания; хорошая архитектура, упрощающая написание качественного кода (многие университеты используют его для начальных курсов обучения программированию).
- Гибкая, императивный, функционального и объектно ориентированного программирования стилями.
- Бесплатно и с открытым кодом.
- Хорошо работает во всех основных операционных системах.  
- Поддерживает многие бесплатные, удобные и хорошо спроектированной библиотеки.  
- Поддерживается множество документации, образцов и широким сообществом разработчиков.  

Дополнительные сведения о языке, начинаться с [Python для начинающих](https://www.python.org/about/gettingstarted/) на сайте python.org.

Для установки Python, сам посетите [ https://www.python.org/download/ ](https://www.python.org/download/).

## <a name="python-tools-for-visual-studio"></a>Python Tools for Visual Studio
  
Инструменты Python для Visual Studio, которые можно установить из [visualstudio.com](https://www.visualstudio.com/explore/python-vs), предоставляют следующие возможности:  
  
- Поддержка нескольких интерпретаторов: различные версии CPython, IronPython и IPython.  
- Система проектов, которая неявно получает структуру папок кода Python и обеспечивает явное управление, позволяя определять код приложения, тестовый код, веб-страницы, JavaScript, скрипты сборки и т. д.  
- Шаблоны проектов для консольных приложений, веб-приложений, Azure, обработки и анализа данных и других типов проектов.    
- Azure SDK для Python (см. ниже)    
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
- Демонстрация установки и возможностей (27 минут)])https://www.youtube.com/watch?v=JNNAOypc6Ek)  
- [Документация](https://github.com/Microsoft/PTVS/wiki)  

Обратите внимание, что Visual Studio в настоящее время предоставляет средства для создания отдельный исполняемый файл с помощью Python, который по сути означает, что программа с внедренным интерпретатором Python. Но предназначенные для выполнения этой задачи средства можно найти в сообществе Python, как описано на сайте [StackOverflow](http://stackoverflow.com/questions/5458048/how-to-make-a-python-script-standalone-executable-to-run-without-any-dependency). CPython также можно внедрять в приложение машинного кода. Об этом можно узнать в записи блога [Using CPython's Embeddable Zip File](https://devblogs.microsoft.com/python/cpython-embeddable-zip-file/) (Использование внедряемого ZIP-файла CPython).
  
## <a name="building-ui-with-python"></a>Создание пользовательского интерфейса с помощью Python  

Основные предложения, для создания пользовательского интерфейса с помощью Python — [Qt Project](https://www.qt.io/qt-for-application-development/), с привязками для Python, известный как [PySide (официальная привязка)](http://wiki.qt.io/PySide) (также см. в разделе [для скачивания PySide](https://download.qt.io/official_releases/pyside/.)) и [PyQt](https://wiki.python.org/moin/PyQt). В настоящее время поддержки Python в Visual Studio не включает какие-либо конкретные средства для разработки пользовательского интерфейса.

## <a name="azure-sdk-for-python"></a>Пакет Azure SDK для Python
  
Пакет Azure SDK для Python — это удобное средство для использования служб Microsoft Azure и управления ими. Оно поддерживает ОС Windows, Mac и Linux. Подробные сведения см. в перечисленных ниже ресурсах. 

- Чтобы установить пакет SDK, используйте [индекс пакета Python](https://pypi.python.org/pypi/azure) или следуйте инструкциям по [установке Python и пакета SDK](https://azure.microsoft.com/documentation/articles/python-how-to-install/) в документации Azure. 
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

[Начало работы с PTVS. Настройка Visual Studio](../python/getting-started-with-ptvs-setting-up-visual-studio.md)
[начало работы с PTVS: Приступаем к написанию кода (проекты)](../python/getting-started-with-ptvs-start-coding-projects.md)
[начало работы с PTVS: Редактирование кода](../python/getting-started-with-ptvs-editing-code.md)
[начало работы с PTVS: Отладка](../python/getting-started-with-ptvs-debugging.md)
[начало работы с PTVS: Интерактивный Python](../python/getting-started-with-ptvs-interactive-python.md)
[начало работы с PTVS: Создание веб-сайта в Azure](../python/getting-started-with-ptvs-building-a-website-in-azure.md)

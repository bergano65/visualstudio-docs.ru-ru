---
title: Начало работы с Python (ru) Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-python
ms.topic: conceptual
ms.assetid: 33f4f6fb-0ae4-4234-9df2-531f2d3af17f
caps.latest.revision: 13
author: kraigb
ms.author: kraigb
manager: jillfra
ms.openlocfilehash: 97d60fe31f838c4cc497701f4560dc426ebc1cc9
ms.sourcegitcommit: 054815dc9821c3ea219ae6f31ebd9cd2dc8f6af5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/02/2020
ms.locfileid: "80543977"
---
# <a name="getting-started-with-python"></a>Начало работы с Python
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Python Tools for Visual Studio (PTVS) — это бесплатный плагин с [открытым исходным кодом](https://github.com/Microsoft/ptvs) для Visual Studio, который является мощным опытом разработки Python.  
  
## <a name="python-the-language"></a>Язык Python.
  
Python является популярным языком программирования, который используется многими университетами, учеными, разработчиками приложений, случайными разработчиками и профессиональными разработчиками, работающими над приложениями, веб-сайтами и облачными службами.

В качестве языка программирования Python:
  
- Надежность.
- Как правило, полезно для быстрого разработки сценариев, скриптов приложений, настольных приложений, веб-серверов, веб-служб и научных вычислений.
- Легкий для понимания; хорошая архитектура, упрощающая написание качественного кода (многие университеты используют его для начальных курсов обучения программированию).
- Гибкие, поддерживающие императивные, функциональные и объектно-ориентированные стили программирования.
- Бесплатно и с открытым кодом.
- Работает хорошо на всех основных операционных системах.  
- Поддерживается множеством бесплатных, полезных и хорошо продуманных библиотек.  
- Поддерживается большим количеством документации, образцов и сильного сообщества разработчиков.  

Чтобы узнать больше о языке, начните с [Python для начинающих](https://www.python.org/about/gettingstarted/) на python.org.

Чтобы установить Python [https://www.python.org/download/](https://www.python.org/download/)себя, посетите .

## <a name="python-tools-for-visual-studio"></a>Средства Python для Visual Studio
  
Python Tools for Visual Studio, который можно установить из [visualstudio.com,](https://www.visualstudio.com/explore/python-vs)предоставляют следующие функции:  
  
- Поддержка нескольких интерпретаторов: различные версии CPython, IronPython и IPython.  
- Система проектов, которая неявно получает структуру папок кода Python и обеспечивает явное управление, позволяя определять код приложения, тестовый код, веб-страницы, JavaScript, скрипты сборки и т. д.  
- Шаблоны проектов для консольных приложений, веб-приложений, Azure, обработки и анализа данных и других типов проектов.    
- Azure SDK для python (см. ниже)    
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
- Установка и особенности демо (27 мин) » (https://www.youtube.com/watch?v=JNNAOypc6Ek)  
- [Документация](https://github.com/Microsoft/PTVS/wiki)  

Обратите внимание, что Visual Studio в настоящее время не предоставляет средств для создания автономного исполнителя с помощью Python, что по существу означает программу со встроенным переводчиком Python. Но предназначенные для выполнения этой задачи средства можно найти в сообществе Python, как описано на сайте [StackOverflow](https://stackoverflow.com/questions/5458048/how-to-make-a-python-script-standalone-executable-to-run-without-any-dependency). CPython также можно внедрять в приложение машинного кода. Об этом можно узнать в записи блога [Using CPython's Embeddable Zip File](https://devblogs.microsoft.com/python/cpython-embeddable-zip-file/) (Использование внедряемого ZIP-файла CPython).
  
## <a name="building-ui-with-python"></a>Создание uI с Python  

Основным предложением для создания uI с Python является [проект «Зт»](https://www.qt.io/qt-for-application-development/)с привязками для Python, известный как [PySide (официальная привязка)](https://wiki.qt.io/PySide) (также см. [PySide загрузки)](https://download.qt.io/official_releases/pyside/.)и [Py't](https://wiki.python.org/moin/PyQt). В настоящее время поддержки Python в Visual Studio не включает какие-либо конкретные средства для разработки пользовательского интерфейса.

## <a name="azure-sdk-for-python"></a>SDK Azure для Python
  
Пакет Azure SDK для Python — это удобное средство для использования служб Microsoft Azure и управления ими. Оно поддерживает ОС Windows, Mac и Linux. Подробные сведения см. в перечисленных ниже ресурсах. 

- Чтобы установить пакет SDK, используйте [индекс пакета Python](https://pypi.python.org/pypi/azure) или следуйте инструкциям по [установке Python и пакета SDK](/azure/developer/python/azure-sdk-install) в документации Azure. 
- В [Центре разработчиков пакета Azure SDK для Python](https://azure.microsoft.com/develop/python/) содержится много полезных сведений, начиная с описания установки и заканчивая документацией с учебниками.  Описание некоторых особенностей  
- Практические руководства
  - [Хранение Blob](https://azure.microsoft.com/develop/python/how-to-guides/blob-service/)  
  - [Очередь службы хранилища](https://azure.microsoft.com/develop/python/how-to-guides/queue-service/)  
  - [Таблица хранения](https://azure.microsoft.com/develop/python/how-to-guides/table-service/)  
  - [Как использовать очереди служебной шины](https://azure.microsoft.com/develop/python/how-to-guides/service-bus-queues/)
  - [Сервис Автобус Темы / Подписки](https://azure.microsoft.com/develop/python/how-to-guides/service-bus-topics/) 
  - [Управление обслуживанием](https://azure.microsoft.com/develop/python/how-to-guides/service-management/)  

## <a name="scientific-computing"></a>Научные вычисления

В дополнение ко всем библиотекам научных данных Python Инструменты Python для Visual Studio поддерживают среды IPython и IPython Notebook, которые можно разместить в Azure.

Мы рекомендуем получить среду IPython и библиотеки научных вычислений (matplotlib, scipy, numpy и т. д.) из [Калифорнийского университета в Ирвайне](https://www.lfd.uci.edu/~gohlke/pythonlibs/#scipy-stack).  
  
## <a name="see-also"></a>См. также:  

[Начало работы с PTVS: Настройка визуальной студии](../python/getting-started-with-ptvs-setting-up-visual-studio.md)
[Начало работы с PTVS: Начало кодирования (проекты)](../python/getting-started-with-ptvs-start-coding-projects.md)
[Начало работы с PTVS: Редактирование кода](../python/getting-started-with-ptvs-editing-code.md)
[Начало работы с PTVS: Отладка](../python/getting-started-with-ptvs-debugging.md)
[Начало работы с PTVS: Интерактивный Python](../python/getting-started-with-ptvs-interactive-python.md)
[Начало работы с PTVS: Создание веб-сайта в Azure](../python/getting-started-with-ptvs-building-a-website-in-azure.md)

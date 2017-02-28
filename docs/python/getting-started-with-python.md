---
title: "Начало работы с Python в Visual Studio | Документы Майкрософт"
ms.custom: 
ms.date: 1/3/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 33f4f6fb-0ae4-4234-9df2-531f2d3af17f
caps.latest.revision: 11
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
ms.sourcegitcommit: 7d0b0b0b12b9d65f26b67d6f797abc0cf7a0c2c9
ms.openlocfilehash: e7cc978dabb401a8e9bab6791988aa737edb76b0
ms.lasthandoff: 02/22/2017

---
# <a name="getting-started-with-python-in-visual-studio"></a>Начало работы с Python в Visual Studio

Python ([http://python.org/download/](http://python.org/download/)) — это популярный язык программирования, который отличается надежностью, гибкостью и простотой освоения. Он бесплатен и поддерживается широким сообществом разработчиков. Кроме того, для него доступно множество бесплатных библиотек. Python работает в большинстве операционных систем и полезен в различных областях применения, включая веб-приложения, веб-службы, классические приложения, скрипты и научные вычисления. Поэтому он используется множеством университетов, ученых, разработчиков-любителей и профессиональных разработчиков.

Чтобы узнать больше об этом языке, начните с руководства [Python для начинающих](https://www.python.org/about/gettingstarted/) (python.org).

## <a name="python-tools-for-visual-studio"></a>Python Tools for Visual Studio

Инструменты Python для Visual Studio (PTVS) — это бесплатное расширение для Visual Studio с открытым исходным кодом, которое предоставляет эффективную среду разработки на Python, включая систему проектов и шаблоны, широкие возможности редактирования и IntelliSense, полнофункциональную отладку и множество других средств.

Расширение предоставляет указанные ниже возможности.

- Поддержка нескольких интерпретаторов: различные версии CPython, IronPython и IPython.
- Система проектов, которая неявно получает структуру папок кода Python и обеспечивает явное управление, позволяя определять код приложения, тестовый код, веб-страницы, JavaScript, скрипты сборки и т. д.
- Шаблоны проектов для консольных приложений, веб-приложений, Azure, обработки и анализа данных и других типов проектов.
- Широкие возможности редактирования и понимания кода, включая раскраску синтаксических конструкций, автозавершение для всего кода и библиотек, справку по сигнатурам, представление классов, переход к определению, поиск всех ссылок, рефакторинг и т. д.
- Интерактивное окно (REPL)
- Широкие возможности отладки без проекта Visual Studio, вложение в существующий исполняемый файл, смешанный режим отладки, удаленная отладка для Windows, Linux и Mac и отладка в интерактивном окне.

- IPython с визуализацией данных.
- Поддержка IronPython, а также .NET и WPF.
- Средства профилирования.
- Средства тестирования.
- Пакет [Azure SDK для Python](#azure-sdk-for-python)

Используйте следующие ресурсы для начала работы:

- [Установка инструментов Python для Visual Studio](https://www.visualstudio.com/vs/python/)
- [Руководство по установке](https://github.com/Microsoft/PTVS/wiki/PTVS-Installation)
- [Короткие видеоролики по началу работы и углубленному рассмотрению](https://www.youtube.com/playlist?list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff)
- Демонстрация установки и возможностей (27 минут) (https://www.youtube.com/watch?v=JNNAOypc6Ek)
- [Документация](https://github.com/Microsoft/PTVS/wiki)
- [Исходный код](https://github.com/Microsoft/ptvs)


## <a name="azure-sdk-for-python"></a>Пакет Azure SDK для Python

Пакет Azure SDK для Python — это удобное средство для использования служб Microsoft Azure и управления ими. Оно поддерживает ОС Windows, Mac и Linux. Подробные сведения см. в перечисленных ниже ресурсах.

- Чтобы установить пакет SDK, используйте [индекс пакета Python](https://pypi.python.org/pypi/azure) или следуйте инструкциям по [установке Python и пакета SDK](https://azure.microsoft.com/documentation/articles/python-how-to-install/) в документации Azure.
- В [Центре разработчиков пакета Azure SDK для Python](http://azure.microsoft.com/en-us/develop/python/) содержится много полезных сведений, начиная с описания установки и заканчивая документацией с учебниками.  Описание некоторых особенностей
- Практические руководства
  - [Хранилище BLOB-объектов](http://azure.microsoft.com/en-us/develop/python/how-to-guides/blob-service/)
  - [Очередь хранилища](http://azure.microsoft.com/en-us/develop/python/how-to-guides/queue-service/)
  - [Таблица хранилища](http://azure.microsoft.com/en-us/develop/python/how-to-guides/table-service/)
  - [Очередь служебной шины](http://azure.microsoft.com/en-us/develop/python/how-to-guides/service-bus-queues/)   - [Разделы и подписки, связанные со служебной шиной](http://azure.microsoft.com/en-us/develop/python/how-to-guides/service-bus-topics/)
  - [Управление службами](http://azure.microsoft.com/en-us/develop/python/how-to-guides/service-management/)
- В [репозитории GitHub для SDK](https://github.com/Azure/azure-sdk-for-python) имеются [модульные тесты](https://github.com/Azure/azure-sdk-for-python/tree/master/azure-mgmt/tests), которые также являются хорошим источником информации об интерфейсах API.


## <a name="scientific-computing"></a>Научные вычисления
В дополнение ко всем библиотекам научных данных Python Инструменты Python для Visual Studio поддерживают среды IPython и IPython Notebook, которые можно разместить в Azure.

Мы рекомендуем получить среду IPython и библиотеки научных вычислений (matplotlib, scipy, numpy и т. д.) из [Калифорнийского университета в Ирвайне](http://www.lfd.uci.edu/~gohlke/pythonlibs/#scipy-stack).

## <a name="see-also"></a>См. также
 [Начало работы с PTVS. Настройка Visual Studio](../python/getting-started-with-ptvs-setting-up-visual-studio.md)
 [Начало работы с PTVS. Приступаем к написанию кода (проекты)](../python/getting-started-with-ptvs-start-coding-projects.md)
 [Начало работы с PTVS. Редактирование кода](../python/getting-started-with-ptvs-editing-code.md)
 [Начало работы с PTVS. Отладка](../python/getting-started-with-ptvs-debugging.md)
 [Начало работы с PTVS. Interactive Python](../python/getting-started-with-ptvs-interactive-python.md)
 [Начало работы с PTVS. Создание веб-сайта в Azure](../python/getting-started-with-ptvs-building-a-website-in-azure.md)

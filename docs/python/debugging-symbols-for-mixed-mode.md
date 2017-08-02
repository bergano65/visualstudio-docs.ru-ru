---
title: "Символы для смешанного режима отладки Python и C++ в Visual Studio | Документы Майкрософт"
ms.custom: 
ms.date: 4/4/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: be5fdf2f-b55f-488a-9772-58adfe07a7ab
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
ms.sourcegitcommit: adf122a478b29674dc2924dcf7d42972a5a3f52e
ms.openlocfilehash: b8bf362f506255c09468934f01a7beeef3a632dd
ms.lasthandoff: 04/10/2017

---

# <a name="installing-debugging-symbols-for-python-interpreters"></a>Установка отладочных символов для интерпретаторов Python

Чтобы предоставить полные возможности отладки, [отладчик смешанного режима Python](debugging-mixed-mode.md) в Visual Studio должен проанализировать множество внутренних структур данных в используемом интерпретаторе Python. Это означает, что для самого интерпретатора нужны отладочные символы. Для python27.dll, например, соответствующим файлом символов является python27.pdb; для python36.dll файлом символов является python36.pdb. Каждая версия интерпретатора также поддерживает файлы символов для различных модулей.

В Visual Studio 2017 интерпретаторы, "Python 3" и "Anaconda 3" автоматически устанавливают свои соответствующие символы, которые Visual Studio будет находить автоматически. Для Visual Studio 2015 и более ранних версий или при использовании других интерпретаторов необходимо отдельно скачать символы и указать их в Visual Studio, выбрав **Инструменты > Параметры**, а затем — **Отладка > Символы**. Эти действия описаны в разделах ниже.

Visual Studio может вывести запрос на использование символов (обычно при запуске сеанса отладки в смешанном режиме). В этом случае отображается диалоговое окно с двумя вариантами выбора.

- **Открыть диалоговое окно параметров** — открывает диалоговое окно **Параметры** на вкладке **Отладка > Символы**.
- **Загрузить символы для интерпретатора** — открывает эту страницу документации. В этом случае выберите **Инструменты > Параметры** и перейдите на вкладку **Отладка > Символы**, чтобы продолжить.

    ![Запрос на добавление символов в отладчике смешанного режима](~/python/media/mixed-mode-debugging-symbols-required.png)

## <a name="downloading-symbols"></a>Загрузка символов

- Python 3.5 и более поздние версии: получите отладочные символы с помощью установщика Python. Выберите **Выборочная установка**, затем нажмите кнопку **Далее** и перейдите к разделу **Дополнительные параметры**. Здесь установите флажки **Загрузить отладочные символы** и **Загрузить двоичные файлы отладки**.

    ![Добавление отладочных символов в установщике Python 3.x](~/python/media/mixed-mode-debugging-symbols-installer35.png)

    Файлы символов (`.pdb`) будут находиться в корневой папке установки (файлы символов для отдельных модулей находятся в папке `DLLs`). Поэтому Visual Studio найдет их автоматически и никакие дополнительные действия не потребуются.

- Python 3.4.x и более ранние версии: символы доступны в виде загружаемых ZIP-файлов в [официальных дистрибутивах](#official-distributions) или в [Enthought Canopy](#enthought-canopy), как указано ниже. После загрузки извлеките файлы в локальную папку, например в папку `Symbols` внутри папки Python.

    > [!Important]
    > Как в дополнительных сборках Python, так и в сборках 32- и 64-разрядных версий используются разные символы, поэтому нужно точно знать используемые версии. Чтобы проверить, какой интерпретатор используется, разверните в обозревателе решений *узел* **Среды Python** в проекте и запишите имя среды. Затем перейдите в *окно* **Среды Python** и запишите расположение установки. После этого откройте окно командной строки в этом расположении и запустите `python.exe`, чтобы отобразить точную версию и архитектуру — 32- или 64-разрядная.

- Если вы используете дистрибутив Python независимого производителя, например ActiveState Python, свяжитесь с авторами дистрибутива и попросите предоставить вам эти символы. WinPython поддерживает стандартный интерпретатор Python без малейших изменений, поэтому для него можно использовать символы из официального дистрибутива для соответствующего номера версии.

## <a name="pointing-visual-studio-to-the-symbols"></a>Указание Visual Studio на символы

Если вы загрузили символы отдельно, выполните следующие шаги, чтобы Visual Studio могла распознавать их. Если символы установлены с помощью Python 3.5 или более поздней версии установщика, Visual Studio найдет их автоматически.

1. Выберите пункт меню **Инструменты > Параметры**, затем перейдите к разделу **Отладка > Символы**.
    
1. На панели инструментов нажмите кнопку "Добавить" (выделена ниже), укажите папку, где развернуты загруженные символы (там, где находится `python.pdb`, например `c:\python34\Symbols`, как показано ниже), а затем нажмите кнопку **ОК**. 

    ![Параметры символов в отладчике смешанного режима](~/python/media/mixed-mode-debugging-symbols.png)

1. Во время сеанса отладки Visual Studio может также запросить расположение исходного файла для интерпретатора Python. Если вы загрузили эти файлы (например, на сайте [python.org/downloads](https://www.python.org/downloads)), их также можно указать.

> [!Note]
> Функции кэширования символов, отображаемые в диалоговом окне, используются для создания локального кэша символов, полученных из источника в Интернете. Эти функции не нужны для символов интерпретатора Python, так как они уже загружены локально. В любом случае см. раздел [Указание символов и исходных файлов в отладчике Visual Studio](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

## <a name="official-distributions"></a>Официальные дистрибутивы

| Версия Python | Загрузки | 
| --- | --- | 
| 3.5 и более поздние версии | Установите символы с помощью установщика Python. | 
| 3.4.4 | [32-разрядная](https://www.python.org/ftp/python/3.4.4/python-3.4.4-pdb.zip) - [64-разрядная](https://www.python.org/ftp/python/3.4.4/python-3.4.4.amd64-pdb.zip) |
| 3.4.3 | [32-разрядная](https://www.python.org/ftp/python/3.4.3/python-3.4.3-pdb.zip) - [64-разрядная](https://www.python.org/ftp/python/3.4.3/python-3.4.3.amd64-pdb.zip) |
| 3.4.2 | [32-разрядная](https://www.python.org/ftp/python/3.4.2/python-3.4.2-pdb.zip) - [64-разрядная](https://www.python.org/ftp/python/3.4.2/python-3.4.2.amd64-pdb.zip) |
| 3.4.1 | [32-разрядная](https://www.python.org/ftp/python/3.4.1/python-3.4.1-pdb.zip) - [64-разрядная](https://www.python.org/ftp/python/3.4.1/python-3.4.1.amd64-pdb.zip) |
| 3.4.0 | [32-разрядная](https://www.python.org/ftp/python/3.4.0/python-3.4.0-pdb.zip) - [64-разрядная](https://www.python.org/ftp/python/3.4.0/python-3.4.0.amd64-pdb.zip) |
| 3.3.5 | [32-разрядная](http://www.python.org/ftp/python/3.3.5/python-3.3.5-pdb.zip) - [64-разрядная](http://www.python.org/ftp/python/3.3.5/python-3.3.5.amd64-pdb.zip) |
| 3.3.4 | [32-разрядная](http://python.org/ftp/python/3.3.4/python-3.3.4-pdb.zip) - [64-разрядная](http://python.org/ftp/python/3.3.4/python-3.3.4.amd64-pdb.zip) |
| 3.3.3 | [32-разрядная](http://python.org/ftp/python/3.3.3/python-3.3.3-pdb.zip) - [64-разрядная](http://python.org/ftp/python/3.3.3/python-3.3.3.amd64-pdb.zip) |
| 3.3.2 | [32-разрядная](http://python.org/ftp/python/3.3.2/python-3.3.2-pdb.zip) - [64-разрядная](http://python.org/ftp/python/3.3.2/python-3.3.2.amd64-pdb.zip) |
| 3.3.1 | [32-разрядная](http://python.org/ftp/python/3.3.1/python-3.3.1-pdb.zip) - [64-разрядная](http://python.org/ftp/python/3.3.1/python-3.3.1.amd64-pdb.zip) |
| 3.3.0 | [32-разрядная](http://python.org/ftp/python/3.3.0/python-3.3.0-pdb.zip) - [64-разрядная](http://python.org/ftp/python/3.3.0/python-3.3.0.amd64-pdb.zip) |
| 2.7.11 | [32-разрядная](https://www.python.org/ftp/python/2.7.11/python-2.7.11-pdb.zip) - [64-разрядная](https://www.python.org/ftp/python/2.7.11/python-2.7.11.amd64-pdb.zip) |
| 2.7.10 | [32-разрядная](https://www.python.org/ftp/python/2.7.10/python-2.7.10-pdb.zip) - [64-разрядная](https://www.python.org/ftp/python/2.7.10/python-2.7.10.amd64-pdb.zip) |
| 2.7.9 | [32-разрядная](https://www.python.org/ftp/python/2.7.9/python-2.7.9-pdb.zip) - [64-разрядная](https://www.python.org/ftp/python/2.7.9/python-2.7.9.amd64-pdb.zip) |
| 2.7.8 | [32-разрядная](https://www.python.org/ftp/python/2.7.8/python-2.7.8-pdb.zip) - [64-разрядная](https://www.python.org/ftp/python/2.7.8/python-2.7.8.amd64-pdb.zip) |
| 2.7.7 | [32-разрядная](https://www.python.org/ftp/python/2.7.7/python-2.7.7-pdb.zip) - [64-разрядная](https://www.python.org/ftp/python/2.7.7/python-2.7.7.amd64-pdb.zip) |
| 2.7.6 | [32-разрядная](http://python.org/ftp/python/2.7.6/python-2.7.6-pdb.zip) - [64-разрядная](http://python.org/ftp/python/2.7.6/python-2.7.6.amd64-pdb.zip) |
| 2.7.5 | [32-разрядная](http://python.org/ftp/python/2.7.5/python-2.7.5-pdb.zip) - [64-разрядная](http://python.org/ftp/python/2.7.5/python-2.7.5.amd64-pdb.zip) |
| 2.7.4 | [32-разрядная](http://python.org/ftp/python/2.7.4/python-2.7.4-pdb.zip) - [64-разрядная](http://python.org/ftp/python/2.7.4/python-2.7.4.amd64-pdb.zip) |
| 2.7.3 | [32-разрядная](http://python.org/ftp/python/2.7.3/python-2.7.3-pdb.zip) - [64-разрядная](http://python.org/ftp/python/2.7.3/python-2.7.3.amd64-pdb.zip) |
| 2.7.2 | [32-разрядная](http://python.org/ftp/python/2.7.2/python-2.7.2-pdb.zip) - [64-разрядная](http://python.org/ftp/python/2.7.2/python-2.7.2.amd64-pdb.zip) |
| 2.7.1 | [32-разрядная](http://python.org/ftp/python/2.7.1/python-2.7.1-pdb.zip) - [64-разрядная](http://python.org/ftp/python/2.7.1/python-2.7.1.amd64-pdb.zip) |


## <a name="enthought-canopy"></a>Enthought Canopy

Enthought Canopy предоставляет символы для своих двоичных файлов начиная с версии 1.2. Они автоматически устанавливаются вместе с дистрибутивом, но папку, в которой они размещены, необходимо вручную добавить в путь к символам, как описано выше. В обычных установках Canopy для отдельных пользователей эти символы находятся в папке `%UserProfile%\AppData\Local\Enthought\Canopy\User\Scripts` для 64-разрядной версии и `%UserProfile%\AppData\Local\Enthought\Canopy32\User\Scripts` для 32-разрядной версии.

В установках Enthought Canopy 1.1 и более ранних версий, а также в дистрибутивах Enthought Python (EPD) символы для интерпретатора не предоставляются, а значит вы не сможете применить для них отладку в смешанном режиме.

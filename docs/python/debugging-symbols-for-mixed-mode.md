---
title: "Символы для отладки в смешанном режиме для Инструментов Python для Visual Studio | Документация Майкрософт"
ms.custom: 
ms.date: 3/7/2017
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
ms.sourcegitcommit: a42f5a30375192c89c9984e40ba0104da98d7253
ms.openlocfilehash: 9f7ba91262875344ded1e09277883abff292f359
ms.lasthandoff: 03/07/2017

---

# <a name="installing-debugging-symbols-for-python-interpreters"></a>Установка отладочных символов для интерпретаторов Python

Чтобы предоставить полные возможности отладки, [отладчик смешанного режима](debugging-mixed-mode.md) в Инструментах Python для Visual Studio (PTVS) должен проанализировать множество внутренних структур данных в используемом интерпретаторе Python. Это означает, что для самого интерпретатора нужны отладочные символы. Например, для библиотеки python27.dll отладочные символы собраны в файле python27.pdb.

Когда PTVS обнаруживает, что ему нужны эти символы, он предлагает вам указать папку с файлом символов, или скачать их.

![Сообщение о символах при отладке в смешанном режиме](media/mixed-mode-debugging-symbols-required.png) 

Файлы символов вы можете скачать из [официального дистрибутива](#official-distribution) или из [Enthought Canopy](#enthought-canopy), как описано ниже. Если вы используете дистрибутив Python независимого производителя, например ActiveState Python, свяжитесь с авторами дистрибутива и попросите предоставить вам эти символы. (WinPython полностью поддерживает стандартный интерпретатор Python без малейших изменений, поэтому для него можно использовать символы из официального дистрибутива для соответствующего номера версии).

Когда вы предоставите PDB-файлы интерпретатору, сообщите о них PTVS следующим образом, чтобы он автоматически загружал символы при запуске сеансов отладки:

1. Выберите пункт меню **Средства > Параметры**, затем перейдите к разделу **Отладка > Символы**:

![Параметры символов в отладчике смешанного режима](media/mixed-mode-debugging-symbols.png)

1. Нажмите на панели инструментов кнопку "Добавить" (на изображении выше это самая левая кнопка, справа от символа "!"), затем перейдите в папку с PDB-файлами и нажмите кнопку **ОК**.


## <a name="official-distribution"></a>Официальный дистрибутив

Python 3.5 и более поздних версий позволяет предоставить отладочные символы с помощью установщика (как при новой установке, так и с помощью изменения существующей). Выберите **Выборочная установка**, затем нажмите **Далее** и перейдите к разделу **Дополнительные параметры**. Здесь установите флажки "Загрузить отладочные символы**и**Загрузить двоичные файлы отладки**:

![Добавление отладочных символов в установщике Python 3.x](media/mixed-mode-debugging-symbols-installer35.png)

В Python 3.4.x и более ранних версий символы доступны в виде загружаемых ZIP-файлов. Эти файлы нужно скачать, извлечь их содержимое в новую папку и выполнить инструкции из предыдущего раздела, чтобы зарегистрировать файлы в PTVS.

| Версия Python | Загрузки | 
| --- | --- | 
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

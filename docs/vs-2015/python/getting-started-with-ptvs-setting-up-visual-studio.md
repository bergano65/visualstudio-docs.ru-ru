---
title: Начало работы с PTVS. Настройка Visual Studio 2015 | Документация Майкрософт
titleSuffix: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-python
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ec491c1d-bdb2-4c2b-a390-bd808cec635a
caps.latest.revision: 6
author: kraigb
ms.author: kraigb
manager: ghogen
ms.openlocfilehash: c48687f0c3c151b45fed4f6dc53a428faca41cd9
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 12/07/2018
ms.locfileid: "53052923"
---
# <a name="getting-started-with-ptvs-setting-up-visual-studio"></a>Начало работы с PTVS. Настройка Visual Studio

[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio позволяет быстрее установить PTVS и связанные библиотеки. Если у вас нет Visual Studio, можно получить бесплатную копию версии профессионального уровня.

Эти инструкции можно просмотреть в очень коротком [видеоролике в Youtube](https://www.youtube.com/watch?v=_okUV47eM5c&list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff&index=1).

Ниже приведены действия верхнего уровня: установка Visual Studio, установите PTVS, установите Python и библиотеки данных (Anaconda, Canopy), а затем Наконец проверьте установку.

Первое, что вам потребуется — Visual Studio. Если вы разработчик открытого кода или отдельных, можно использовать Visual Studio [Community Edition](https://www.visualstudio.com/products/visual-studio-community-vs), бесплатно, и включающую функции для профессионалов. Community Edition также можно использовать в организации для обучения, научных исследований или участия в проектах с открытым исходным кодом. Учащимся и начинающим разработчикам следует обратиться к программам DreamSpark и BizSpark, чтобы проверить соответствие правам на бесплатный доступ. Кроме того, вы можете спросить у работодателя, есть ли у вас подписка MSDN.

После установки Visual Studio вам потребуется [установить PTVS](http://pytools.codeplex.com/wikipage?title=PTVS%20Installation). Это расширение бесплатно, автономно, полностью поддерживается корпорацией Майкрософт и разрабатывается в рамках открытого проекта при участии сообщества разработчиков.

Теперь нужно [установить Python](https://www.python.org/download/). Python поддерживается сообществом, и Домашняя страница проекта — python.org. Компания continuum Analytics предоставляет бесплатный пакет Anaconda, включающий Python и многие полезные библиотеки (особенно для обработки и анализа и обработки данных) и Enthought создает аналогичный пакет с именем Canopy. Вам достаточно установить только один из этих продуктов. Если вы не можете определиться, начните с пакета [Anaconda](https://www.continuum.io/downloads), который включает последнюю версию Python и большинство пакетов со сложной установкой.

Запустите Visual Studio и убедитесь в том, что все работает. В меню «Вид» выберите «Другие окна». В списке вы увидите пункт «Среды Python». В этом окне показаны все установки Python, обнаруженные PTVS, и все установленные пакеты. Окно также управляет обновлением базы данных для отображения вариантов завершения при редактировании кода. Процесс обновления занимает некоторое время, но после его завершения PTVS может предоставить гораздо больше полезных сведений о пакетах.

Если вы хотите использовать IPython с PTVS, выполните эти [инструкции](http://pytools.codeplex.com/wikipage?title=Using%20IPython%20with%20PTVS).

Вы можете ознакомиться с этими инструкциями в короткие [видео на сайте youtube](https://www.youtube.com/watch?v=_okUV47eM5c&list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff&index=1).

## <a name="see-also"></a>См. также

[Видеоролики по началу работы и углубленному рассмотрению PTVS](https://www.youtube.com/playlist?list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff)

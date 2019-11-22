---
title: Начало работы с PTVS. Настройка Visual Studio 2015 | Документация Майкрософт
titleSuffix: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-python
ms.topic: conceptual
ms.assetid: ec491c1d-bdb2-4c2b-a390-bd808cec635a
caps.latest.revision: 6
author: kraigb
ms.author: kraigb
manager: jillfra
ms.openlocfilehash: 073230f2b2a35a27540b9a67cfec3c4ace502eb8
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2019
ms.locfileid: "74300502"
---
# <a name="getting-started-with-ptvs-setting-up-visual-studio"></a>Начало работы с PTVS. Настройка Visual Studio

[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio позволяет быстрее установить PTVS и связанные библиотеки. Если у вас нет Visual Studio, можно получить бесплатную копию версии профессионального уровня.

Эти инструкции можно просмотреть в очень коротком [видеоролике в Youtube](https://www.youtube.com/watch?v=_okUV47eM5c&list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff&index=1).

Если кратко: установите Visual Studio, установите PTVS, установите Python и библиотеки данных (Anaconda, Canopy), а затем проверьте установку.

Прежде всего вам потребуется Visual Studio. Если вы разработчик открытого кода или независимый разработчик, вы можете использовать Visual Studio [Community Edition](https://www.visualstudio.com/products/visual-studio-community-vs) — бесплатную версию, включающую функции для профессионалов. Community Edition также можно использовать в организации для обучения, научных исследований или участия в проектах с открытым исходным кодом. Учащимся и начинающим разработчикам следует обратиться к программам DreamSpark и BizSpark, чтобы проверить соответствие правам на бесплатный доступ. Кроме того, вы можете спросить у работодателя, есть ли у вас подписка MSDN.

После установки Visual Studio вам потребуется [установить PTVS](https://archive.codeplex.com/?p=pytools). Это расширение бесплатно, автономно, полностью поддерживается корпорацией Майкрософт и разрабатывается в рамках открытого проекта при участии сообщества разработчиков.

Теперь нужно [установить Python](https://www.python.org/download/). Python поддерживается сообществом разработчиков; домашняя страница проекта — python.org. Компания Continuum Analytics предоставляет бесплатный пакет Anaconda, включающий Python и многие полезные библиотеки (особенно для обработки научных вычислений и данных), а компания Enthought выпускает аналогичный пакет Canopy. Вам нужно установить один из пакетов. Если вы не можете определиться, начните с пакета [Anaconda](https://www.continuum.io/downloads), который включает последнюю версию Python и большинство пакетов со сложной установкой.

Запустите Visual Studio и убедитесь в том, что все работает. В меню «Вид» выберите «Другие окна». В списке вы увидите пункт «Среды Python». В этом окне показаны все установки Python, обнаруженные PTVS, и все установленные пакеты. Окно также управляет обновлением базы данных для отображения вариантов завершения при редактировании кода. Процесс обновления занимает некоторое время, но после его завершения PTVS может предоставить гораздо больше полезных сведений о пакетах.

Если вы хотите использовать IPython с PTVS, выполните эти [инструкции](https://archive.codeplex.com/?p=pytools).

Эти инструкции можно просмотреть в коротком [видеоролике в YouTube](https://www.youtube.com/watch?v=_okUV47eM5c&list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff&index=1).

## <a name="see-also"></a>См. также

[Видеоролики по началу работы и углубленному рассмотрению PTVS](https://www.youtube.com/playlist?list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff)

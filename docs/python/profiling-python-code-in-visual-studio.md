---
title: Измерение производительности кода Python
description: Руководство по проверке производительности кода Python при использовании интерпретаторов на основе CPython с помощью профилировщика Visual Studio.
ms.date: 01/09/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- python
- data-science
ms.openlocfilehash: 2f0bd25221f975cd8df122af51af20d125a43a65
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/19/2018
ms.locfileid: "31584078"
---
# <a name="profiling-python-code"></a>Профилирование кода Python

Вы можете профилировать приложение Python при использовании интерпретаторов на основе CPython. (Сведения о доступности этой функции для разных версий Visual Studio см. в разделе [Матрица возможностей — профилирование](overview-of-python-tools-for-visual-studio.md#matrix-profiling).)

Профилирование запускается с помощью меню **Анализ > Launch Python Profiling** (Запустить профилирование Python), которая открывает такое диалоговое окно:

![Диалоговое окно профилирования](media/profiling-start.png)

Когда вы нажмете кнопку **ОК**, запустится профилировщик, в котором откроется отчет о производительности. Из отчета вы узнаете, сколько времени выполнялось ваше приложение:

![Отчет профилирования о производительности](media/profiling-results.png)

|   |   |
|---|---|
| ![значок кинокамеры для видео](../install/media/video-icon.png "Просмотреть видео") | [Просмотрите видео (Microsoft Virtual Academy)](https://mva.microsoft.com/en-US/training-courses-embed/python-tools-for-visual-studio-2017-18121/Video-Profiling-Python-s6FoC6LWE_1005918567) с примером профилирования Python (3 мин 00 с)|

> [!Note]
> Сейчас Visual Studio поддерживает только этот уровень профилирования приложений, но мы хотим получить ваши отзывы о других возможностях. Используйте [кнопку обратной связи **Была ли эта страница полезной?**](#feedback) внизу страницы.

## <a name="profiling-for-ironpython"></a>Профилирование для IronPython

Так как интерпретатор IronPython не основан на CPython, функция профилирования для него не работает.

Вместо этого используйте профилировщик Visual Studio .NET, запустив `ipy.exe` непосредственно в качестве целевого приложения с аргументами, чтобы запустить нужный сценарий загрузки. Включите в командную строку параметр `-X:Debug`, чтобы обеспечить отладку и профилирование для всего кода Python. Этот аргумент создает отчет о производительности, где указано время, затраченное и на среду выполнения IronPython, и на основной код. Для вашего кода используются искаженные имена.

Кроме того, IronPython имеет некоторые встроенные средства профилирования, но пока для них нет хорошего средства визуализации. В разделе [о профилировщике IronPython](http://blogs.msdn.com/b/curth/archive/2009/03/29/an-ironpython-profiler.aspx) (на сайте блогов MSDN) вы можете узнать, какие средства доступны.
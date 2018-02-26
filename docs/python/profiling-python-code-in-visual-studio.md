---
title: "Измерение производительности кода Python в Visual Studio | Документация Майкрософт"
description: "Руководство по проверке производительности кода Python при использовании интерпретаторов на основе CPython с помощью профилировщика Visual Studio."
ms.custom: 
ms.date: 01/09/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
dev_langs:
- python
ms.tgt_pltfrm: 
ms.topic: article
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload:
- python
- data-science
ms.openlocfilehash: 0faae917aba237a85c6a01743d89cf66adf06296
ms.sourcegitcommit: a07b789cc41ed72664f2c700c1f114476e7b0ddd
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/19/2018
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

## <a name="profiling-for-ironpython"></a>Профилирование для IronPython

Так как интерпретатор IronPython не основан на CPython, функция профилирования для него не работает.

Вместо этого используйте профилировщик Visual Studio .NET, запустив `ipy.exe` непосредственно в качестве целевого приложения с аргументами, чтобы запустить нужный сценарий загрузки. Включите в командную строку параметр `-X:Debug`, чтобы обеспечить отладку и профилирование для всего кода Python. Этот аргумент создает отчет о производительности, где указано время, затраченное и на среду выполнения IronPython, и на основной код. Для вашего кода используются искаженные имена.

Кроме того, IronPython имеет некоторые встроенные средства профилирования, но пока для них нет хорошего средства визуализации. В разделе [о профилировщике IronPython](http://blogs.msdn.com/b/curth/archive/2009/03/29/an-ironpython-profiler.aspx) (на сайте блогов MSDN) вы можете узнать, какие средства доступны.
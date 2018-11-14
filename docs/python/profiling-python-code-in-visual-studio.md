---
title: Измерение производительности кода Python
description: Руководство по проверке производительности кода Python при использовании интерпретаторов на основе CPython с помощью профилировщика Visual Studio.
ms.date: 11/12/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- python
- data-science
ms.openlocfilehash: 0b5ca29b061f0ba61eec775a0344fb8d2067e08d
ms.sourcegitcommit: 6a955a2d179cd0e137942389f940d9fcbbe125de
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/13/2018
ms.locfileid: "51607488"
---
# <a name="profile-python-code"></a>Профилирование кода Python

Вы можете профилировать приложение Python при использовании интерпретаторов на основе CPython. (Сведения о доступности этой функции для разных версий Visual Studio см. в разделе [Матрица возможностей — профилирование](overview-of-python-tools-for-visual-studio.md#matrix-profiling).)

## <a name="profiling-for-cpython-based-interpreters"></a>Профилирование для интерпретаторов на основе CPython

Профилирование запускается с помощью команды меню **Анализ** > **Запустить профилирование Python**, которая открывает диалоговое окно настройки:

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

Вместо этого используйте профилировщик Visual Studio .NET, запустив *ipy.exe* непосредственно в качестве целевого приложения с аргументами, чтобы запустить нужный скрипт загрузки. Включите в командную строку параметр `-X:Debug`, чтобы обеспечить отладку и профилирование для всего кода Python. Этот аргумент создает отчет о производительности, где указано время, затраченное на среду выполнения IronPython и основной код. Для вашего кода используются искаженные имена.

Кроме того, IronPython имеет некоторые встроенные средства профилирования, но пока для них нет хорошего средства визуализации. В разделе [о профилировщике IronPython](https://blogs.msdn.microsoft.com/curth/2009/03/30/an-ironpython-profiler/) (на сайте блогов MSDN) вы можете узнать, какие средства доступны.

---
title: "Измерение производительности кода Python в Visual Studio | Документация Майкрософт"
ms.custom: 
ms.date: 01/09/2018
ms.reviewer: 
ms.suite: 
ms.technology: devlang-python
ms.devlang: python
ms.tgt_pltfrm: 
ms.topic: article
caps.latest.revision: "1"
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload:
- python
- data-science
ms.openlocfilehash: bdfd378a9441aba9c57c56f1f853e5cdd27a8d49
ms.sourcegitcommit: 11740fed01cc602252ef698aaa11c07987b00570
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/12/2018
---
# <a name="profiling-python-code"></a>Профилирование кода Python

Visual Studio поддерживает профилирование приложений Python при использовании интерпретаторов на основе CPython.

Профилирование запускается с помощью меню **Анализ > Launch Python Profiling** (Запустить профилирование Python), которая открывает такое диалоговое окно:

![Диалоговое окно профилирования](media/profiling-start.png)

Когда вы нажмете кнопку **ОК**, запустится профилировщик, в котором откроется отчет о производительности. Из отчета вы узнаете, сколько времени выполнялось ваше приложение:

![Отчет профилирования о производительности](media/profiling-results.png)

Демонстрацию см. в видеоролике [Профилирование Python](https://mva.microsoft.com/en-US/training-courses/python-tools-for-visual-studio-2017-18121?l=s6FoC6LWE_1005918567) (Microsoft Virtual Academy, 3 мин 00 с).

> [!VIDEO https://mva.microsoft.com/en-US/training-courses-embed/python-tools-for-visual-studio-2017-18121/Video-Profiling-Python-s6FoC6LWE_1005918567]

## <a name="profiling-for-ironpython"></a>Профилирование для IronPython

Так как интерпретатор IronPython не основан на CPython, функция профилирования для него не работает.

Вместо этого используйте профилировщик Visual Studio .NET, запустив `ipy.exe` непосредственно в качестве целевого приложения с аргументами, чтобы запустить нужный сценарий загрузки. Включите в командную строку параметр `-X:Debug`, чтобы обеспечить отладку и профилирование для всего кода Python. Этот аргумент создает отчет о производительности, где указано время, затраченное и на среду выполнения IronPython, и на основной код. Для вашего кода используются искаженные имена.

Кроме того, IronPython имеет некоторые встроенные средства профилирования, но пока для них нет хорошего средства визуализации. В разделе [о профилировщике IronPython](http://blogs.msdn.com/b/curth/archive/2009/03/29/an-ironpython-profiler.aspx) (на сайте блогов MSDN) вы можете узнать, какие средства доступны.
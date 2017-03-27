---
title: "Измерение производительности кода Python в Visual Studio | Документация Майкрософт"
ms.custom: 
ms.date: 3/7/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2723d4d0-89c8-4279-bfc2-27c0834a997e
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
ms.sourcegitcommit: 7d726441c2d6953bd7b50451bec7fff05d5d71b0
ms.openlocfilehash: 2511f1076450848dfc75584edc97950fd4279c7b
ms.lasthandoff: 03/10/2017

---

# <a name="profiling-python-code"></a>Профилирование кода Python

Visual Studio поддерживает профилирование приложений Python при использовании интерпретаторов на основе CPython.

Профилирование запускается с помощью меню **Анализ > Launch Python Profiling** (Запустить профилирование Python), которая открывает такое диалоговое окно:

![Диалоговое окно профилирования](media/profiling-start.png)

Когда вы нажмете кнопку **ОК**, запустится профилировщик, в котором откроется отчет о производительности. Из отчета вы узнаете, сколько времени выполнялось ваше приложение:

![Отчет профилирования о производительности](media/profiling-results.png)

Обзор см. далее.

Пошаговое руководство представлено в видеоролике [Profiling with Python Tools for Visual Studio](http://www.youtube.com/watch?v=K-KqkFkp55k) (Профилирование с помощью инструментов Python для Visual Studio, длительность 8 мин 52 с).

> [!VIDEO https://www.youtube.com/embed/K-KqkFkp55k]

## <a name="profiling-for-ironpython"></a>Профилирование для IronPython

Поскольку интерпретатор IronPython не основан на CPython, функция профилирования для него не работает.

Вместо этого используйте профилировщик Visual Studio .NET, запустив `ipy.exe` непосредственно в качестве целевого приложения с аргументами, чтобы запустить нужный сценарий загрузки. Включите в командную строку параметр `-X:Debug`, чтобы принудительно разрешить отладку и профилирование для всего кода Python. Теперь в отчете о производительности будет указано время, затраченное и на среду выполнения IronPython, и на основной код. Для вашего кода используются искаженные имена.

Кроме того, IronPython имеет некоторые встроенные средства профилирования, но пока для них нет хорошего средства визуализации. В разделе [о профилировщике IronPython](http://blogs.msdn.com/b/curth/archive/2009/03/29/an-ironpython-profiler.aspx) (на сайте блогов MSDN) вы можете узнать, какие средства доступны.

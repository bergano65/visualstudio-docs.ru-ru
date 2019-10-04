---
title: Создание пользовательских представлений объектов | Документация Майкрософт
ms.date: 01/08/2019
ms.topic: conceptual
f1_keywords:
- vs.debug.data.elements
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- data types, custom
- custom data types
- managed code, custom data types
- autoexp.dat file
- mcee_cs.dat file
- debugger, expanding data types
- mcee_mc.dat file
ms.assetid: 9969e9b2-9008-4729-8a14-0d6deaa61576
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 36e875bc8101bc8a1b0eb1bec6671c76e3b0c9b2
ms.sourcegitcommit: 8a3545329a58e446672181cfed2083f850e1ad14
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2019
ms.locfileid: "71814301"
---
# <a name="create-custom-views-of-objects-c-visual-basic-f-ccli"></a>Создание пользовательских представлений объектов (C#, Visual Basic, F#, C++/CLI)
Можно настроить то, как Visual Studio отображает типы данных в окнах переменных отладчика.

## <a name="attributes"></a>Атрибуты

В C#Visual Basic, F#и C++ (C++только для кода/CLI) можно добавлять расширения для пользовательских данных с помощью <xref:System.Diagnostics.DebuggerTypeProxyAttribute>, <xref:System.Diagnostics.DebuggerDisplayAttribute> и <xref:System.Diagnostics.DebuggerBrowsableAttribute>.

В .NET Framework 2,0 код Visual Basic не поддерживает атрибут Дебугжербровсабле. Это ограничение устранено в более новых версиях платформы .NET Framework.

## <a name="visualizers"></a>Визуализаторы

Можно написать визуализатор для отображения любого управляемого типа. Дополнительные сведения см. в разделе [Практическое руководство. написать визуализатор](/visualstudio/debugger/create-custom-visualizers-of-data).

> [!NOTE]
> Для C++ кода можно добавить расширения пользовательских типов данных с помощью платформы Natvis, как описано в разделе [Создание пользовательских представлений C++ объектов в отладчике](/visualstudio/debugger/create-custom-views-of-native-objects).

## <a name="see-also"></a>См. также

- [Сообщить отладчику, что отображать с помощью атрибута DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md)
- [Сообщить отладчику, какой тип отображать с помощью атрибута DebuggerTypeProxy](../debugger/using-debuggertypeproxy-attribute.md)
- [Окна "Контрольные значения" и "Быстрая проверка"](../debugger/watch-and-quickwatch-windows.md)
- [Повышение эффективности отладки с помощью атрибутов просмотра отладчика](/dotnet/framework/debug-trace-profile/enhancing-debugging-with-the-debugger-display-attributes)
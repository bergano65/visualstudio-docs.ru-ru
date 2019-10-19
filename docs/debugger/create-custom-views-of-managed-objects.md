---
title: Создание пользовательских представлений управляемых объектов | Документация Майкрософт
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
ms.openlocfilehash: 3d75193368188efc660391d1e80c562ed881324b
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72578017"
---
# <a name="create-custom-views-of-managed-objects-c-visual-basic-f-ccli"></a>Создание пользовательских представлений управляемых объектов (C#, Visual Basic, F#, C++/CLI)
Можно настроить то, как Visual Studio отображает типы данных в окнах переменных отладчика.

## <a name="attributes"></a>Атрибуты

В C#Visual Basic, F#и C++ (C++только для кода/CLI) можно добавлять расширения для пользовательских данных с помощью <xref:System.Diagnostics.DebuggerTypeProxyAttribute>, <xref:System.Diagnostics.DebuggerDisplayAttribute> и <xref:System.Diagnostics.DebuggerBrowsableAttribute>.

В .NET Framework 2,0 код Visual Basic не поддерживает атрибут Дебугжербровсабле. Это ограничение удаляется в более поздних версиях .NET.

## <a name="visualizers"></a>Визуализаторы

Можно написать визуализатор для отображения любого управляемого типа. Дополнительные сведения см. [в разделе Практические руководства. Написание визуализатора](/visualstudio/debugger/create-custom-visualizers-of-data).

> [!NOTE]
> Для C++ кода можно добавить расширения пользовательских типов данных с помощью платформы Natvis, как описано в разделе [Создание пользовательских представлений C++ объектов в отладчике](/visualstudio/debugger/create-custom-views-of-native-objects).

## <a name="see-also"></a>См. также раздел

- [Сообщить отладчику, что отображать с помощью атрибута DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md)
- [Сообщить отладчику, какой тип отображать с помощью атрибута DebuggerTypeProxy](../debugger/using-debuggertypeproxy-attribute.md)
- [Окна "Контрольные значения" и "Быстрая проверка"](../debugger/watch-and-quickwatch-windows.md)
- [Повышение эффективности отладки с помощью атрибутов просмотра отладчика](/dotnet/framework/debug-trace-profile/enhancing-debugging-with-the-debugger-display-attributes)

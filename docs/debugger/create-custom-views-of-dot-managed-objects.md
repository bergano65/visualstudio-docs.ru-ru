---
title: Создание настраиваемых представлений объектов | Документация Майкрософт
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
ms.openlocfilehash: 733f3ec7573287e934f8a5f0167db89c0683759a
ms.sourcegitcommit: cd91a8a4f6086cda9ba6948be25864fc7d6b8e44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/12/2019
ms.locfileid: "59537482"
---
# <a name="create-custom-views-of-objects-c-visual-basic-c"></a>Создание настраиваемых представлений объектов (C#, Visual Basic, C++)
Можно настроить то, как Visual Studio отображает типы данных в окнах переменных отладчика.

## <a name="native-code"></a>Машинный код

Для C++ кода, можно добавить расширения пользовательских типов данных с помощью платформы Natvis, как описано в разделе [Создание пользовательских представлений C++ объектов в отладчике](/visualstudio/debugger/create-custom-views-of-native-objects). Для C++/кода интерфейса командной строки, также можно использовать атрибуты, описанные здесь, в этой статье.

## <a name="attributes"></a>Атрибуты

В C#, Visual Basic и C++ (C++только выполняет код), можно добавлять расширения для пользовательских данных при помощи <xref:System.Diagnostics.DebuggerTypeProxyAttribute>, <xref:System.Diagnostics.DebuggerDisplayAttribute>, и <xref:System.Diagnostics.DebuggerBrowsableAttribute>.

Visual Basic не поддерживает атрибут DebuggerBrowsable в случае кода для [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)]. Это ограничение устранено в более новых версиях платформы .NET Framework.

## <a name="visualizers"></a>Визуализаторы

Можно написать визуализатор для отображения любого управляемого типа. Дополнительные сведения см. в разделе [Как написать визуализатор](/visualstudio/debugger/create-custom-visualizers-of-data).

## <a name="see-also"></a>См. также

- [Указать отладчику, что нужно показывать использование атрибута DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md)
- [Указать отладчику какие типов, чтобы отобразить использование атрибута DebuggerTypeProxy](../debugger/using-debuggertypeproxy-attribute.md)
- [Окна "Контрольные значения" и "Быстрая проверка"](../debugger/watch-and-quickwatch-windows.md)
- [Повышение эффективности отладки с помощью атрибутов просмотра отладчика](/dotnet/framework/debug-trace-profile/enhancing-debugging-with-the-debugger-display-attributes)
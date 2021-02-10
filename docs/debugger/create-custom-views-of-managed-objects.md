---
title: Создание настраиваемых представлений управляемых объектов | Документация Майкрософт
description: Данные отладчика Visual Studio отображаются в окнах переменных. В этой статье приводятся сведения о том, как настраивать отображение типов данных, включая пользовательские типы.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: c054d3bcfbb06d0093f04190ab8b4825b5cbf20f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99865804"
---
# <a name="create-custom-views-of-managed-objects-c-visual-basic-f-ccli"></a>Создание настраиваемых представлений управляемых объектов (C#, Visual Basic, F#, C++/CLI)
Можно настроить то, как Visual Studio отображает типы данных в окнах переменных отладчика.

## <a name="attributes"></a>Атрибуты

В C#, Visual Basic, F# и C++ (только код C++/CLI) можно добавлять расширения для пользовательских данных с помощью <xref:System.Diagnostics.DebuggerTypeProxyAttribute>, <xref:System.Diagnostics.DebuggerDisplayAttribute> и <xref:System.Diagnostics.DebuggerBrowsableAttribute>.

При использовании кода .NET Framework 2.0 Visual Basic не поддерживает атрибут DebuggerBrowsable. Это ограничение устранено в более новых версиях .NET.

## <a name="visualizers"></a>Визуализаторы

Можно написать визуализатор для отображения любого управляемого типа. Дополнительные сведения см. в разделе [Практическое руководство. написать визуализатор](create-custom-visualizers-of-data.md).

> [!NOTE]
> При использовании кода C++ вы можете добавлять расширения пользовательских типов данных, используя платформу Natvis (см. руководство по [созданию пользовательских представлений объектов C++ в отладчике](create-custom-views-of-native-objects.md)).

## <a name="see-also"></a>См. также

- [Информирование отладчика о том, что отображать, с помощью атрибута DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md)
- [Информирование отладчика о том, что отображать, с помощью атрибута DebuggerTypeProxy](../debugger/using-debuggertypeproxy-attribute.md)
- [Окна "Контрольные значения" и "Быстрая проверка"](../debugger/watch-and-quickwatch-windows.md)
- [Повышение эффективности отладки с помощью атрибутов просмотра отладчика](/dotnet/framework/debug-trace-profile/enhancing-debugging-with-the-debugger-display-attributes)

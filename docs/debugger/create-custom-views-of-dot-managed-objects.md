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
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: c2e4b2d34df1a1e870247112892d4cd00ff887f3
ms.sourcegitcommit: 01185dadd2fa1f9a040d2a366869f1a5e1d18e0f
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 01/11/2019
ms.locfileid: "54227646"
---
# <a name="create-custom-views-of-objects-c-visual-basic-c"></a>Создание настраиваемых представлений объектов (C#, Visual Basic, C++)
Можно настроить то, как Visual Studio отображает типы данных в окнах переменных отладчика.  

## <a name="native-code"></a>Машинный код

Для кода C++, можно добавить расширения пользовательских типов данных с помощью платформы Natvis, как описано в разделе [создавать пользовательские представления собственного объекта в отладчике](/visualstudio/debugger/create-custom-views-of-native-objects). Для C + +/ CLI кода, также можно использовать атрибуты, описанные здесь, в этой статье.

## <a name="attributes"></a>Атрибуты

В C#, Visual Basic и C++ (C + +/ CLI только в код), можно добавлять расширения для пользовательских данных при помощи <xref:System.Diagnostics.DebuggerTypeProxyAttribute>, <xref:System.Diagnostics.DebuggerDisplayAttribute>, и <xref:System.Diagnostics.DebuggerBrowsableAttribute>.  
  
Visual Basic не поддерживает атрибут DebuggerBrowsable в случае кода для [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)]. Это ограничение устранено в более новых версиях платформы .NET Framework.    

## <a name="visualizers"></a>Визуализаторы

Можно написать визуализатор для отображения любого управляемого типа. Дополнительные сведения см. в разделе [Как написать визуализатор](/visualstudio/debugger/create-custom-visualizers-of-data).
  
## <a name="see-also"></a>См. также раздел  
 [Использование атрибута DebuggerTypeProxy](../debugger/using-debuggertypeproxy-attribute.md)   
 [Использование атрибута DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md)   
 [Окна "Контрольные значения" и "Быстрая проверка"](../debugger/watch-and-quickwatch-windows.md)   
 [Повышение эффективности отладки с помощью атрибутов просмотра отладчика](/dotnet/framework/debug-trace-profile/enhancing-debugging-with-the-debugger-display-attributes)
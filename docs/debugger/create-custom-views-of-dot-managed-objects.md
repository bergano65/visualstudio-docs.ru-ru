---
title: "Создание настраиваемых представлений управляемых объектов | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.data.elements
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- data types [C#], custom
- custom data types
- managed code, custom data types
- autoexp.dat file
- mcee_cs.dat file
- debugger, expanding data types
- mcee_mc.dat file
ms.assetid: 9969e9b2-9008-4729-8a14-0d6deaa61576
caps.latest.revision: "34"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: dotnet
ms.openlocfilehash: 329e7fae6a2a8682c23417f88e59700b7caffd53
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="create-custom-views-of-managed-objects"></a>Создание настраиваемых представлений управляемых объектов
Можно настроить то, как Visual Studio отображает типы данных в окнах переменных отладчика.  
  
## <a name="attributes"></a>Атрибуты  
 В C# и Visual Basic можно добавлять расширения для пользовательских данных с помощью <xref:System.Diagnostics.DebuggerTypeProxyAttribute>, <xref:System.Diagnostics.DebuggerDisplayAttribute> и <xref:System.Diagnostics.DebuggerBrowsableAttribute>.  
  
 Visual Basic не поддерживает атрибут DebuggerBrowsable в случае кода для [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)]. Это ограничение устранено в более новых версиях платформы .NET Framework.  
  
## <a name="visualizers"></a>Визуализаторы  
 Можно написать визуализатор для отображения любого управляемого типа. Дополнительные сведения см. в разделе [как: написать визуализатор](../debugger/how-to-write-a-visualizer.md).  
  
## <a name="native-code"></a>Машинный код  
 Для машинного кода можно добавлять расширения пользовательских типов данных в файл autoexp.dat, который находится в каталоге "Program Files\Microsoft Visual Studio 11.0\Common7\Packages\Debugger". Инструкции относительно записи в `autoexp` правил автоматического использования, расположены в этом файле.  
  
> [!CAUTION]
>  Структура этого файла, а также синтаксис правил автоматического использования могут изменяться от одного выпуска Visual Studio к другому.  
  
 Отображение машинного типа можно также настроить путем написания надстройки — вычислителя выражений. Дополнительные сведения см. в разделе EEAddIn Sample: Debugging Expression Evaluator Add-In. Дополнительные сведения см. в разделе [пример EEAddIn: отладка выражение оценки надстройки](http://msdn.microsoft.com/en-us/d4f6b068-c812-45bc-9ec0-7e0363c4bb9e).  
  
## <a name="see-also"></a>См. также  
 [Использование атрибута DebuggerTypeProxy](../debugger/using-debuggertypeproxy-attribute.md)   
 [Использование атрибута DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md)   
 [Контрольное значение и окна "Быстрая проверка"](../debugger/watch-and-quickwatch-windows.md)   
 [Повышение эффективности отладки с помощью атрибутов просмотра отладчика](/dotnet/framework/debug-trace-profile/enhancing-debugging-with-the-debugger-display-attributes)
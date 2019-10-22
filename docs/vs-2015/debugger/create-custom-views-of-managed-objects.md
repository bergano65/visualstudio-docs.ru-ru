---
title: Создание пользовательских представлений управляемых объектов | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.data.elements
dev_langs:
- FSharp
- VB
- CSharp
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
caps.latest.revision: 37
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: cb5b56404c7ddc99b7999b47cf3c2a899f915efd
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72578029"
---
# <a name="create-custom-views-of-managed-objects"></a>Создание настраиваемых представлений управляемых объектов
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Можно настроить то, как Visual Studio отображает типы данных в окнах переменных отладчика.  
  
## <a name="attributes"></a>Атрибуты  
 В C# и Visual Basic можно добавлять расширения для пользовательских данных с помощью <xref:System.Diagnostics.DebuggerTypeProxyAttribute>, <xref:System.Diagnostics.DebuggerDisplayAttribute> и <xref:System.Diagnostics.DebuggerBrowsableAttribute>.  
  
 Visual Basic не поддерживает атрибут DebuggerBrowsable в случае кода для [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)]. Это ограничение устранено в более новых версиях платформы .NET Framework.  
  
## <a name="visualizers"></a>Визуализаторы  
 Можно написать визуализатор для отображения любого управляемого типа. Дополнительные сведения см. [в разделе Практические руководства. Написание визуализатора](../debugger/how-to-write-a-visualizer.md).  
  
## <a name="native-code"></a>Машинный код  
 Для машинного кода можно добавлять расширения пользовательских типов данных в файл autoexp.dat, который находится в каталоге "Program Files\Microsoft Visual Studio 11.0\Common7\Packages\Debugger". Инструкции относительно записи в `autoexp` правил автоматического использования, расположены в этом файле.  
  
> [!CAUTION]
> Структура этого файла, а также синтаксис правил автоматического использования могут изменяться от одного выпуска Visual Studio к другому.  
  
 Отображение машинного типа можно также настроить путем написания надстройки — вычислителя выражений. Дополнительные сведения см. в разделе EEAddIn Sample: Debugging Expression Evaluator Add-In. Дополнительные сведения см. [в разделе Иаддин Sample: отладка надстройки оценщика выражений](https://msdn.microsoft.com/d4f6b068-c812-45bc-9ec0-7e0363c4bb9e).  
  
## <a name="see-also"></a>См. также раздел  
 [Использование атрибута DebuggerTypeProxy](../debugger/using-debuggertypeproxy-attribute.md)   
 [Использование атрибута DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md)   
 [Окна "Контрольные значения" и "Быстрая проверка"](../debugger/watch-and-quickwatch-windows.md)   
 [Повышение эффективности отладки с помощью атрибутов просмотра отладчика](https://msdn.microsoft.com/library/72bb7aa9-459b-42c4-9163-9312fab4c410)

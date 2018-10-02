---
title: Создание настраиваемых представлений управляемых объектов | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
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
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a84802e3b4e3c32f917dba56fce95268e39cd4bb
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47558327"
---
# <a name="create-custom-views-of-managed-objects"></a>Создание настраиваемых представлений управляемых объектов
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [Создание настраиваемых представлений управляемых объектов](https://docs.microsoft.com/visualstudio/debugger/create-custom-views-of-dot-managed-objects).  
  
Можно настроить то, как Visual Studio отображает типы данных в окнах переменных отладчика.  
  
## <a name="attributes"></a>Атрибуты  
 В C# и Visual Basic можно добавлять расширения для пользовательских данных с помощью <xref:System.Diagnostics.DebuggerTypeProxyAttribute>, <xref:System.Diagnostics.DebuggerDisplayAttribute> и <xref:System.Diagnostics.DebuggerBrowsableAttribute>.  
  
 Visual Basic не поддерживает атрибут DebuggerBrowsable в случае кода для [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)]. Это ограничение устранено в более новых версиях платформы .NET Framework.  
  
## <a name="visualizers"></a>Визуализаторы  
 Можно написать визуализатор для отображения любого управляемого типа. Дополнительные сведения см. в разделе [как: Написание визуализатора на](../debugger/how-to-write-a-visualizer.md).  
  
## <a name="native-code"></a>Машинный код  
 Для машинного кода можно добавлять расширения пользовательских типов данных в файл autoexp.dat, который находится в каталоге "Program Files\Microsoft Visual Studio 11.0\Common7\Packages\Debugger". Инструкции относительно записи в `autoexp` правил автоматического использования, расположены в этом файле.  
  
> [!CAUTION]
>  Структура этого файла, а также синтаксис правил автоматического использования могут изменяться от одного выпуска Visual Studio к другому.  
  
 Отображение машинного типа можно также настроить путем написания надстройки — вычислителя выражений. Дополнительные сведения см. в разделе EEAddIn Sample: Debugging Expression Evaluator Add-In. Дополнительные сведения см. в разделе [пример EEAddIn: отладка выражение вычислителя надстройки](http://msdn.microsoft.com/en-us/d4f6b068-c812-45bc-9ec0-7e0363c4bb9e).  
  
## <a name="see-also"></a>См. также  
 [Использование атрибута DebuggerTypeProxy](../debugger/using-debuggertypeproxy-attribute.md)   
 [Использование атрибута DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md)   
 [Посмотрите, как и Windows "Быстрая проверка"](../debugger/watch-and-quickwatch-windows.md)   
 [Повышение эффективности отладки с помощью атрибутов просмотра отладчика](http://msdn.microsoft.com/library/72bb7aa9-459b-42c4-9163-9312fab4c410)




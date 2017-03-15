---
title: "Отображение пользовательских типов данных | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.data.elements"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "autoexp.dat - файл"
  - "пользовательские типы данных"
  - "типы данных [C#], пользовательский"
  - "отладчик, расширение типов данных"
  - "управляемый код, пользовательские типы данных"
  - "mcee_cs.dat - файл"
  - "mcee_mc.dat - файл"
ms.assetid: 9969e9b2-9008-4729-8a14-0d6deaa61576
caps.latest.revision: 34
caps.handback.revision: 34
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Отображение пользовательских типов данных
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Можно настроить то, как Visual Studio отображает типы данных в окнах переменных отладчика.  
  
## Атрибуты  
 В C\# и Visual Basic можно добавлять расширения для пользовательских данных с помощью <xref:System.Diagnostics.DebuggerTypeProxyAttribute>, <xref:System.Diagnostics.DebuggerDisplayAttribute> и <xref:System.Diagnostics.DebuggerBrowsableAttribute>.  
  
 Visual Basic не поддерживает атрибут DebuggerBrowsable в случае кода для [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)].  Это ограничение устранено в более новых версиях платформы .NET Framework.  
  
## Визуализаторы  
 Можно написать визуализатор для отображения любого управляемого типа.  Дополнительные сведения см. в разделе [Практическое руководство. Написание визуализатора](../debugger/how-to-write-a-visualizer.md).  
  
## Машинный код  
 Для машинного кода можно добавлять расширения пользовательских типов данных в файл autoexp.dat, который находится в каталоге "Program Files\\Microsoft Visual Studio 11.0\\Common7\\Packages\\Debugger".  Инструкции относительно записи в `autoexp` правил автоматического использования, расположены в этом файле.  
  
> [!CAUTION]
>  Структура этого файла, а также синтаксис правил автоматического использования могут изменяться от одного выпуска Visual Studio к другому.  
  
 Отображение машинного типа можно также настроить путем написания надстройки — вычислителя выражений. Дополнительные сведения см. в разделе \<link xlink:href\="d4f6b068\-c812\-45bc\-9ec0\-7e0363c4bb9e"\>EEAddIn Sample: Debugging Expression Evaluator Add\-In\<\/link\>.  Дополнительные сведения см. в разделе [EEAddIn Sample: Debugging Expression Evaluator Add\-In](http://msdn.microsoft.com/ru-ru/d4f6b068-c812-45bc-9ec0-7e0363c4bb9e).  
  
## См. также  
 [Использование атрибута DebuggerTypeProxy](../debugger/using-debuggertypeproxy-attribute.md)   
 [Использование атрибута DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md)   
 [Окна "Контрольные значения" и "Быстрая проверка"](../debugger/watch-and-quickwatch-windows.md)   
 [Enhancing Debugging with the Debugger Display Attributes](../Topic/Enhancing%20Debugging%20with%20the%20Debugger%20Display%20Attributes.md)
---
title: "Диалоговое окно &quot;Попадание в точку останова&quot; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.whenbreakpointishit"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "JScript"
  - "SQL"
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: 476e3d98-cf35-4338-b124-cd0f3010d854
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# Диалоговое окно &quot;Попадание в точку останова&quot;
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

С помощью этого диалогового окна можно произвести настройку действия, выполняемого при достижении точки останова.  
  
## Список элементов пользовательского интерфейса  
 **Напечатать сообщение**  
 Печатает сообщение, используя синтаксис DebuggerDisplay.  Дополнительные сведения см. в разделе [Использование атрибута DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md).  
  
 Это текстовое поле также поддерживает специальные ключевые слова \(например, $ADDRESS\), которые можно использовать без дополнительных параметров или заключать в фигурные скобки выражений DebuggerDisplay.  Доступные ключевые слова перечислены в диалоговом окне.  
  
 **Продолжить выполнение**  
 Данный элемент управления доступен только в том случае, когда выбран параметр **Напечатать сообщение**.  При выборе указанного элемента управления точку останова можно использовать в качестве точки трассировки для отслеживания выполнения программы вместо останова при достижении точки.  
  
## См. также  
 [Использование точек останова](../debugger/using-breakpoints.md)   
 [Использование атрибута DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md)
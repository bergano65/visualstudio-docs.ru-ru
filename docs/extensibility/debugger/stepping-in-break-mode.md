---
title: "Пошаговое выполнение в режиме приостановки выполнения | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "режим приостановки выполнения, пошаговое выполнение"
  - "Пошаговое выполнение, в режиме приостановки выполнения"
  - "отладка [пакет SDK для отладки], пошаговое выполнение в режиме приостановки выполнения"
ms.assetid: b08dc8ee-6c63-4462-a097-6f525cfbb35a
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# Пошаговое выполнение в режиме приостановки выполнения
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Далее описывается процесс, который происходит, когда отладчик в режиме приостановки выполнения и пошаговое выполнение кода:  
  
## Процесс пошагового выполнения  
  
1.  Вызов [IDebugProgram2:: Шаг](../../extensibility/debugger/reference/idebugprogram2-step.md) с  [STEPKIND](../../extensibility/debugger/reference/stepkind.md) и  [STEPUNIT](../../extensibility/debugger/reference/stepunit.md) аргументы для выполнения шага.  
  
2.  Если шаг завершен, отправьте IDebugStepCompleteEvent2 например, при остановке событие.  
  
## См. также  
 [Вызов события отладчика](../../extensibility/debugger/calling-debugger-events.md)
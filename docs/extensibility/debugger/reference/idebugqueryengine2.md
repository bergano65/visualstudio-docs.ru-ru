---
title: "IDebugQueryEngine2 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugQueryEngine2"
helpviewer_keywords: 
  - "Интерфейс IDebugQueryEngine2"
ms.assetid: 8f0e1838-a818-4459-9138-a3dceb7408de
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugQueryEngine2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Этот интерфейс позволяет сеансу отладки \(SDM\) диспетчер извлекает интерфейс, представляющий обработчик отладки \(DE\).  
  
## Синтаксис  
  
```  
IDebugQueryEngine2 : IUnknown  
```  
  
## Примечания по реализации  
 DE реализует этот интерфейс для объектов, которые реализуют интерфейс \(например наиболее распространенным DE [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)"  [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)и  [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)разрешить доступ\)  [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) сам интерфейс DE.  
  
## Замечания для вызывающих объектов  
 Вызов QueryInterface в типичном DE интерфейсе для получения этого интерфейса.  
  
## Методы в том порядке Vtable  
 В следующей таблице показаны методы `IDebugQueryEngine2`.  
  
|Метод|Описание|  
|-----------|--------------|  
|[GetEngineInterface](../Topic/IDebugQueryEngine2::GetEngineInterface.md)|Возвращает пользовательский интерфейс обработчика отладки \(DE\).|  
  
## Заметки  
 Этот интерфейс обычно реализуется в объекте, реализующий IDebugProgram2 интерфейс поддержки причинност\-приказанный пошаговое выполнение функций; то есть, если отладчик шагает из функций, следующая функция, которую необходимо выполнить, не может быть функцией предыдущей функции в стеке, а в другом потоке.  Для определения причинности "," см. в разделе [Глоссарий отладчика Visual Studio](../../../extensibility/debugger/reference/visual-studio-debugger-glossary.md).  
  
## Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## См. также  
 [Базовых интерфейсов](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)   
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
---
title: "Интерфейс IDebugStackFrame | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugStackFrame — интерфейс"
ms.assetid: e95c1b4f-17c1-490c-a56b-c25fa45d4822
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Интерфейс IDebugStackFrame
Представляет логический кадр стека в стеке потока.  Вызовите метод `IDebugStackFrame::QueryInterface` чтобы получить интерфейс `IDebugExpressionContext`, который позволяет окна вычисления выражений и контрольные значения.  
  
 В дополнение к методам, наследуемым от интерфейса `IUnknown`, интерфейс `IDebugStackFrame` предоставляет следующие методы.  
  
## Методы в порядке таблицы Vtable  
  
|Метод|Описание|  
|-----------|--------------|  
|[IDebugStackFrame::GetCodeContext](../../winscript/reference/idebugstackframe-getcodecontext.md)|Возвращает текущий контекст кода, связанный с данным кадром стека.|  
|[IDebugStackFrame::GetDescriptionString](../../winscript/reference/idebugstackframe-getdescriptionstring.md)|Возвращает короткое или подробное текстовое описание кадра стека.|  
|[IDebugStackFrame::GetLanguageString](../../winscript/reference/idebugstackframe-getlanguagestring.md)|Возвращает короткое или long текстовое описание языка.|  
|[IDebugStackFrame::GetThread](../../winscript/reference/idebugstackframe-getthread.md)|Возвращает поток, связанный с данным кадром стека.|  
|[IDebugStackFrame::GetDebugProperty](../../winscript/reference/idebugstackframe-getdebugproperty.md)|Возвращает обозреватель свойств для текущего кадра.|
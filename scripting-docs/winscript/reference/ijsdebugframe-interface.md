---
title: "Интерфейс IJsDebugFrame | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 5af46b18-9d25-4a23-b8d1-fa23bea3efcf
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# Интерфейс IJsDebugFrame
Предоставляет кадр стека.  
  
## Синтаксис  
  
```  
IJsDebugFrame : public IUnknown;  
```  
  
## Члены  
  
### Открытые методы  
  
|Имя|Описание|  
|---------|--------------|  
|[Метод IJsDebugFrame::Evaluate](../../winscript/reference/ijsdebugframe-evaluate-method.md)|Вычисляет выражение в контексте этого кадра стека.|  
|[Метод IJsDebugFrame::GetDebugProperty](../../winscript/reference/ijsdebugframe-getdebugproperty-method.md)|Возвращает браузер свойств для данного фрейма стеков.|  
|[Метод IJsDebugFrame::GetDocumentPositionWithId](../../winscript/reference/ijsdebugframe-getdocumentpositionwithid-method.md)|Возвращает текущее положение этого кадра стека в пределах пользовательского документа.|  
|[Метод IJsDebugFrame::GetDocumentPositionWithName](../../winscript/reference/ijsdebugframe-getdocumentpositionwithname-method.md)|Возвращает текущее положение этого кадра стека в пределах пользовательского документа.|  
|[Метод IJsDebugFrame::GetName](../../winscript/reference/ijsdebugframe-getname-method.md)|Возвращает понятное имя кадра стека.|  
|[Метод IJsDebugFrame::GetReturnAddress](../../winscript/reference/ijsdebugframe-getreturnaddress-method.md)|Получает обратный адрес, отправленный в "начале" \(см. GetStackRange\) кадра.|  
|[Метод IJsDebugFrame::GetStackRange](../../winscript/reference/ijsdebugframe-getstackrange-method.md)|Возвращает диапазон абсолютных адресов логического фрейма стеков JavaScript.|  
  
## Требования  
 **Заголовок:** jscript9diag.h  
  
## См. также  
 [Справочник по интерфейсам скриптов Windows](../../winscript/reference/windows-script-interfaces-reference.md)
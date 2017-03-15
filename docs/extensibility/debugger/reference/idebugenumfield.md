---
title: "IDebugEnumField | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugEnumField"
helpviewer_keywords: 
  - "Интерфейс IDebugEnumField"
ms.assetid: 42f685bf-0f39-47f4-98b0-6022efe2bf97
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugEnumField
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Этот интерфейс представляет тип перечисления.  
  
## Синтаксис  
  
```  
IDebugEnumField : IDebugContainerField  
```  
  
## Примечания по реализации  
 Поставщик символов реализующий этот интерфейс, чтобы представить перечисление.  
  
## Замечания для вызывающих объектов  
 Используйте [QueryInterface](/visual-cpp/atl/queryinterface) получить этот интерфейс с  [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) если интерфейс  [GetKind](../Topic/IDebugField::GetKind.md) возвращает  `FIELD_TYPE_ENUM`.  
  
## Методы в том порядке VTable  
 в дополнение к методам на `IDebugField` и  `IDebugContainerField` интерфейсы этот интерфейс реализуется следующие методы:  
  
|Метод|Описание|  
|-----------|--------------|  
|[GetUnderlyingSymbol](../../../extensibility/debugger/reference/idebugenumfield-getunderlyingsymbol.md)|Возвращает IDebugField описание имя данного типа перечисления.|  
|[GetStringFromValue](../../../extensibility/debugger/reference/idebugenumfield-getstringfromvalue.md)|Возвращает имя константы перечисления, связанной с данным значением.|  
|[GetValueFromString](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstring.md)|Возвращает значение, связанное с заданным именем констант перечисления|  
|[GetValueFromStringCaseInsensitive](../Topic/IDebugEnumField::GetValueFromStringCaseInsensitive.md)|Возвращает значение, связанное с заданным именем констант перечисления, но пропущено регистр.|  
  
## Заметки  
 Базовый символ, фактически выполняет привязку к местоположению с [Привязка](../../../extensibility/debugger/reference/idebugbinder-bind.md).  
  
## Требования  
 Заголовок: sh.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## См. также  
 [Интерфейсы поставщика символов](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [Привязка](../../../extensibility/debugger/reference/idebugbinder-bind.md)
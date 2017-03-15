---
title: "IDebugPointerField | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugPointerField"
helpviewer_keywords: 
  - "Интерфейс IDebugPointerField"
ms.assetid: d51bd5b2-f18e-4e27-b4fb-e6f652fbf635
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugPointerField
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Этот интерфейс представляет тип указателя.  
  
## Синтаксис  
  
```  
IDebugPointerField : IDebugContainerField  
```  
  
## Примечания по реализации  
 Поставщик символов реализует этот интерфейс для представления указателя.  
  
## Замечания для вызывающих объектов  
 Используйте [QueryInterface](/visual-cpp/atl/queryinterface) получить этот интерфейс с  [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) если интерфейс  [GetKind](../Topic/IDebugField::GetKind.md) возвращает  `FIELD_TYPE_POINTER`.  
  
## Методы в том порядке Vtable  
 в дополнение к методам на `IDebugField` и  `IDebugContainerField` интерфейсы, этот интерфейс реализован следующий метод:  
  
|Метод|Описание|  
|-----------|--------------|  
|[GetDereferencedField](../../../extensibility/debugger/reference/idebugpointerfield-getdereferencedfield.md)|Возвращает IDebugField описание целевой объект указателя.|  
  
## Заметки  
 В C\/C\+\+, указатель может быть контейнером, если он используется, используя нотацию массива.  Например, при наличии `char *pString`"  `pString` тип указателя на  `char`.  `pString[3]` имеет тип контейнера, указатель  `char` он ссылается на четвертый элемент контейнера.  
  
## Требования  
 Заголовок: sh.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## См. также  
 [Интерфейсы поставщика символов](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)
---
title: "IDebugClassField | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugClassField"
helpviewer_keywords: 
  - "Интерфейс IDebugClassField"
ms.assetid: 49358cbc-8973-4862-9dcc-79b1248e6712
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugClassField
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Этот интерфейс представляет класс как тип.  
  
## Синтаксис  
  
```  
IDebugClassField : IDebugContainerField  
```  
  
## Примечания по реализации  
 Поставщик символов реализует этот интерфейс на одном и том же объекта, реализующего [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) интерфейс.  Этот интерфейс специализация, представляющий тип класса.  
  
## Замечания для вызывающих объектов  
 Несколько интерфейсов имеют методы, которые может вернуть этот интерфейс, в том числе [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)"  [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)и  [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md).  Также можно воспользоваться [QueryInterface](/visual-cpp/atl/queryinterface) получить этот интерфейс с  [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) если интерфейс  [GetKind](../Topic/IDebugField::GetKind.md) метод возвращает пометить  `FIELD_TYPE_CLASS`.  
  
## Методы в том порядке Vtable  
 в дополнение к методам на [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) и  [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) интерфейсы, этот интерфейс, реализующих следующее:  
  
|Метод|Описание|  
|-----------|--------------|  
|[EnumBaseClasses](../Topic/IDebugClassField::EnumBaseClasses.md)|Создает перечислитель для базовых классов этого класса.|  
|[DoesInterfaceExist](../../../extensibility/debugger/reference/idebugclassfield-doesinterfaceexist.md)|Определяет, определен в классе определенный интерфейс.|  
|[EnumNestedClasses](../../../extensibility/debugger/reference/idebugclassfield-enumnestedclasses.md)|Создает перечислитель для вложенных классов этого класса.|  
|[GetEnclosingClass](../../../extensibility/debugger/reference/idebugclassfield-getenclosingclass.md)|Возвращает класс, ограничивающий данный класс.|  
|[EnumInterfacesImplemented](../Topic/IDebugClassField::EnumInterfacesImplemented.md)|Создает перечислитель для интерфейсов, реализованных этим классом.|  
|[EnumConstructors](../../../extensibility/debugger/reference/idebugclassfield-enumconstructors.md)|Создает перечислитель для конструкторов этого класса.|  
|[GetDefaultIndexer](../../../extensibility/debugger/reference/idebugclassfield-getdefaultindexer.md)|Возвращает имя по умолчанию индексатора.|  
|[EnumNestedEnums](../../../extensibility/debugger/reference/idebugclassfield-enumnestedenums.md)|Создает перечислитель для вложенных перечислителей этого класса.|  
  
## Требования  
 Заголовок: sh.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## См. также  
 [Интерфейсы поставщика символов](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)
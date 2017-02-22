---
title: "IDebugCustomAttributeQuery2 | Microsoft Docs"
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
  - "IDebugCustomAttributeQuery2"
helpviewer_keywords: 
  - "Интерфейс IDebugCustomAttributeQuery"
  - "Интерфейс IDebugCustomAttributeQuery2"
ms.assetid: 7cfa23e4-a05a-47a3-af6c-bd40c655014b
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugCustomAttributeQuery2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Определяет наличие настраиваемых атрибутов для этого поля и, если он существует, то возвращается информация атрибутов.  
  
## Синтаксис  
  
```  
IDebugCustomAttributeQuery2 : IDebugCustomAttributeQuery  
```  
  
## Примечания по реализации  
 Поставщик символов реализует этот интерфейс на одном и том же объекта, реализующего IDebugField поддерживать настраиваемые атрибуты.  
  
## Замечания для вызывающих объектов  
 Используйте [QueryInterface](/visual-cpp/atl/queryinterface) получить этот интерфейс с  [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) интерфейс.  
  
## Методы в том порядке Vtable  
 В следующей таблице показаны методы IDebugCustomAttributeQuery интерфейс.  
  
|Метод|Описание|  
|-----------|--------------|  
|[IsCustomAttributeDefined](../../../extensibility/debugger/reference/idebugcustomattributequery2-iscustomattributedefined.md)|Определяет, существует ли настраиваемый атрибут по имени.|  
|[GetCustomAttributeByName](../Topic/IDebugCustomAttributeQuery2::GetCustomAttributeByName.md)|Получает данные атрибута для заданного настраиваемого атрибута.|  
  
 Помимо **IDebugCustomAttributeQuery** методы  `IDebugCustomAttributeQuery2` реализован следующий метод:  
  
|Метод|Описание|  
|-----------|--------------|  
|[EnumCustomAttributes](../../../extensibility/debugger/reference/idebugcustomattributequery2-enumcustomattributes.md)|Возвращает перечислитель для всех настраиваемых атрибутов, вложенных в это поле.|  
  
## Заметки  
 [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md) метод может возвратить перечислитель для всех настраиваемых атрибутов, определенных для данного поля.  
  
## Требования  
 Заголовок: sh.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## См. также  
 [Интерфейсы поставщика символов](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)
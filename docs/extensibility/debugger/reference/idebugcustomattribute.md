---
title: "IDebugCustomAttribute | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugCustomAttribute"
helpviewer_keywords: 
  - "Интерфейс IDebugCustomAttribute"
ms.assetid: c5ae41e9-00b9-4cca-871d-b8de9ef390d1
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# IDebugCustomAttribute
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Этот интерфейс представляет настраиваемый атрибут, и он может предоставить имя родительского класса, а тип атрибута.  
  
## Синтаксис  
  
```  
IDebugCustomAttribute : IUnknown  
```  
  
## Примечания по реализации  
 Поставщик символов реализующий этот интерфейс, чтобы поддерживать настраиваемые атрибуты, связанные с символом.  Обычно он реализован в собственном объекте.  
  
## Замечания для вызывающих объектов  
 Вызов [Далее](../../../extensibility/debugger/reference/ienumdebugcustomattributes-next.md) возвращает данный интерфейс.  Вызов [EnumCustomAttributes](../../../extensibility/debugger/reference/idebugcustomattributequery2-enumcustomattributes.md) метод возвращает  [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md) интерфейс.  
  
## Методы в том порядке Vtable  
 В следующей таблице показаны методы `IDebugCustomAttribute`.  
  
|Метод|Описание|  
|-----------|--------------|  
|[GetParentField](../Topic/IDebugCustomAttribute::GetParentField.md)|Получает поле, в который вложен текущий атрибут.|  
|[GetAttributeTypeField](../../../extensibility/debugger/reference/idebugcustomattribute-getattributetypefield.md)|Возвращает тип класса настраиваемого атрибута.|  
|[GetName](../../../extensibility/debugger/reference/idebugcustomattribute-getname.md)|Возвращает имя настраиваемого атрибута.|  
|[GetAttributeBytes](../../../extensibility/debugger/reference/idebugcustomattribute-getattributebytes.md)|Получает данные атрибута как большой двоичный объект байтов.|  
  
## Заметки  
 Настраиваемый атрибут структура для c\#, которое содержит пользовательские метаданные, связанные с указанным классом или методом.  
  
## Требования  
 Заголовок: sh.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## См. также  
 [Интерфейсы поставщика символов](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)   
 [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)
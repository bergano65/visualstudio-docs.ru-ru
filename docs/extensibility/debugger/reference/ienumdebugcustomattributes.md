---
title: "IEnumDebugCustomAttributes | Microsoft Docs"
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
  - "IEnumCustomAttributes"
helpviewer_keywords: 
  - "Интерфейс IEnumDebugCustomAttributes"
ms.assetid: 11aa768d-1852-44d6-9de3-17f9bafaded2
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# IEnumDebugCustomAttributes
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Перечисляет настраиваемые атрибуты.  
  
## Синтаксис  
  
```  
IEnumCustomAttributes : IUnknown  
```  
  
## Примечания по реализации  
 Поставщик символов реализующий этот интерфейс, чтобы поддерживать настраиваемые атрибуты \(посредством [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md) интерфейс\).  
  
## Замечания для вызывающих объектов  
 [EnumCustomAttributes](../../../extensibility/debugger/reference/idebugcustomattributequery2-enumcustomattributes.md) возвращает данный интерфейс.  
  
## Методы в том порядке Vtable  
 В следующей таблице показаны методы `IEnumDebugCustomAttributes`.  
  
|Метод|Описание|  
|-----------|--------------|  
|[Далее](../../../extensibility/debugger/reference/ienumdebugcustomattributes-next.md)|Извлекает заданное количество настраиваемых атрибутов в последовательности перечисления.|  
|[Пропустить](../../../extensibility/debugger/reference/ienumdebugcustomattributes-skip.md)|Пропустить указанное количество настраиваемых атрибутов в последовательности перечисления.|  
|[Сбросить](../../../extensibility/debugger/reference/ienumdebugcustomattributes-reset.md)|Сбросить последовательность перечисления в начало.|  
|[Клонировать](../Topic/IEnumDebugCustomAttributes::Clone.md)|Создает перечислитель с тем же состоянием перечисления, что и текущий перечислитель.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugcustomattributes-getcount.md)|Возвращает количество настраиваемых атрибутов в перечислителе.|  
  
## Требования  
 Заголовок: sh.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## См. также  
 [Интерфейсы поставщика символов](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [EnumCustomAttributes](../../../extensibility/debugger/reference/idebugcustomattributequery2-enumcustomattributes.md)   
 [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)
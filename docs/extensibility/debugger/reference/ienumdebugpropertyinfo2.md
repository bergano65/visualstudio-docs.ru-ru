---
title: "IEnumDebugPropertyInfo2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEnumDebugPropertyInfo2"
helpviewer_keywords: 
  - "IEnumDebugPropertyInfo2"
ms.assetid: fdea8262-40b8-473e-88ba-639e4c4648e6
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IEnumDebugPropertyInfo2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Этот интерфейс перечисляет [DEBUG\_PROPERTY\_INFO](../../../extensibility/debugger/reference/debug-property-info.md) структуры.  
  
## Синтаксис  
  
```  
IEnumDebugPropertyInfo2 : IUnknown  
```  
  
## Примечания по реализации  
 Отладчик \(DE\) реализует этот интерфейс для представления сведений для указанного свойства.  
  
## Замечания для вызывающих объектов  
 Вызов [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) получить этот интерфейс, представляющий дочерние элементы указанного свойства.  Вызов [EnumProperties](../Topic/IDebugStackFrame2::EnumProperties.md) получить этот интерфейс, представляющий свойства, определенного кадра стека.  
  
## Методы в том порядке Vtable  
 В следующей таблице показаны методы `IEnumDebugPropertyInfo2`.  
  
|Метод|Описание|  
|-----------|--------------|  
|[Далее](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-next.md)|Получает заданное число [DEBUG\_PROPERTY\_INFO](../../../extensibility/debugger/reference/debug-property-info.md) структуры в последовательности перечисления.|  
|[Пропустить](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-skip.md)|Пропустить заданное число [DEBUG\_PROPERTY\_INFO](../../../extensibility/debugger/reference/debug-property-info.md) структуры в последовательности перечисления.|  
|[Сбросить](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-reset.md)|Сбросить последовательность перечисления в начало.|  
|[Клонировать](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-clone.md)|Создает перечислитель с тем же состоянием перечисления, что и текущий перечислитель.|  
|[GetCount](../Topic/IEnumDebugPropertyInfo2::GetCount.md)|Получает число [DEBUG\_PROPERTY\_INFO](../../../extensibility/debugger/reference/debug-property-info.md) структуры в перечислителе.|  
  
## Заметки  
 Обычно свойство иерархия информацию, которая может включать имя, значение и тип, адрес, а также любого другого сведения соответствующего к связанным объектом или кадр стека свойства.  Дополнительные сведения см. в разделе [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md).  
  
## Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## См. также  
 [Базовых интерфейсов](../../../extensibility/debugger/reference/core-interfaces.md)   
 [DEBUG\_PROPERTY\_INFO](../../../extensibility/debugger/reference/debug-property-info.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)   
 [EnumProperties](../Topic/IDebugStackFrame2::EnumProperties.md)
---
title: "IEnumDebugPortSuppliers2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEnumDebugPortSuppliers2"
helpviewer_keywords: 
  - "IEnumDebugPortSuppliers2"
ms.assetid: cd0a73dc-dd25-46fd-8c4f-5b011501afeb
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# IEnumDebugPortSuppliers2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Этот интерфейс перечисляет поставщиков портов.  
  
## Синтаксис  
  
```  
IEnumDebugPortSuppliers2 : IUnknown  
```  
  
## Примечания по реализации  
 Visual Studio реализующий этот интерфейс, чтобы представлять список поставщиков портов.  
  
## Замечания для вызывающих объектов  
 Вызов [EnumPortSuppliers](../../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md) получить список поставщиков портов.  
  
## Методы в том порядке Vtable  
 В следующей таблице показаны методы `IEnumDebugPortSuppliers2`.  
  
|Метод|Описание|  
|-----------|--------------|  
|[Далее](../Topic/IEnumDebugPortSuppliers2::Next.md)|Извлекает заданное количество поставщиков портов в последовательности перечисления.|  
|[Пропустить](../../../extensibility/debugger/reference/ienumdebugportsuppliers2-skip.md)|Пропустить указанное количество поставщиков портов в последовательности перечисления.|  
|[Сбросить](../../../extensibility/debugger/reference/ienumdebugportsuppliers2-reset.md)|Сбросить последовательность перечисления в начало.|  
|[Клонировать](../Topic/IEnumDebugPortSuppliers2::Clone.md)|Создает перечислитель с тем же состоянием перечисления, что и текущий перечислитель.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugportsuppliers2-getcount.md)|Возвращает количество поставщиков портов в перечислителе.|  
  
## Заметки  
 Обработчик отладки, как правило, не требуется получить этот интерфейс.  
  
## Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## См. также  
 [Базовых интерфейсов](../../../extensibility/debugger/reference/core-interfaces.md)   
 [EnumPortSuppliers](../../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md)
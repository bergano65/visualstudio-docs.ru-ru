---
title: "IEnumDebugModules2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEnumDebugModules2"
helpviewer_keywords: 
  - "IEnumDebugModules2"
ms.assetid: 4fe28074-a960-41ad-b74d-b57f04c0c0ad
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IEnumDebugModules2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Этот интерфейс перечисляет список модулей.  
  
## Синтаксис  
  
```  
IEnumDebugModules2 : IUnknown  
```  
  
## Примечания по реализации  
 Отладчик \(DE\) реализует этот интерфейс, чтобы представлять список модулей, загруженных для программы.  
  
## Замечания для вызывающих объектов  
 Вызовы Visual Studio [EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md) получить этот интерфейс.  
  
## Методы в том порядке Vtable  
 В следующей таблице показаны методы `IEnumDebugModules2`.  
  
|Метод|Описание|  
|-----------|--------------|  
|[Далее](../../../extensibility/debugger/reference/ienumdebugmodules2-next.md)|Извлекает заданное количество модулей в последовательности перечисления.|  
|[Пропустить](../../../extensibility/debugger/reference/ienumdebugmodules2-skip.md)|Пропустить указанное количество модулей в последовательности перечисления.|  
|[Сбросить](../Topic/IEnumDebugModules2::Reset.md)|Сбросить последовательность перечисления в начало.|  
|[Клонировать](../../../extensibility/debugger/reference/ienumdebugmodules2-clone.md)|Создает перечислитель с тем же состоянием перечисления, что и текущий перечислитель.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugmodules2-getcount.md)|Возвращает количество модулей.|  
  
## Заметки  
 Visual Studio использует этот интерфейс в основном для обновления **Модули** окна.  
  
 Для отладки в Visual Studio, программа логическая последовательность инструкций кода, которые могут пересекать границы модуля, поэтому необходимость список модулей для отдельного IDebugProgram2 интерфейс.  Первый модуль в списке обычно содержит исходную точку входа для соответствующей программы.  
  
## Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## См. также  
 [Базовых интерфейсов](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md)
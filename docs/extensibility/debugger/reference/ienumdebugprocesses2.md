---
title: "IEnumDebugProcesses2 | Microsoft Docs"
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
  - "IEnumDebugProcesses2"
helpviewer_keywords: 
  - "IEnumDebugProcesses2"
ms.assetid: 06a1368f-10f0-44eb-af61-e388c2327111
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# IEnumDebugProcesses2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Этот интерфейс перечисляет процессами, запущенными на порт отладки.  
  
## Синтаксис  
  
```  
IEnumDebugProcesses : IUnknown  
```  
  
## Примечания по реализации  
 Пользовательский поставщик порта, реализующий этот интерфейс, чтобы предоставить список процессов, запущенных на порт.  
  
## Замечания для вызывающих объектов  
 Вызовы Visual Studio [EnumProcesses](../Topic/IDebugPort2::EnumProcesses.md) получить этот интерфейс.  
  
## Методы в том порядке Vtable  
 В следующей таблице показаны методы `IEnumDebugProcesses2`.  
  
|Метод|Описание|  
|-----------|--------------|  
|[Далее](../../../extensibility/debugger/reference/ienumdebugprocesses2-next.md)|Получает заданное число процессов в последовательности перечисления.|  
|[Пропустить](../../../extensibility/debugger/reference/ienumdebugprocesses2-skip.md)|Пропустить заданное число процессов в последовательности перечисления.|  
|[Сбросить](../../../extensibility/debugger/reference/ienumdebugprocesses2-reset.md)|Сбросить последовательность перечисления в начало.|  
|[Клонировать](../Topic/IEnumDebugProcesses2::Clone.md)|Создает перечислитель с тем же состоянием перечисления, что и текущий перечислитель.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugprocesses2-getcount.md)|Получает число процессов в перечислителе.|  
  
## Заметки  
 Visual Studio использует этот интерфейс для заполнения **Процессы** окна.  
  
## Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## См. также  
 [Базовых интерфейсов](../../../extensibility/debugger/reference/core-interfaces.md)   
 [EnumProcesses](../Topic/IDebugPort2::EnumProcesses.md)
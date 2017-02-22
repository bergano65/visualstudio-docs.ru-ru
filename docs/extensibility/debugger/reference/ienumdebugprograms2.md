---
title: "IEnumDebugPrograms2 | Microsoft Docs"
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
  - "IEnumDebugPrograms2"
helpviewer_keywords: 
  - "IEnumDebugPrograms2"
ms.assetid: 7fbb8fb7-db64-4546-a364-dc668430c8af
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IEnumDebugPrograms2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Этот интерфейс перечисляет программ, запущенных на протяжении сеанса отладки.  
  
## Синтаксис  
  
```  
IEnumDebugPrograms2 : IUnknown  
```  
  
## Примечания по реализации  
 Отладчик \(DE\) реализует этот интерфейс, чтобы предоставить список отлаживаемых программ " ив.  
  
## Замечания для вызывающих объектов  
 Вызовы Visual Studio [EnumPrograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md) получить этот интерфейс.  [EnumPrograms](../../../extensibility/debugger/reference/idebugengine2-enumprograms.md) не использует Visual Studio.  
  
## Методы в том порядке Vtable  
 В следующей таблице показаны методы `IEnumDebugPrograms2`.  
  
|Метод|Описание|  
|-----------|--------------|  
|[Далее](../Topic/IEnumDebugPrograms2::Next.md)|Извлекает заданное количество служебных программ в последовательности перечисления.|  
|[Пропустить](../../../extensibility/debugger/reference/ienumdebugprograms2-skip.md)|Пропустить указанное количество служебных программ в последовательности перечисления.|  
|[Сбросить](../../../extensibility/debugger/reference/ienumdebugprograms2-reset.md)|Сбросить последовательность перечисления в начало.|  
|[Клонировать](../Topic/IEnumDebugPrograms2::Clone.md)|Создает перечислитель с тем же состоянием перечисления, что и текущий перечислитель.|  
|[GetCount](../Topic/IEnumDebugPrograms2::GetCount.md)|Возвращает количество служебных программ в перечислителе.|  
  
## Заметки  
 Visual Studio использует этот интерфейс.  
  
-   Заполнение **Модули** окно \(путем вызова  [EnumPrograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md) затем вызов  [EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md) в каждой программе\).  
  
-   Заполнение **Присоединение к процессу** поля \(путем вызова  `IDebugProcess2::EnumPrograms` затем вызов  [QueryInterface](/visual-cpp/atl/queryinterface) на каждом  [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) интерфейс для получения  [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md) интерфейс\).  
  
-   Создание списка DEs, который может отлаживать каждую программу в процессе \(использование [GetEngineInfo](../../../extensibility/debugger/reference/idebugprogram2-getengineinfo.md)\).  
  
-   Примените правка и продолжите операцию обновления \(ENCL\) в каждой программе \(путем вызова IDebugProcess2:: EnumPrograms а затем вызвать [GetENCUpdate](../../../extensibility/debugger/reference/idebugprogram2-getencupdate.md)\).  
  
## Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## См. также  
 [Базовых интерфейсов](../../../extensibility/debugger/reference/core-interfaces.md)   
 [EnumPrograms](../../../extensibility/debugger/reference/idebugengine2-enumprograms.md)   
 [EnumPrograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md)
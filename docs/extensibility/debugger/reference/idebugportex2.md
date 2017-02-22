---
title: "IDebugPortEx2 | Microsoft Docs"
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
  - "IDebugPortEx2"
helpviewer_keywords: 
  - "Интерфейс IDebugPortEx2"
ms.assetid: 144724d0-38ee-4c9b-87ca-8a504371182b
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugPortEx2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Этот интерфейс позволяет сеансу отладки элемент управления диспетчера \(SDM\) программы и процессами, запущенными на порт.  
  
## Синтаксис  
  
```  
IDebugPortEx2 : IUnknown  
```  
  
## Примечания по реализации  
 Пользовательский поставщик порта, реализующего этот интерфейс для одного и того же объекта, реализующего IDebugPort2.  
  
## Замечания для вызывающих объектов  
 Вызовы SDM [QueryInterface](/visual-cpp/atl/queryinterface) на  `IDebugPort2` интерфейс для получения этого интерфейса.  
  
## Методы в том порядке Vtable  
 В следующей таблице показаны методы `IDebugPortEx2`.  
  
|Метод|Описание|  
|-----------|--------------|  
|[LaunchSuspended](../../../extensibility/debugger/reference/idebugportex2-launchsuspended.md)|Запустит исполняемый файл.|  
|[ResumeProcess для](../../../extensibility/debugger/reference/idebugportex2-resumeprocess.md)|Возобновляет выполнение процесса ".|  
|[CanTerminateProcess](../../../extensibility/debugger/reference/idebugportex2-canterminateprocess.md)|Определяет, является ли процесс может быть завершен.|  
|[TerminateProcess](../../../extensibility/debugger/reference/idebugportex2-terminateprocess.md)|Завершает процесс.|  
|[GetPortProcessId](../../../extensibility/debugger/reference/idebugportex2-getportprocessid.md)|Получает идентификатор процесса самой порта.|  
|[GetProgram](../../../extensibility/debugger/reference/idebugportex2-getprogram.md)|Возвращает программу, связанный с узлом программы.|  
  
## Заметки  
 Этот интерфейс обычно является частным между SDM и пользовательским поставщиком порта.  
  
 Если необходимо, отладчик \(DE\) может искать этот интерфейс на [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) интерфейс, передаваемый  [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md) и использование  [LaunchSuspended](../../../extensibility/debugger/reference/idebugportex2-launchsuspended.md) запуск программы.  Это не является обязательным, но и DE может выполнять любые действия необходимо выполнить, чтобы запустить программу запроса.  
  
## Требования  
 Заголовок: portpriv.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## См. также  
 [Базовых интерфейсов](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
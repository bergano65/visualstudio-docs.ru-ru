---
title: "IDebugEngineLaunch2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugEngineLaunch2"
helpviewer_keywords: 
  - "Интерфейс IDebugEngineLaunch2"
ms.assetid: 5eaf2ad8-3fbf-446e-b48b-5327ad3f5255
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# IDebugEngineLaunch2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Используется обработчиком отладки \(DE\) для запуска и выполнения программы.  
  
## Синтаксис  
  
```  
IDebugEngineLaunch2 : IDebugEngine2  
```  
  
## Примечания по реализации  
 Этот интерфейс реализуется настраиваемым средством DE если он имеет особые требования для запуска процесса, который не может быть обработан весь пользовательским портом.  Обычно это случай, когда DE часть преобразователя и отлаживаемый процесс скрипт: переводчику должен запускаться первым, а затем скрипт загружен и запущен.  Порт может начинаться транслятор, но скрипт может потребоваться специальная обработка выпуска \(который, где DE имеет роль\).  Этот интерфейс реализуется только в том случае, если однозначно требования для запуска программы, которая нестандартного порта не может обработать.  
  
## Замечания для вызывающих объектов  
 Этот интерфейс, вызывается сеанса отладки \(SDM\), если диспетчер SDM может получить этот интерфейс с [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) интерфейс \(использование QueryInterface\).  Если этот интерфейс может быть получен, то SDM знает, что DE имеет особых требований и вызывает этот интерфейс, чтобы запустить программу, а не иметь запуск порта.  
  
## Методы в том порядке Vtable  
 В следующей таблице показаны методы `IDebugEngineLaunch2`.  
  
|Метод|Описание|  
|-----------|--------------|  
|[LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)|Запускает процесс посредством DE.|  
|[ResumeProcess для](../../../extensibility/debugger/reference/idebugenginelaunch2-resumeprocess.md)|Возобновляет выполнение процесса ".|  
|[CanTerminateProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-canterminateprocess.md)|Определяет, если процесс может быть завершен.|  
|[TerminateProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-terminateprocess.md)|Завершает процесс.|  
  
## Требования  
 Заголовок: Msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## См. также  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
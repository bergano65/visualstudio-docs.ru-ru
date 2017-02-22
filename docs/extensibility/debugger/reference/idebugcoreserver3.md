---
title: "IDebugCoreServer3 | Microsoft Docs"
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
  - "IDebugCoreServer3"
helpviewer_keywords: 
  - "Интерфейс IDebugCoreServer3"
ms.assetid: 51f5f41b-a5a4-4df0-a703-41f3d1811d7f
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugCoreServer3
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Этот интерфейс предоставляет доступ к сведениям о сервере выполняется процесс.  
  
## Синтаксис  
  
```  
IDebugCoreServer3 : IDebugCoreServer2  
```  
  
## Примечания по реализации  
 Visual Studio реализует этот интерфейс.  
  
## Замечания для вызывающих объектов  
 Используйте [QueryInterface](/visual-cpp/atl/queryinterface) получить этот интерфейс с  [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md) интерфейс.  Вызов [GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md) может также возвращать этот интерфейс.  Этот интерфейс используется чаще всего пользовательским поставщиком порта для запуска программы \(на сервере или локально или удаленно\).  
  
## Методы в том порядке Vtable  
 в дополнение к методам на [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md) интерфейс этот интерфейс реализует следующие методы:  
  
|Метод|Описание|  
|-----------|--------------|  
|[GetServerName](../../../extensibility/debugger/reference/idebugcoreserver3-getservername.md)|Извлекает имя сервера.|  
|[GetServerFriendlyName](../../../extensibility/debugger/reference/idebugcoreserver3-getserverfriendlyname.md)|Извлекает содружественная версия имени сервера|  
|[EnableAutoAttach](../../../extensibility/debugger/reference/idebugcoreserver3-enableautoattach.md)|Указывает обработчики отладки, специфичные для автоматического вложения к процессам при его запуске этих процессов.|  
|[DiagnoseWebDebuggingError](../Topic/IDebugCoreServer3::DiagnoseWebDebuggingError.md)|Получает конкретный код ошибки, если автоматическое вложение fail.|  
|[CreateInstanceInServer](../../../extensibility/debugger/reference/idebugcoreserver3-createinstanceinserver.md)|Создает экземпляр обработчика отладки на сервере.|  
|[QueryIsLocal](../../../extensibility/debugger/reference/idebugcoreserver3-queryislocal.md)|Извлекает пометить указывающее, является ли сервер на том же компьютере, что и вызывающий объект.|  
|[GetConnectionProtocol](../Topic/IDebugCoreServer3::GetConnectionProtocol.md)|Извлекает значение, указывающее протокол, используемого для связи с сервером.|  
|[DisableAutoAttach](../../../extensibility/debugger/reference/idebugcoreserver3-disableautoattach.md)|Отключить все автоматическ\-вложите параметры для всех обработчиков отладки этот сервер знает.|  
  
## Заметки  
 Пользовательский поставщик порта возвращает [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md) интерфейс при вызове функции  [Событие](../../../extensibility/debugger/reference/idebugportevents2-event.md).  `IDebugCoreServer3` интерфейс можно получить из этого интерфейса.  
  
## Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## См. также  
 [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)   
 [GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md)
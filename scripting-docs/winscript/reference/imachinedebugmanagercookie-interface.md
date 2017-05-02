---
title: "Интерфейс IMachineDebugManagerCookie | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IMachineDebugManagerCookie — интерфейс"
ms.assetid: 04770935-3ccf-41e9-b0c1-c78376ab1e3c
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Интерфейс IMachineDebugManagerCookie
Подобно интерфейсу `IMachineDebugManager`, поддержки интерфейса `IMachineDebugManagerCookie` отладочные файлы cookie.  
  
 Этот интерфейс \(вместе с интерфейсом `IDebugCookie` \) позволяет скрипты для запуска в процессе отладки скрипта, не требуя, что отладчик отслеживает этих скриптов.  
  
 Отладчик скриптов вызывает метод `IDebugCookie::SetDebugCookie` в диспетчере процесс отладки \(PDM\).  Затем PDM отправляет этот файл cookie вместе с любым запросом добавить или удалить приложение сценария или из диспетчера отладка компьютера \(MDM\), с помощью методов интерфейса `IMachineDebugManagerCookie`.  MDM затем уведомляет каждый отладчик изменения, кроме одного, которому принадлежит этот файл cookie.  
  
 В дополнение к методам, наследуемым от интерфейса `IUnknown`, интерфейс `IMachineDebugManagerCookie` предоставляет следующие методы.  
  
## Методы в порядке таблицы Vtable  
  
|Метод|Описание|  
|-----------|--------------|  
|[IMachineDebugManagerCookie::AddApplication](../../winscript/reference/imachinedebugmanagercookie-addapplication.md)|Добавляет приложение с выполняющимся список приложения.|  
|[IMachineDebugManagerCookie::EnumApplications](../../winscript/reference/imachinedebugmanagercookie-enumapplications.md)|Возвращает перечислитель для текущего списка выполняющихся приложений.|  
|[IMachineDebugManagerCookie::RemoveApplication](../../winscript/reference/imachinedebugmanagercookie-removeapplication.md)|Удаляет приложение из выполняющегося списка приложения.|  
  
## См. также  
 [Интерфейс IMachineDebugManager](../../winscript/reference/imachinedebugmanager-interface.md)   
 [Интерфейс IDebugCookie](../../winscript/reference/idebugcookie-interface.md)
---
title: "Интерфейс IRemoteDebugApplication | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IRemoteDebugApplication — интерфейс"
ms.assetid: 96bf2a3f-049f-46ba-86ad-57fc184343a2
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# Интерфейс IRemoteDebugApplication
Представляет запущенное приложение.  Для этого не требуется сопоставить к процессу операционной системы.  Обычно он предназначен для приложения для отладки.  Диспетчер процесса отладка обычно реализует объект приложения.  
  
 В дополнение к методам, наследуемым от интерфейса `IUnknown`, интерфейс `IRemoteDebugApplication` предоставляет следующие методы.  
  
## Методы в порядке таблицы Vtable  
  
|Метод|Описание|  
|-----------|--------------|  
|[IRemoteDebugApplication::ResumeFromBreakPoint](../../winscript/reference/iremotedebugapplication-resumefrombreakpoint.md)|Переход приложение, которое в данный момент в точке останова.|  
|[IRemoteDebugApplication::CauseBreak](../../winscript/reference/iremotedebugapplication-causebreak.md)|Заставляет приложение переключиться в режим отладчика при первой возможности.|  
|[IRemoteDebugApplication::ConnectDebugger](../../winscript/reference/iremotedebugapplication-connectdebugger.md)|Отладчик подключается к данному приложению.|  
|[IRemoteDebugApplication::DisconnectDebugger](../../winscript/reference/iremotedebugapplication-disconnectdebugger.md)|Отключает текущий режим отладчика из приложения.|  
|[IRemoteDebugApplication::GetDebugger](../../winscript/reference/iremotedebugapplication-getdebugger.md)|Возвращает текущий подключенный отладчик к приложению.|  
|[IRemoteDebugApplication::CreateInstanceAtApplication](../../winscript/reference/iremotedebugapplication-createinstanceatapplication.md)|Предоставляет механизм для интегрированной среды разработки отладчика, выполняющийся вне процесса к приложению, создания объектов в обработке приложения.|  
|[IRemoteDebugApplication::QueryAlive](../../winscript/reference/iremotedebugapplication-queryalive.md)|Указывает если приложение отзывчиво.|  
|[IRemoteDebugApplication::EnumThreads](../../winscript/reference/iremotedebugapplication-enumthreads.md)|Перечисляет все потоки известные, что быть связано с приложением.|  
|[IRemoteDebugApplication::GetName](../../winscript/reference/iremotedebugapplication-getname.md)|Получает имя узла приложения.|  
|[IRemoteDebugApplication::GetRootNode](../../winscript/reference/iremotedebugapplication-getrootnode.md)|Возвращает узел приложения, в котором добавитьы все узлы, связанные с приложением.|  
|[IRemoteDebugApplication::EnumGlobalExpressionContexts](../../winscript/reference/iremotedebugapplication-enumglobalexpressioncontexts.md)|Перечисляет глобальные контекстах выражения для всех языков, работающим в этом приложении.|
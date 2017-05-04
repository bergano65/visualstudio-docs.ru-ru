---
title: "IRemoteDebugApplicationEx — интерфейс | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IRemoteDebugApplicationEx — интерфейс"
ms.assetid: 8e16164d-dbb2-4488-9507-25ae34f343dc
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# IRemoteDebugApplicationEx — интерфейс
Представляет запущенное приложение.  Для этого не требуется сопоставить к процессу операционной системы.  Обычно он предназначен для приложения для отладки.  Диспетчер процесса отладка обычно реализует объект приложения.  
  
 В дополнение к методам, наследуемым от интерфейса `IUnknown`, интерфейс `IRemoteDebugApplicationEx` предоставляет следующие методы.  
  
## Методы в порядке таблицы Vtable  
  
|Метод|Описание|  
|-----------|--------------|  
|[IRemoteDebugApplicationEx:GetHostPid](../../winscript/reference/iremotedebugapplicationex-gethostpid.md)|Возвращает идентификатор процесса для ведущего приложения.|  
|GetHostMachineName|Возвращает имя компьютера, на котором выполняется ведущее приложение.|  
|[IRemoteDebugApplicationEx:SetLocale](../../winscript/reference/iremotedebugapplicationex-setlocale.md)|Задает язык для локализации отладчика.|  
|[IRemoteDebugApplicationEx:ForceStepMode](../../winscript/reference/iremotedebugapplicationex-forcestepmode.md)|Вызывает отладчик в режим единый\- шага.|  
|[IRemoteDebugApplicationEx:RevokeBreak](../../winscript/reference/iremotedebugapplicationex-revokebreak.md)|Отменяет команду прерывания.|  
|SetProxyBlanketAndAddRef|Сведения о безопасности COM обновлений на прокси\-сервере для объекта отладчика для обеспечения совместимости с удаленной отладкой из Windows 95, основанный операционных системах.|  
|ReleaseFromSetProxyBlanket|Выпуски AddRef из SetProxyBlanketAndAddRef.|
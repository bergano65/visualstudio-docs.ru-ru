---
title: "Iremotedebugapplicationex — интерфейс | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IRemoteDebugApplicationEx Interface
ms.assetid: 8e16164d-dbb2-4488-9507-25ae34f343dc
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3360cea0d1649348a795356ad827b32b6f8ebc19
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="iremotedebugapplicationex-interface"></a>IRemoteDebugApplicationEx — интерфейс
Представляет работающее приложение. Он не сопоставлен процесс операционной системы. Как правило отладчик обращается приложение для отладки. Как правило, диспетчер отладки процессов реализует объект приложения.  
  
 Помимо методов, наследуемых от `IUnknown`, `IRemoteDebugApplicationEx` интерфейс предоставляет следующие методы.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
  
|Метод|Описание|  
|------------|-----------------|  
|[IRemoteDebugApplicationEx:GetHostPid](../../winscript/reference/iremotedebugapplicationex-gethostpid.md)|Возвращает идентификатор процесса для ведущего приложения.|  
|GetHostMachineName|Возвращает имя компьютера, который ведущее приложение выполняется на.|  
|[IRemoteDebugApplicationEx:SetLocale](../../winscript/reference/iremotedebugapplicationex-setlocale.md)|Задает язык для локализации отладчика.|  
|[IRemoteDebugApplicationEx:ForceStepMode](../../winscript/reference/iremotedebugapplicationex-forcestepmode.md)|Заставляет отладчик в пошаговом режиме.|  
|[IRemoteDebugApplicationEx:RevokeBreak](../../winscript/reference/iremotedebugapplicationex-revokebreak.md)|Отменяет команду break.|  
|SetProxyBlanketAndAddRef|Обновляет сведения о безопасности COM на прокси-сервера для объекта отладчика для обеспечения совместимости с удаленную отладку с операционными системами Windows 95.|  
|ReleaseFromSetProxyBlanket|Выпуски AddRef из SetProxyBlanketAndAddRef.|
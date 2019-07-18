---
title: Iremotedebugapplicationex — интерфейс | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IRemoteDebugApplicationEx Interface
ms.assetid: 8e16164d-dbb2-4488-9507-25ae34f343dc
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ab9e25a28ade1ac73b9e4837dae61e2d91f24c45
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62788382"
---
# <a name="iremotedebugapplicationex-interface"></a>IRemoteDebugApplicationEx — интерфейс
Представляет выполняющееся приложение. Он не должен соответствовать процесс операционной системы. Как правило отладчик обращается приложение для отладки. Диспетчер отладки процессов обычно реализует объект приложения.  
  
 Помимо методов, наследуемых от `IUnknown`, `IRemoteDebugApplicationEx` интерфейс предоставляет следующие методы.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
  
|Метод|Описание|  
|------------|-----------------|  
|[IRemoteDebugApplicationEx:GetHostPid](../../winscript/reference/iremotedebugapplicationex-gethostpid.md)|Возвращает идентификатор процесса для ведущего приложения.|  
|GetHostMachineName|Возвращает имя компьютера под управлением ведущего приложения.|  
|[IRemoteDebugApplicationEx:SetLocale](../../winscript/reference/iremotedebugapplicationex-setlocale.md)|Задает язык для локализации отладчика.|  
|[IRemoteDebugApplicationEx:ForceStepMode](../../winscript/reference/iremotedebugapplicationex-forcestepmode.md)|Заставляет отладчик в пошаговом режиме.|  
|[IRemoteDebugApplicationEx:RevokeBreak](../../winscript/reference/iremotedebugapplicationex-revokebreak.md)|Отменяет команду break.|  
|SetProxyBlanketAndAddRef|Обновляет сведения о безопасности COM на прокси-сервер для объекта отладчика для обеспечения совместимости с удаленную отладку с операционными системами Windows 95.|  
|ReleaseFromSetProxyBlanket|AddRef выпуски из SetProxyBlanketAndAddRef.|
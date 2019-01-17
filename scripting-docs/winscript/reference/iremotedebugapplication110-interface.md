---
title: Интерфейс IRemoteDebugApplication110 | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IRemoteDebugApplication110 Interface
ms.assetid: 785ab46a-8827-41cb-806a-132e6b2c8f47
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f280e2b869a3046ecb2d3fac37facdcc1bfeb7fb
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/16/2019
ms.locfileid: "54349885"
---
# <a name="iremotedebugapplication110-interface"></a>IRemoteDebugApplication110 — интерфейс
Используется для предоставления новых возможностей, которые могут быть вызваны отладчиках скриптов и вызывающих объектов в процессе.  
  
> [!IMPORTANT]
>  Этот интерфейс реализуется в PDM v11.0 и более поздней версии. Обнаружено в activdbg100.h.  
  
## <a name="methods"></a>Методы  
 Интерфейс `IRemoteDebugApplication110` предоставляет следующие методы.  
  
|Метод|Описание|  
|------------|-----------------|  
|[IRemoteDebugApplication110::SetDebuggerOptions](../../winscript/reference/iremotedebugapplication110-setdebuggeroptions.md)|Вызывается для обновления параметров отладчика. Параметры по умолчанию 0 (SDO_NONE).|  
|[IRemoteDebugApplication110::GetCurrentDebuggerOptions](../../winscript/reference/iremotedebugapplication110-getcurrentdebuggeroptions.md)|Возвращает текущий набор доступных параметров.|  
|[IRemoteDebugApplication110::GetMainThread](../../winscript/reference/iremotedebugapplication110-getmainthread.md)|Возвращает основной поток для узлов, которые вызывают SetSite.|
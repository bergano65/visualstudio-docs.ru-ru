---
title: IActiveScriptSiteInterruptPoll::QueryContinue | Документы Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSiteInterruptPoll.QueryContinue
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSiteInterruptPoll::QueryContinue
ms.assetid: 41ac3807-f8b4-4a0e-bcc6-556bc89f3904
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 93323d500ae7e99957c365d60741fa612ba0fc34
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24725164"
---
# <a name="iactivescriptsiteinterruptpollquerycontinue"></a>IActiveScriptSiteInterruptPoll::QueryContinue
Позволяет ведущему приложению указать сценарий должно быть прекращено.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT QueryContinue();  
```  
  
#### <a name="parameters"></a>Параметры  
 Этот метод не принимает параметры.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|`S_OK`|Вызов завершился успешно и узел разрешает сценарий для продолжения работы.|  
|`S_FALSE`|Вызов успешно и запросы узла, приводящие к прерыванию скрипт.|  
  
## <a name="remarks"></a>Примечания  
 Завершать размещенного скрипта, если возвращаемое значение `QueryContinue` метод `S_OK`. Возвращаемое значение `S_FALSE` указывает, что узел явно запрашивает завершение, скрипт.  
  
 Многопоточные ведущее приложение может использовать `IActiveScript::InterruptScriptThread` метод для завершения скрипта.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IActiveScriptSiteInterruptPoll](../../winscript/reference/iactivescriptsiteinterruptpoll-interface.md)   
 [IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md)
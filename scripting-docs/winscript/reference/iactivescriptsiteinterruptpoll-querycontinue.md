---
title: IActiveScriptSiteInterruptPoll::QueryContinue | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 63ce45c0973d65d240136d7b42aef0c078b00c9a
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2019
ms.locfileid: "58154313"
---
# <a name="iactivescriptsiteinterruptpollquerycontinue"></a>IActiveScriptSiteInterruptPoll::QueryContinue
Позволяет ведущему приложению указать, что следует прервать сценарий.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT QueryContinue();  
```  
  
#### <a name="parameters"></a>Параметры  
 Этот метод не принимает параметров.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|`S_OK`|Вызов завершился успешно, и основное приложение разрешает сценарий продолжать работу.|  
|`S_FALSE`|Вызов успешно и узла запросов, приводящих к прекращению скрипт.|  
  
## <a name="remarks"></a>Примечания  
 Размещенным сценарием должно быть прекращено, если возвращаемое значение `QueryContinue` метод `S_OK`. Возвращаемое значение `S_FALSE` указывает, что узел явно запрашивает, что завершить скрипт.  
  
 Многопоточные узел может использовать `IActiveScript::InterruptScriptThread` метод для завершения скрипта.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IActiveScriptSiteInterruptPoll](../../winscript/reference/iactivescriptsiteinterruptpoll-interface.md)   
 [IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md)
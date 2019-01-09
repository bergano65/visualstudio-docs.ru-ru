---
title: IActiveScriptSiteInterruptPoll::QueryContinue | Документация Майкрософт
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
ms.openlocfilehash: 9b43211dca57a404d5625cfc2d7ede67a70a0a40
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2019
ms.locfileid: "54087988"
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
  
|Значение|Описание:|  
|-----------|-----------------|  
|`S_OK`|Вызов завершился успешно, и основное приложение разрешает сценарий продолжать работу.|  
|`S_FALSE`|Вызов успешно и узла запросов, приводящих к прекращению скрипт.|  
  
## <a name="remarks"></a>Примечания  
 Размещенным сценарием должно быть прекращено, если возвращаемое значение `QueryContinue` метод `S_OK`. Возвращаемое значение `S_FALSE` указывает, что узел явно запрашивает, что завершить скрипт.  
  
 Многопоточные узел может использовать `IActiveScript::InterruptScriptThread` метод для завершения скрипта.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IActiveScriptSiteInterruptPoll](../../winscript/reference/iactivescriptsiteinterruptpoll-interface.md)   
 [IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md)
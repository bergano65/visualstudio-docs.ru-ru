---
title: 'Иактивескриптситеинтерруптполл:: Куериконтинуе | Документация Майкрософт'
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
ms.openlocfilehash: 7ce2ad61b54dce510035dd8e97d0dfb2accbf7a7
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572234"
---
# <a name="iactivescriptsiteinterruptpollquerycontinue"></a>IActiveScriptSiteInterruptPoll::QueryContinue
Позволяет узлу указать, что скрипт должен завершаться.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT QueryContinue();  
```  
  
#### <a name="parameters"></a>Параметры  
 Этот метод не принимает параметров.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|значения|Описание|  
|-----------|-----------------|  
|`S_OK`|Вызов выполнен, и узел разрешает продолжение выполнения сценария.|  
|`S_FALSE`|Вызов выполнен, и узел запрашивает завершение скрипта.|  
  
## <a name="remarks"></a>Заметки  
 Размещенный скрипт должен завершаться, если только возвращаемое значение метода `QueryContinue` не `S_OK`. Возвращаемое значение `S_FALSE` указывает, что узел явным образом запрашивает завершение скрипта.  
  
 Многопоточный узел может использовать метод `IActiveScript::InterruptScriptThread` для завершения скрипта.  
  
## <a name="see-also"></a>См. также  
 @No__t_1 [интерфейса иактивескриптситеинтерруптполл](../../winscript/reference/iactivescriptsiteinterruptpoll-interface.md)  
 [IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md)
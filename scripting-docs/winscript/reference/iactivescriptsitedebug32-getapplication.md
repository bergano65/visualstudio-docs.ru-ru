---
title: 'IActiveScriptSiteDebug32:: My Application | Документация Майкрософт'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 533d770d-06a4-4693-873e-255c9c6f0df0
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: 0b82ab6cd37f789e98ca08c635011a7e04f5b871
ms.sourcegitcommit: 9a9c61ca115c22d33bb902153eb0853789c7be4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85835632"
---
# <a name="iactivescriptsitedebug32getapplication"></a>IActiveScriptSiteDebug32::GetApplication
Возвращает объект приложения отладки, связанный с этим сайтом скриптов.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT GetApplication(  
   IDebugApplication**  ppda  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `ppda`  
 заполняет Указатель на объект приложения отладки, связанный с сайтом скрипта.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод выполнен успешно.|  
|`E_NOTIMPL`|Узел не поддерживает отладку напрямую.|  
  
## <a name="remarks"></a>Комментарии  
 `GetApplication`Метод предоставляет интеллектуальному узлу возможность определить объект приложения, к которому относится каждый скрипт. Обработчики сценариев должны попытаться вызвать этот метод, чтобы получить содержащее его приложение, и выполнить в `IProcessDebugManager::GetDefaultApplication` случае сбоя.  
  
## <a name="see-also"></a>Дополнительно  
 [Интерфейс IActiveScriptSiteDebug32](../../winscript/reference/iactivescriptsitedebug32-interface.md)   
 [IProcessDebugManager::GetDefaultApplication](../../winscript/reference/iprocessdebugmanager-getdefaultapplication.md)
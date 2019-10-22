---
title: 'IActiveScriptSiteDebug32:: My Application | Документация Майкрософт'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 533d770d-06a4-4693-873e-255c9c6f0df0
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: 93c4a8fe6e5c2aac8b07f896810dcd03060b46d0
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572195"
---
# <a name="iactivescriptsitedebug32getapplication"></a>IActiveScriptSiteDebug32:: a Application
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
  
|значения|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
|`E_NOTIMPL`|Узел не поддерживает отладку напрямую.|  
  
## <a name="remarks"></a>Заметки  
 Метод `GetApplication` предоставляет смарт-узлу способ определения объекта приложения, к которому относится каждый скрипт. Обработчики сценариев должны попытаться вызвать этот метод, чтобы получить содержащее его приложение, и прибегнуть к `IProcessDebugManager::GetDefaultApplication` в случае сбоя.  
  
## <a name="see-also"></a>См. также  
 @No__t_1 [интерфейса IActiveScriptSiteDebug32](../../winscript/reference/iactivescriptsitedebug32-interface.md)  
 [IProcessDebugManager::GetDefaultApplication](../../winscript/reference/iprocessdebugmanager-getdefaultapplication.md)
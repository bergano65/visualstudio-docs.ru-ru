---
title: IActiveScriptSiteDebug32::GetApplication | Документация Майкрософт
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
ms.openlocfilehash: c71e33445db7745f71e374c586d079a9665776b2
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62992486"
---
# <a name="iactivescriptsitedebug32getapplication"></a>IActiveScriptSiteDebug32::GetApplication
Возвращает объект отладки приложения, связанные с этим сайтом скрипта.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT GetApplication(  
   IDebugApplication**  ppda  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `ppda`  
 [out] Указатель на объект отладки приложения, связанный с сайт скрипта.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
|`E_NOTIMPL`|Узел непосредственно не поддерживает отладку.|  
  
## <a name="remarks"></a>Примечания  
 `GetApplication` Метод предоставляет способ для промежуточных узлов определить объект приложения, к которой принадлежит каждый скрипт. Обработчики скриптов следует попытаться вызвать этот метод, чтобы получить их содержащему их приложению и прибегнуть к `IProcessDebugManager::GetDefaultApplication` Если это не удается.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IActiveScriptSiteDebug32](../../winscript/reference/iactivescriptsitedebug32-interface.md)   
 [IProcessDebugManager::GetDefaultApplication](../../winscript/reference/iprocessdebugmanager-getdefaultapplication.md)
---
title: IActiveScriptSiteDebug::GetApplication | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSiteDebug.GetApplication
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSiteDebug::GetApplication
ms.assetid: 4400f1b1-3108-4a71-b1f1-43586fe1227c
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 75560ead40809c77e4768f8318d754a512e5d7ba
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2019
ms.locfileid: "58147492"
---
# <a name="iactivescriptsitedebuggetapplication"></a>IActiveScriptSiteDebug::GetApplication
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
 [Интерфейс IActiveScriptSiteDebug](../../winscript/reference/iactivescriptsitedebug-interface.md)   
 [IProcessDebugManager::GetDefaultApplication](../../winscript/reference/iprocessdebugmanager-getdefaultapplication.md)
---
title: IProcessDebugManager::CreateApplication | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IProcessDebugManager.CreateApplication
apilocation:
- pdm.dll
helpviewer_keywords:
- IProcessDebugManager::CreateApplication
ms.assetid: d6b646f2-8af0-445c-ae7e-a9772042b3a1
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 10d7f2246b327393a810170f5b133f2885186c3a
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2019
ms.locfileid: "58152828"
---
# <a name="iprocessdebugmanagercreateapplication"></a>IProcessDebugManager::CreateApplication
Создает новый объект отладки приложения для этого приложения.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT CreateApplication(  
   IDebugApplication**  ppda  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `ppda`  
 [out] Объект приложения отладки для этого приложения.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Примечания  
 Объект, созданный с помощью данного метода не имеет имени и не добавляется с запуском список приложений. Используйте `IProcessDebugManager::AddApplication` Чтобы добавить это приложение отладки в список приложений.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IProcessDebugManager](../../winscript/reference/iprocessdebugmanager-interface.md)   
 [IProcessDebugManager::AddApplication](../../winscript/reference/iprocessdebugmanager-addapplication.md)
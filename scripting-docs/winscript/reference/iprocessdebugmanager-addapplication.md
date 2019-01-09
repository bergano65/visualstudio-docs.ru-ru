---
title: IProcessDebugManager::AddApplication | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IProcessDebugManager.AddApplication
apilocation:
- pdm.dll
helpviewer_keywords:
- IProcessDebugManager::AddApplication
ms.assetid: 73828299-11eb-4c58-ad70-f80f2d0eede8
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fa0b811a23f8c97f1924883a04878f22cabc9b26
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2019
ms.locfileid: "54087533"
---
# <a name="iprocessdebugmanageraddapplication"></a>IProcessDebugManager::AddApplication
Добавляет приложение диспетчера отладки компьютера список выполняемых приложений.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT AddApplication(  
   IDebugApplication*  pda,  
   DWORD*              pdwAppCookie  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pda`  
 [in] Приложение отладки, чтобы добавить в список запущенных приложений.  
  
 `pdwAppCookie`  
 [out] Файл cookie, который используется для удаления существующего приложения с диспетчером отладки.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Примечания  
 Этот метод добавляет приложению выполнения список приложений в диспетчер отладки.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IProcessDebugManager](../../winscript/reference/iprocessdebugmanager-interface.md)   
 [IProcessDebugManager::RemoveApplication](../../winscript/reference/iprocessdebugmanager-removeapplication.md)
---
title: IMachineDebugManagerCookie::AddApplication | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IMachineDebugManagerCookie.AddApplication
apilocation:
- scrobj.dll
helpviewer_keywords:
- IMachineDebugManagerCookie::AddApplication
ms.assetid: 4d5503c5-aca9-4cf7-9900-f77bf5f3263d
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c71983dd5f1273679351bc45c1db2df62757d153
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62977660"
---
# <a name="imachinedebugmanagercookieaddapplication"></a>IMachineDebugManagerCookie::AddApplication
Добавляет приложению выполнения список приложений.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT AddApplication(  
   IRemoteDebugApplication*  pda,  
   DWORD                     dwDebugAppCookie,  
   DWORD*                    pdwAppCookie  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pda`  
 [in] Приложению выполнения список приложений.  
  
 `dwDebugAppCookie`  
 [in] Файл cookie, идентифицирующий приложение отладки.  
  
 `pdwAppCookie`  
 [out] Файл cookie, который используется для удаления существующего приложения с диспетчером отладки.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Примечания  
 Этот метод вызывается диспетчером отладки процессов каждый раз, когда `IProcessDebugManager::AddApplication` вызывается.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IMachineDebugManagerCookie](../../winscript/reference/imachinedebugmanagercookie-interface.md)   
 [IMachineDebugManagerCookie::RemoveApplication](../../winscript/reference/imachinedebugmanagercookie-removeapplication.md)   
 [IProcessDebugManager::AddApplication](../../winscript/reference/iprocessdebugmanager-addapplication.md)
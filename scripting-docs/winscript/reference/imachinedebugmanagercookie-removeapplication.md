---
title: "IMachineDebugManagerCookie::RemoveApplication | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IMachineDebugManagerCookie.RemoveApplication
apilocation:
- scrobj.dll
helpviewer_keywords:
- IMachineDebugManagerCookie::RemoveApplication
ms.assetid: af8f4a52-ec5e-48fa-87de-234d5e6528d0
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fe0849b2f580eac7759db36335823a737a198e55
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="imachinedebugmanagercookieremoveapplication"></a>IMachineDebugManagerCookie::RemoveApplication
Удаляет приложение с запуском список приложений.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT RemoveApplication(  
   DWORD  dwDebugAppCookie,  
   DWORD  dwAppCookie  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `dwDebugAppCookie`  
 [in] Файл cookie, который идентифицирует приложение отладки.  
  
 `dwAppCookie`  
 [in] Файл cookie, когда приложение был добавлен в список приложений.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Примечания  
 Этот метод вызывается диспетчером процесс отладки всякий раз, когда `IProcessDebugManager::RemoveApplication` вызывается.  
  
## <a name="see-also"></a>См. также  
 [IMachineDebugManagerCookie::AddApplication](../../winscript/reference/imachinedebugmanagercookie-addapplication.md)   
 [Интерфейс IMachineDebugManagerCookie](../../winscript/reference/imachinedebugmanagercookie-interface.md)   
 [IProcessDebugManager::RemoveApplication](../../winscript/reference/iprocessdebugmanager-removeapplication.md)
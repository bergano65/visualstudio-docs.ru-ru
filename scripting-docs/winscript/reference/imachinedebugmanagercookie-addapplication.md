---
title: 'IMachineDebugManagerCookie:: Аддаппликатион | Документация Майкрософт'
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
ms.openlocfilehash: da436308c71a66d3070d42128d8da03ae88d2935
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573917"
---
# <a name="imachinedebugmanagercookieaddapplication"></a>IMachineDebugManagerCookie::AddApplication
Добавляет приложение в список выполняющихся приложений.  
  
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
 окне Приложение в список выполняющихся приложений.  
  
 `dwDebugAppCookie`  
 окне Файл cookie, определяющий приложение отладки.  
  
 `pdwAppCookie`  
 заполняет Файл cookie, который используется для удаления приложения из диспетчера отладки.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Примечания  
 Этот метод вызывается диспетчером отладки процессов всякий раз, когда вызывается `IProcessDebugManager::AddApplication`.  
  
## <a name="see-also"></a>См. также:  
   [интерфейса IMachineDebugManagerCookie](../../winscript/reference/imachinedebugmanagercookie-interface.md)  
 [IMachineDebugManagerCookie:: ремовеаппликатион](../../winscript/reference/imachinedebugmanagercookie-removeapplication.md)   
 [IProcessDebugManager::AddApplication](../../winscript/reference/iprocessdebugmanager-addapplication.md)
---
title: IMachineDebugManagerCookie::RemoveApplication | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IMachineDebugManagerCookie.RemoveApplication
apilocation:
- scrobj.dll
helpviewer_keywords:
- IMachineDebugManagerCookie::RemoveApplication
ms.assetid: af8f4a52-ec5e-48fa-87de-234d5e6528d0
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4d920bcc348266d4aa9f0c4a4e297506f008e859
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2019
ms.locfileid: "58150638"
---
# <a name="imachinedebugmanagercookieremoveapplication"></a>IMachineDebugManagerCookie::RemoveApplication
Удаляет приложение из выполняемого список приложений.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT RemoveApplication(  
   DWORD  dwDebugAppCookie,  
   DWORD  dwAppCookie  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `dwDebugAppCookie`  
 [in] Файл cookie, идентифицирующий приложение отладки.  
  
 `dwAppCookie`  
 [in] Файл cookie, когда приложение было добавлено в список приложений.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание:|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Примечания  
 Этот метод вызывается диспетчером отладки процессов каждый раз, когда `IProcessDebugManager::RemoveApplication` вызывается.  
  
## <a name="see-also"></a>См. также  
 [IMachineDebugManagerCookie::AddApplication](../../winscript/reference/imachinedebugmanagercookie-addapplication.md)   
 [Интерфейс IMachineDebugManagerCookie](../../winscript/reference/imachinedebugmanagercookie-interface.md)   
 [IProcessDebugManager::RemoveApplication](../../winscript/reference/iprocessdebugmanager-removeapplication.md)
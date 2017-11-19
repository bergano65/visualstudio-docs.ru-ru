---
title: "IDebugCookie::SetDebugCookie | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugCookie.SetDebugCookie
apilocation: pdm.dll
helpviewer_keywords: IDebugCookie::SetDebugCookie
ms.assetid: 9cba3b05-ff81-4fb0-9382-e9338cb9192d
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1155b00750cfe2a91625ba0f531622f381467198
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="idebugcookiesetdebugcookie"></a>IDebugCookie::SetDebugCookie
Задает файл cookie отладки приложения.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT SetDebugCookie(  
   DWORD  dwDebugAppCookie  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `dwDebugAppCookie`  
 [in] Файл cookie, который идентифицирует приложение отладки.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Примечания  
 Этот метод задает отладки приложения куки-файл, что позволяет более одного отладчик мог присоединиться к процессу.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IDebugCookie](../../winscript/reference/idebugcookie-interface.md)
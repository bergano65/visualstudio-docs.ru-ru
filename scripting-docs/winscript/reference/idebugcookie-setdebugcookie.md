---
title: 'IDebugCookie:: Сетдебугкукие | Документация Майкрософт'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugCookie.SetDebugCookie
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugCookie::SetDebugCookie
ms.assetid: 9cba3b05-ff81-4fb0-9382-e9338cb9192d
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 664939d0b91b8dbbf87dbff2978064811ffee486
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573182"
---
# <a name="idebugcookiesetdebugcookie"></a>IDebugCookie::SetDebugCookie
Задает файл cookie приложения отладки.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT SetDebugCookie(  
   DWORD  dwDebugAppCookie  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `dwDebugAppCookie`  
 окне Файл cookie, определяющий приложение отладки.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|значения|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Заметки  
 Этот метод задает файл cookie приложения отладки, который позволяет присоединять к процессу более чем один отладчик.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IDebugCookie](../../winscript/reference/idebugcookie-interface.md)
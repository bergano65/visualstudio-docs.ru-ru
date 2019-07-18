---
title: IScriptNode::GetCookie | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptNode.GetCookie
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptNode::GetCookie
ms.assetid: 007339c6-a73a-4147-b3c0-cc041e467ecd
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b05d184af3ecd6302fc05893600fd7026eeca3ad
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62787057"
---
# <a name="iscriptnodegetcookie"></a>IScriptNode::GetCookie
Возвращает значение, определяемые приложением, которое используется для связывания с объектом главного пользователи.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT GetCookie(  
   DWORD              *pdwCookie  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pdwCookie`  
 [out] Для `IScriptEntry` объекта, возвращает значение файла cookie, определяемые приложением.  
  
 Для `IScriptNode` , представляющий веб-страницы, возвращает значение 0.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Примечания  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IScriptNode](../../winscript/reference/iscriptnode-interface.md)
---
title: IScriptScriptlet::SetSimpleEventName | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptScriptlet.SetSimpleEventName
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptScriptlet::SetSimpleEventName
ms.assetid: 7de9132e-635f-45df-9c92-83a24242b477
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 63e6d05066d59e14a7036fb8f371c9c20b886df7
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2019
ms.locfileid: "58150846"
---
# <a name="iscriptscriptletsetsimpleeventname"></a>IScriptScriptlet::SetSimpleEventName
Задает имя простого события, который связан с пользователи. Это имя одного слова, которое не содержит пробелов.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT SetSimpleEventName(  
   LPCOLESTR          psz  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `psz`  
 [in] Буфер, содержащий имя простых событий, связанный с `IScriptScriptlet` объекта.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Примечания  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IScriptScriptlet](../../winscript/reference/iscriptscriptlet-interface.md)
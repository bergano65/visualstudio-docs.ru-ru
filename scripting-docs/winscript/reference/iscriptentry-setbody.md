---
title: IScriptEntry::SetBody | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptEntry.SetBody
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptEntry::SetBody
ms.assetid: 719062e4-98e4-4a7b-946d-6e5dbbcc5225
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 46ebccb57885480d34d79cbd27e99dc6a35b343d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62787649"
---
# <a name="iscriptentrysetbody"></a>IScriptEntry::SetBody
Задает текст, который находится в теле `IScriptEntry` блок скрипта или `IScriptScriptlet` скриптлета.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT SetBody(  
   LPCOLESTR          psz  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `psz`  
 [in] Для `IScriptEntry` блок скрипта, `psz` является текст, заключенный в теги сценариев.  
  
 Для `IScriptEntry` блока функции `psz` представляет собой тело функции.  
  
 Для `IScriptScriptlet` объекта (который является производным от `IScriptEntry`), `psz` — это сценарий текст сценария.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Примечания  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IScriptEntry](../../winscript/reference/iscriptentry-interface.md)   
 [IScriptEntry::GetBody](../../winscript/reference/iscriptentry-getbody.md)
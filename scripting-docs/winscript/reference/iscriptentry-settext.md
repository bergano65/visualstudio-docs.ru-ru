---
title: IScriptEntry::SetText | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptEntry.SetText
apilocation:
- scrobj.dll
helpviewer_keywords:
- ISetEntry::SetText
ms.assetid: 4605481b-7707-43d1-ab78-a9207d0cf6fe
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 17e716a7ad52cc5aeca18d02122edb9c457b14e4
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2019
ms.locfileid: "58147648"
---
# <a name="iscriptentrysettext"></a>IScriptEntry::SetText
Задает текст, который соответствует `IScriptEntry` блок сценария, или исходный код, содержащийся в `IScriptScriptlet` обработчик событий.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT SetText(  
   LPCOLESTR          psz  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `psz`  
 [in] Текст `IScriptEntry` блок сценария, или исходный код `IScriptScriptlet` обработчик событий.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Примечания  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IScriptEntry](../../winscript/reference/iscriptentry-interface.md)
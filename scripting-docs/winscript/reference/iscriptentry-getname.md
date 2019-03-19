---
title: IScriptEntry::GetName | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptEntry.GetName
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptEntry::GetName
ms.assetid: 56daa288-618f-497c-a360-7d443afd478b
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d23843aa72ce5cf79f6442048b6493d17eb6ef64
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2019
ms.locfileid: "58147921"
---
# <a name="iscriptentrygetname"></a>IScriptEntry::GetName
Для записи, представляющие один объект (например, функцию) возвращает имя объекта.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT GetName(  
   BSTR               *pbstr  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pbstr`  
 [out] Имя объекта, представленного `IScriptEntry` блок скрипта. Если запись не представляет один объект, возвращается значение NULL.  
  
 Дочерние записи представлять объект одной функции.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание:|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Примечания  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IScriptEntry](../../winscript/reference/iscriptentry-interface.md)   
 [IScriptNode:: CreateChildEntry](../../winscript/reference/iscriptnode-createchildentry.md)